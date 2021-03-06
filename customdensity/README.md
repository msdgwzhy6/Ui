## Customdensity

### 功能
> 简化适配工作,直接使用设计稿px尺寸作为dp值

### 存在问题
* 目前只支持单方向适配
* 和部分实现了适配的组件冲突

### 使用
* 初始化

下载依赖
```
 implementation 'com.github.wangfengye:Ui:sizeAuto'
 ```
Application中初始化
```java
    // 初始化
    CustomDensity.init(720,1080,this);
    // 注册该方法后，所有activity默认使用以宽度适配,未注册该方法时,需手动去取消适配
    registerActivityLifecycleCallbacks(new DensityActivityLifecycleCallbacks());
```
activity中单独使用或该页面使用特殊的适配尺寸
```java
   protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        // 必须在设置布局前调用
         CustomDensity.auto(CustomDensity.WIDTH,720,this);
        setContentView(R.layout.activity_size_adapter);
    }
```
activity单独使用时,需手动取消适配
```java
    @Override
    protected void onPause() {
        super.onPause();
        CustomDensity.cancelAuto(this);
    }
```

* [发现一个更完善的适配库](https://github.com/JessYanCoding/AndroidAutoSize)

