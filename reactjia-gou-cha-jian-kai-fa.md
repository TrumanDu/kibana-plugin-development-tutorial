## 实践
在本篇实现一个app 插件demo,在demo页面可以显示服务器端时间。
### 插件入口
在 在该文件中定义插件名，描述，以及插件前端和后端入口，配置。
```
export default function (kibana) {
  return new kibana.Plugin({
    require: ['elasticsearch'],
    name: 'demo',
    uiExports: {
      app: {
        title: 'Demo',
        description: 'An awesome Kibana plugin',
        main: 'plugins/demo/app',
        styleSheetPath: require('path').resolve(__dirname, 'public/app.scss'),
      },
    },

    config(Joi) {
      return Joi.object({
        enabled: Joi.boolean().default(true),
      }).default();
    },

    init(server, options) { // eslint-disable-line no-unused-vars
      // Add server routes and initialize the plugin here
      exampleRoute(server);
    }
  });
}
```
### 插件前端

首先编写react 组件，展示页面
```
import React from 'react';
import {
  EuiPage,
  EuiPageHeader,
  EuiTitle,
  EuiPageBody,
  EuiPageContent,
  EuiPageContentHeader,
  EuiPageContentBody,
  EuiText
} from '@elastic/eui';

export class Main extends React.Component {
  constructor(props) {
    super(props);
    this.state = {};
  }

  componentDidMount() {
    /*
       FOR EXAMPLE PURPOSES ONLY.  There are much better ways to
       manage state and update your UI than this.
    */
    const { httpClient } = this.props;
    httpClient.get('../api/Demo/example').then((resp) => {
      this.setState({ time: resp.data.time });
    });
  }
  render() {
    const { title } = this.props;
    return (
      <EuiPage>
        <EuiPageBody>
          <EuiPageHeader>
            <EuiTitle size="l">
              <h1>{title} Hello World!</h1>
            </EuiTitle>
          </EuiPageHeader>
          <EuiPageContent>
            <EuiPageContentHeader>
              <EuiTitle>
                <h2>Congratulations</h2>
              </EuiTitle>
            </EuiPageContentHeader>
            <EuiPageContentBody>
              <EuiText>
                <h3>You have successfully created your first Kibana Plugin!</h3>
                <p>The server time (via API call) is {this.state.time || 'NO API CALL YET'}</p>
              </EuiText>
            </EuiPageContentBody>
          </EuiPageContent>
        </EuiPageBody>
      </EuiPage>
    );
  }
}

```

将组件挂载到页面上
```
import React from 'react';
import { uiModules } from 'ui/modules';
import chrome from 'ui/chrome';
import { render, unmountComponentAtNode } from 'react-dom';

import 'ui/autoload/styles';
import './less/main.less';
import { Main } from './components/main';

const app = uiModules.get('apps/demo');

app.config($locationProvider => {
  $locationProvider.html5Mode({
    enabled: false,
    requireBase: false,
    rewriteLinks: false,
  });
});
app.config(stateManagementConfigProvider =>
  stateManagementConfigProvider.disable()
);

function RootController($scope, $element, $http) {
  const domNode = $element[0];

  // render react to DOM
  render(<Main title="Demo" httpClient={$http} />, domNode);

  // unmount react on controller destroy
  $scope.$on('$destroy', () => {
    unmountComponentAtNode(domNode);
  });
}

chrome.setRootController('demo', RootController);
```

### 服务端

```
export default function (server) {

  server.route({
    path: '/api/Demo/example',
    method: 'GET',
    handler(req, reply) {
      reply({ time: (new Date()).toISOString() });
    }
  });

}
```

### 效果
![](/assets/demo.png)