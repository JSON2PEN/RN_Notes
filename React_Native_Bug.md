### 1. listview和scrollow展示不全的bug
```
因为listview继承scrollview，ScrollView必须有一个确定的高度才能正常工作，因为它实际上所做的就是将一系列不确定高度的
子组件装进一个确定高度的容器（通过滚动操作）。要给一个ScrollView确定一个高度的话，要么直接给它设置高度（不建议），要
么确定所有的父容器都已经绑定了高度。在视图栈的任意一个位置忘记使用{flex:1}都会导致错误，你可以使用元素查看器来查找问
题的原因。
    因此listview的每一项必须返回一个特定高度的大小视图，才能正确显示
```
### 2. RN Android打包的相关坑
 **RN打release包流程**
1. 使用android studio创建签名文件xxx.jks,并放在项目根/android/app目录下
2. 项目根/android目录下的gradle.properties文件中添加
```
MYAPP_RELEASE_STORE_FILE=RN_jhj.jks
MYAPP_RELEASE_KEY_ALIAS=RN_jhj
MYAPP_RELEASE_STORE_PASSWORD=abc123
MYAPP_RELEASE_KEY_PASSWORD=abc123
```
3.在项目根/android/app/build.gradle文件修改添加
```
def enableProguardInReleaseBuilds = 改为true
  signingConfigs {
        release {
            storeFile file(MYAPP_RELEASE_STORE_FILE)
            storePassword MYAPP_RELEASE_STORE_PASSWORD
            keyAlias MYAPP_RELEASE_KEY_ALIAS
            keyPassword MYAPP_RELEASE_KEY_PASSWORD
        }
    }
    
      buildTypes {
        release {
            minifyEnabled enableProguardInReleaseBuilds
            proguardFiles getDefaultProguardFile("proguard-android.txt"), "proguard-rules.pro"
            signingConfig signingConfigs.release
        }
    }
```
4. 在项目根目录下执行:(下面命令的index.js或者为index.android.js)

```
react-native bundle --entry-file index.js --platform android --dev false --bundle-output ./android/app/src/main/assets/index.android.bundle --
assets-dest ./android/app/src/main/res/

```
5. 在项目根/android目录下执行命令:输出包
```
gradlew assembleRelease

```
**注意:**
1. RN代码中不能使用 propTypes.style类型校验,否则release运行直接报错;
2. 代码中给的方法中不能使用'({})=>{}'字样否则执行报错
### 3. 软键盘点击空白处不消失的bug
只需要在根scrollview或者listview中设置以下即可:
```
<ScrollView keyboardDismissMode='on-drag'>
```
###4. react-navigation自定义头布局在IOS返回不灵敏
    
```
	
	//不起作用 android上没问题
	static navigationOptions = (navigation) => {  
       		 // const params = navigation.state.params || {};

        return {
            header: ({navigation})=>{
                return <UCBaseTitle back={()=>navigation.goBack(null)}
                                    title={"hahahha"}/>
            }
        };
    };

	//解决方案

	static navigationOptions = ({navigation}) => {
        return {
            headerLeft: <TouchableOpacity activeOpacity={1} style={{
                    flexDirection: 'row',
                    width: 50,
                    alignItems: 'center',
                    height: 50
                }} onPress={() => navigation.goBack()}>
                    <Image style={{width: 30, height: 30, marginLeft: 10}} source={backImg}/>
                </TouchableOpacity>
            ,
            headerTitle: (<View style={{flex: 1, alignItems: 'center',}}><Text style={{color: 'white', fontSize: 20}}>我是标题</Text></View>
            ),
            headerRight: (
                <View style={{height: 50, width: 50}}/>
            ),
            headerStyle: {
                height: 50,
                backgroundColor: '#27232e',
                marginTop: statusHeight
            }
        }
    };
```
### Modal在android中必须添加:onRequestClose属性
```
onRequestClose={() => console.log('onRequestClose...')}
```
    










