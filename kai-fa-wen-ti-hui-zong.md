### 1.系统无法启动  
**问题**：

报错无法启动：Kibana does not support the current Node.js version v8.11.1. Please use Node.js v8.11.4 

**解决方案**：
原因 是因为kibana 限制使用node version为v8.11.4，更改package.json中8.11.4信息为你本机node版本，如果方便的话，最好保持个要求版本一致。

### 2.Request must contain a kbn-xsrf header

**问题：**

Request must contain a kbn-xsrf header

**解决方案**：
在请求的head 中增加：kbn-xsrf: reporting。例如：
```curl -k -XPOST -H "kbn-xsrf: reporting" http://localhost:5601/...```

