#### 说明

####用于设置不显示上面的进度提示,放到AppDelegat 中
 ```
[RCTDevLoadingView setEnabled:NO];
```

####在循环中进行方法的参数传递，需要使用 bind 注意 *pressRowRight*

```
_pressRowRight: function (code,title) {
        if (Platform.OS === 'ios') {
            this.props.navigator.push({
                title: title,
                component: Paypage,
                leftButtonIcon: require('../../image/leftarraw.png'),
                onLeftButtonPress: () => this.props.navigator.pop(),
                rightButtonTitle: '缴费历史',
                onRightButtonPress: () => this._pressRow('缴费历史', History),
                passProps:{
                    code:code
                }
            });
        } else {
            this.props.navigator.push({
                id: page.id,
                index: 5,
                wrapperStyle: styles.customWrapperStyle,
            });
        }

    },

for(var i = 0; i < charge.length; i++){
         var temp = charge[i];
         final.push(
           <TouchableOpacity onPress={this._pressRowRight.bind(this,temp.paycode,temp.aliasname)}>
               <View style={[styles.cell,styles.cellbox,styles.cellborder]}>
                   <View style={{flex:4,justifyContent:'flex-end',}}>
                       <Image source={require('../../image/shjf.png')} style={styles.icon}/>
                   </View>
                   <View style={{flex:3,justifyContent:'center',alignItems:'center'}}>
                       <Text style={[styles.font]}>{charge[i].aliasname}</Text>
                       <Text style={styles.font,{color:'#666',marginTop:PixelRatio.getPixelSizeForLayoutSize(3),}}>
                       ({charge[i].community})</Text>
                   </View>
               </View>
           </TouchableOpacity>
         );
      }
```

####navigator传递是否隐藏toolbar

修改 Navigator.ios.js

```
navigationBarHidden={this.props.navigationBarHidden}
为
navigationBarHidden={route.navigationBarHidden}

```

咽炎秘方

```
菊花，麦冬，甘草，金银花，藏青果，桔梗 等量。加蜂蜜代茶饮。
急性的嗓子痛 弄点罗汉果含含就好了撒
```

http://stackoverflow.com/questions/31177366/react-native-call-function-of-child-from-navigatorios

####如果 react-native 运行的时候报错，执行下上面的
npm prune && npm i

#####使用动画效果参考，有详细的使用说明
https://github.com/browniefed/react-native-animation-book

http://browniefed.com/react-native-animation-book/
