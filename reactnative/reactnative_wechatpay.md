#### 注意事项

微信支付集成参考
ios端代码

http://git.oschina.net/zysoft/wxPay_IOS

java后台代码

http://git.oschina.net/zysoft/wxPay

RN代码

###接口

```
#import <Foundation/Foundation.h>
#import "RCTBridgeModule.h"
#import "WXApi.h"
#import "WXApiObject.h"

@interface WeChatPayManager : NSObject<RCTBridgeModule>



@end
```

###实现

```
#import "WeChatPayManager.h"

#define base_url @"http://1.wchatpay.sinaapp.com/example/app.php"

@implementation WeChatPayManager

RCT_EXPORT_MODULE();


//直接接收参数数据，发送支付
RCT_EXPORT_METHOD(appPay:(NSDictionary *) details successCallback:(RCTResponseSenderBlock)callback){
  NSString *status = @"SUCCESS";
  NSMutableString *stamp  = [details objectForKey:@"timestamp"];
  //调起微信支付
  PayReq* req             = [[PayReq alloc] init];
  req.partnerId           = [details objectForKey:@"partnerid"];
  req.prepayId            = [details objectForKey:@"prepayid"];
  req.nonceStr            = [details objectForKey:@"noncestr"];
  req.timeStamp           = stamp.intValue;
  req.package             = [details objectForKey:@"package"];
  req.sign                = [details objectForKey:@"sign"];
  BOOL isOK  = [WXApi sendReq:req];
  if (!isOK) {
    status = @"FAIL";
  }
  NSDictionary *returnMsg = @{@"status":status};

  callback(@[[NSNull null],returnMsg]);
}


@end
```

JS上调用方法

```
var WeChatPay = require('react-native').NativeModules.WeChatPayManager;
//根据需要组装参数
var payItem = {tocket:'4991454AC5084C88895B0DD8E68AD38E',account:'111',typecode:'07001',type:'iw',body:'测试',detail:'测试',total_fee:'1'};
Util.post('http://1.wchatpay.sinaapp.com/example/app.php',payItem,function(data){
   console.log(data);
   WeChatPay.appPay(data,(error,retmsg) => {
      console.log(retmsg);
      AlertIOS.alert(
          '支付提示',
          '支付响应'+retmsg,
          [
              {text: 'OK', onPress: () => console.log('OK Pressed!')},
              {text: 'Cancel', onPress: () => console.log('Cancel Pressed!'), style: 'cancel'},
          ]
      )
   });
});

```
