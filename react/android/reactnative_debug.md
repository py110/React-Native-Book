#### 说明

####查看连接的设备

adb devices


####形成资源
react-native bundle --platform android --dev true --entry-file index.android.js   --bundle-output android/app/src/main/assets/index.android.bundle   --assets-dest android/app/src/main/res/



####调式图片不能显示

adb reverse tcp:8081 tcp:8081


/index.android.bundle?platform=android&dev=false

http://localhost:8081/index.android.bundle?platform=android&dev=false



localhost:8081/index.android.bundle?platform=android&dev=false


####打包

cd android && ./gradlew assembleRelease

####安装测试

cd android && ./gradlew installRelease


####找不到android的路径

export ANDROID_HOME=/usr/local/Cellar/android-sdk/24.4



#### 配置路径

进 terminal

Add Android SDK path to your ~/.bashrc, ~/.zshrc
export ANDROID_HOME=/usr/local/opt/android- sdk


export ANDROID_HOME=/usr/local/Cellar/android-sdk/24.4



react-native bundle --dev false --entry-file index.ios.js --platform ios --bundle-output main.jsbundle


react-native bundle --entry-file index.ios.js --bundle-output iOS/main.jsbundle --platform 'ios'  --dev false


react-native bundle --dev true --assets-dest ./ios --entry-file index.ios.js --platform ios --bundle-output ios/main.jsbundle
