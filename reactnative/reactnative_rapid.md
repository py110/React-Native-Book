#### 说明
由于国内访问 npm 比较慢，导致在 使用 RN 的指令的时候有点慢，我们可以使用淘宝的镜像来加快速度

####方式一

1. modify the react-native script
    * vim `which react-native`
    * exec('npm install --save react-native'
        * exec('npm --registry=https://registry.npm.taobao.org install --save react-native'
    * var proc = spawn('npm', ['install', '--verbose', '--save', 'react-native'], {stdio: 'inherit'});
        * var proc = spawn('npm', ['--registry=https://registry.npm.taobao.org', 'install', '--verbose', '--save', 'react-native'], {stdio: 'inherit'});
2. add a new file .npmrc in your home dir
    * echo 'registry = https://registry.npm.taobao.org' > ~/.npmrc (Recommeded!)
Then you can re-run react-native init AwesomeProject, it would be much faster. But if you still feel it is slow, try react-native init AwesomeProject --verbose, and you can see what is going on.



echo 'registry = https://registry.npm.taobao.org' > ~/.npmrc


####方式二

安装淘宝镜像

http://npm.taobao.org/


#####安装cnpm

$ npm install -g cnpm --registry=https://registry.npm.taobao.org

然后在对应的ReactNative 工程目录进行包升级的时候执行

cnpm install
