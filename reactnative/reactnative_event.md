#### 说明
RN由于是基于React的单事件流，所以在编程中经常存在需要刷新界面的情况，就不是很好处理，比如登录成功刷新当前窗口

使用事件

```
var RCTDeviceEventEmitter = require('RCTDeviceEventEmitter');
```

在组件里声明需要监听的事件

```
componentDidMount() {
      //注意这里的 js 上下文 this 的问题
      var me = this;
      RCTDeviceEventEmitter.addListener(Util.INTRO_PAGE, function (status) {
          me._onFinish().done();
          me.setState({
              isShow: false,
          });
      });
  },
```


在需要触发的组件中进行事件的分发

```
login: function () {
        //你的业务处理逻辑，成功后进行分发事件
        RCTDeviceEventEmitter.emit(Util.INTRO_PAGE);

      }
  },
  ```

网上参考资料：

https://colinramsay.co.uk/2015/07/04/react-native-eventemitters.html
