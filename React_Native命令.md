npm命令
###### 安装

```
npm install -g react-devtools//全局安装
```
###### 卸载

```
npm uninstall -g react-devtools
```
###### 项目局部安装

```
npm install react-navigation --save
```

###### react -devtools 启动

```
React-devtools
```
###### 调试工具连接调试手机
```
adb reverse tcp:8097 tcp:8097
```
###### bug修复

```
unable to load script from assets"index.android.bundle"
```

```
React-native bundle --platform Android --dev false --entry-file index.android.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res

```
###### 初始化RN旧项目

```
npm install -g rninit  //安装工具

rninit init [project name] --source react-ative@0.x.x//使用指定版本RN编译项目

react-native init MyApp --version 0.50.0//这个指定版本好像也可以
```
###### 查看包历史
```
npm view react-Native versions -json//react-native 可换成查询的包
```
###### 使用yarn 安装 为了防止安装githubdemo npm install总是报错的问题

```
npm install -g yarn react-native-cli
//配置淘宝镜像
yarn config set registryhttps://registry.npm.taobao.org --global
yarn config set disturlhttps://npm.taobao.org/dist --global

```
###### yarn命令总结

```
yarn / yarn install 等同于npm install 批量安装依赖
yarn add xxx 等同于 npm install xxx —save 安装指定包到指定位置
yarn remove xxx 等同于 npm uninstall xxx —save 卸载指定包
yarn add xxx —dev 等同于 npm install xxx —save-dev
yarn upgrade 等同于 npm update 升级全部包
yarn global add xxx 等同于 npm install xxx -g 全局安装指定包
```










