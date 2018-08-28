### 1.系统无法启动  
**问题**：

报错无法启动：Kibana does not support the current Node.js version v8.11.1. Please use Node.js v8.11.4 

**解决方案**：
原因 是因为kibana 限制使用node version为v8.11.4，更改package.json中8.11.4信息为你本机node版本，如果方便的话，最好保持个要求版本一致。


