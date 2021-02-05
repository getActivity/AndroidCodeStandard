# Android 代码规范文档

* 码云地址：[Gitee](https://gitee.com/getActivity/AndroidCodeStandard)

* 开源几年了，被很多人夸过，你的代码写得比较规范，[甚至有人质疑自己代码的写法了](https://github.com/getActivity/AndroidProject/issues/55)，但是迟迟没有出一个代码规范，只是因为我早几年写的代码还不够规范，规范是后续才养成的，我不仅参考了大公司出的代码规范文档，也研究了很多关于谷歌源码的编码规范，同时我也在无时不刻在思考，如何能写出让别人更好理解的代码，自打入行以来，我就在一直在探索。

#### 目录

* [前言](#前言)

* [常规规范](#常规规范)

* [后台接口规范](#后台接口规范)

* [变量命名规范](#变量命名规范)

* [包名命名规范](#包名命名规范)

* [方法命名规范](#方法命名规范)

* [类文件命名规范](#类文件命名规范)

* [接口文件命名规范](#接口文件命名规范)

* [布局文件命名规范](#布局文件命名规范)

* [资源文件命名规范](#资源文件命名规范)

* [接口实现规范](#接口实现规范)

* [异常捕获规范](#异常捕获规范)

* [Activity 跳转约定](#activity-跳转约定)

* [第三方框架使用规范](#第三方框架使用规范)

* [代码注释规范](#代码注释规范)

* [String ID 命名规范](#string-id-命名规范)

* [Anim ID 命名规范](#anim-id-命名规范)

* [View ID 命名规范](#view-id-命名规范)

* [Style 样式命名规范](#style-样式命名规范)

* [资源使用规范](#资源使用规范)

* [XML 编码规范](#xml-编码规范)

* [预览属性约定](#预览属性约定)

* [致谢](#致谢)

#### 前言

* 代码规范是我们每个程序员要做的事，假设我们按照自己的喜好来写代码，那么很可能出现的问题就是我看不懂你的代码或者你看不懂我的代码，这样会给后续维护形成巨大的障碍。这个时候问题来了，如何让代码不分你我，或许只需要一套规则，你和我都认可并且遵守的代码规范守则。

* 那么你的疑问可能又来了，怎么样才能算好的代码规范，答案只有一个，真正好的代码规范就是别人的代码你一眼就能看懂，更不需要反复去看。之所以这样并不是因为看的人 Review 代码的能力有多强，而是写代码的人愿意遵守规则，他知道自己想这么写，但是知道你会看不懂，所以换了一种方式来写，这种方式就是代码规范。

* 代码规范：一个好的代码规范可以帮助我们快速了解和熟悉相关的业务，降低后续维护的成本（二次开发和排查问题）

* 代码不规范：代码不规范会导致项目可读性变差，具体表现为难分辨难理解，在无形之中加大后续维护的成本

* 经验总结：编码不规范，同行两行泪

#### 常规规范

* 不用 `0dp`，而用 `0px`，这样可以避免系统进行换算，提升代码的执行效率

* 尽量采用 `switch case` 来判断，如果不能实现则再考虑用 `if else`

* 不用 paddingLeft，而用 `paddingStart`；不用 `paddingRight`，而用 `paddingEnd`

* 不用 `layout_marginLeft`，而用 `layout_marginStart`；不用 `layout_marginRight`，而用 `layout_marginEnd`

* 如果在 `layout_marginStart` 和 `layout_marginEnd` 相同的情况下，请替换使用 `layout_marginHorizontal`，而 `layout_marginTop` 和 `layout_marginBottom` 也同理，请替换使用 `layout_marginVertical`，`padding` 属性也是同理，这里不再赘述

* `过期` 和 `高版本` 的 API 一定要做对应的兼容（包含 Java 代码和 Xml 属性）

* 在能满足需求的情况下，尽量用 `invisible` 来代替 `gone`，因为 `gone` 会触发当前整个 View 树进行重新测量和绘制

* `api` 和 `implementation`，优先选用 `implementation`，因为这样可以[减少一些编译时间](https://www.jianshu.com/p/8962d6ba936e)

* `ListView` 和 `RecyclerView` 都能实现需求的前提下，优先选用 `RecyclerView`

* `ScrollView` 和 `NestedScrollView` 都能实现需求的前提下，优先选用 `NestedScrollView`

* 应用图标应该放在 `mipmap` 目录下，其他图片资源应当放到 `drawable` 目录下，具体原因可以点击[谷歌官方文档](https://developer.android.google.cn/guide/topics/resources/providing-resources)进行查看

* 不能在项目中创建副本文件，例如创建 `HomeActivity2.java`、`home_activity_v2.xml` 类似的副本文件，因为这样不仅会增加项目的维护难度，同时对编译速度也会造成一定的影响，正确的做法应该是在原有的文件基础上面修改，如果有需求回退的情况，请使用 `Git` 或者 `SVN` 进行版本回退

* 如果一个类不需要被继承，请直接用 `final` 进行修饰，如果一个字段在类初始化过程中已经赋值并且没有地方进行二次赋值，也应当用 `final` 修饰

* 每个小组成员应当安装[阿里巴巴代码约束插件](https://plugins.jetbrains.com/plugin/10046-alibaba-java-coding-guidelines)，并及时地对插件所提示的`代码警告`进行处理

#### 后台接口规范

* 后台返回的 `id` 值，不要使用 int 或者 long 类型来解析，而应该用 `string` 类型来解析，因为我们不需要对这个 id 值进行计算

* 后台返回的`金额`应该使用 `double` 来解析，而不能用 float 来解析，因为 float 在数值比较大的时候会容易丢失精度

* 我们在定义后台返回的 Bean 类时，不应当将一些我们没有使用到的字段添加到代码中，因为这样会消耗性能，因为 Gson 是通过`反射`将后台字段赋值到 Java 字段中，所以我们应当避免一些不必要的字段解析，另外臃余的字段也会给我们排查问题造成一定的阻碍

* 如果后台给定的字段名不符合 Java 代码命名，我们应当使用 `@SerializedName` 注解进行重命名

* 请求的接口参数和返回字段必须要写上注释，除此之外还应该备注对应的后台接口文档地址，以便我们后续能够更好地进行维护和迭代

* 后台返回的 Bean 类字段不能直接访问，而应该通过生成 Get 方法，然后使用这个 Get 方法来访问字段

* 接口请求成功的提示可以不显示，但是请求失败的提示需要要显示给到用户，否则会加大排查问题的难度，也有可能会把问题掩埋掉，从而让问题遗留到线上去

#### 变量命名规范

* `严禁使用中文或者中文拼音`进行重命名

* 使用`驼峰式命名风格`（单词最好控制在三个以内）

* 局部变量应用作用来命名，示例：

    * `String name`
    
    * `TextView nameView`
    
    * `FrameLayout nameLayout`
    
    * 命名规范附带技巧（当布局中同个类型的控件只有一个的时候，可以这样命名）

        * `TextView textView`
        
        * `RecyclerView recyclerView`

* 全局变量必须以小 m 开头，示例：

    * `String mName`
    
    * `TextView mNameView`
    
    * `FrameLayout mNameLayout`

    * 命名规范附带技巧（当布局中同个类型的控件只有一个的时候，可以这样命名）
        
        * `TextView mTextView`
        
        * `RecyclerView mRecyclerView`
    
* 布尔值命名规范，命名不应该以 `is` 开头

    * 错误写法示例：
    
        * 全局变量：`private boolean mIsDebug = false;`
        
        * 局部变量：`boolean isDebug = false;`
    
    * 正确写法示例：
    
        * 全局变量：`private boolean mDebug = false;`
        
        * 局部变量：`boolean debug = false;`
        
* 静态变量则用小 s 开头，示例：

    * `static Handler sHandler`

* 常量则需要用大写，并且用下划线代替驼峰，示例：

    * `static final String REQUEST_INSTALL_PACKAGES"`
    
* 有细心的同学可能会发现一个问题，为什么我们最常用的 Glide 和 OkHttp 的源码为什么没有用字母 `m` 来区分局部变量和全局变量？但是谷歌的 SDK 源码和 Support 库就有呢？那究竟是用还是不用呢？这个问题其实很好回答，我们可以先从体量上分析，首先谷歌的开发人员和项目数量肯定是最多的，那么谷歌在这块的探索和研究肯定是多于 Glie 和 OkHttp 的，其次是 Glide 和 OkHttp 的源码都有一个特点，很多类都维持在 1k 行代码左右，而谷歌源码很多类都接近 10k 行代码，例如 Activity 的源码在 API 30 上面有 8.8k 行代码，所以谷歌在这块略胜一筹，如果非要二选一，我选择谷歌的代码风格，并不是说 Glide 和 OkHttp 命名风格不好，是因为或许在未来的某一天，可能会有新的图片请求框架和网络请求框架来代替 Glide 和 OkHttp，但是基本不可能会出现有代替 Android SDK 或者 Support 库的一天
    
* 最后让我们静静地欣赏一下 `Activity` 字段的命名
    
```java
public class Activity {

    public static final int RESULT_CANCELED    = 0;
    public static final int RESULT_OK          = -1;

    private Instrumentation mInstrumentation;

    private IBinder mToken;
    private IBinder mAssistToken;

    private Application mApplication;

    /*package*/ Intent mIntent;

    /*package*/ String mReferrer;

    private ComponentName mComponent;

    /*package*/ ActivityInfo mActivityInfo;

    /*package*/ ActivityThread mMainThread;

    Activity mParent;

    boolean mCalled;

    /*package*/ boolean mResumed;

    /*package*/ boolean mStopped;

    boolean mFinished;
    boolean mStartedActivity;

    private boolean mDestroyed;
    private boolean mDoReportFullyDrawn = true;
    private boolean mRestoredFromBundle;

    private final ArrayList<Application.ActivityLifecycleCallbacks> mActivityLifecycleCallbacks =
            new ArrayList<Application.ActivityLifecycleCallbacks>();
    
    private Window mWindow;

    private WindowManager mWindowManager;
    
    private CharSequence mTitle;
    private int mTitleColor = 0;


    final Handler mHandler = new Handler();

    final FragmentController mFragments = FragmentController.createController(new HostCallbacks());
}

```

#### 包名命名规范

* 不允许包名中携带`英文大写`

* 包名应该以`简洁的方式`命名

* 包名要按照`模块`或者`作用`来划分

* 不要在某一包名下放置`一些无关的类`

#### 方法命名规范

* initXX：初始化相关方法，使用 `init` 为前缀标识，如初始化布局 initView

* isXX：方法返回值为 boolean 型的请使用 `is` 或 check 为前缀标识

* getXX：返回某个值的方法，使用 `get` 为前缀标识

* setXX：设置某个属性值

* handleXX/processXX：对数据进行处理的方法

* displayXX/showXX：弹出提示框和提示信息，使用 display/show 为前缀标识

* updateXX：更新数据

* saveXX：保存数据

* resetXX：重置数据

* clearXX：清除数据

* removeXX：移除数据或者视图等，如 removeView

* drawXX：绘制数据或效果相关的，使用 `draw` 前缀标识

#### 类文件命名规范

* 业务模块以 `模块` + `类型` 来命名，例如

    * HomeActivity.java
    
    * SettingFragment.java
    
    * HomeAdapter.java
    
    * AddressDialog.java

* 技术模块以类的 `作用` 来命名，例如

    * CrashHandler.java
    
    * GridSpaceDecoration.java
    
    * PickerLayoutManager.java
    
#### 接口文件命名规范

* 如果是监听事件可以参考 View 的写法及命名：

```java
public class View {

    private View.OnClickListener mListener;
    
    public void setOnClickListener(OnClickListener listener) {
        mListener = listener;
    }
    
    public interface OnClickListener {
    
        void onClick(View v);
    }
}
```

* 如果是回调事件可以参考 Handler 的写法及命名：

```java
public class Handler {

    public interface Callback {

        boolean handleMessage(Message msg);
    }
}
```

* 至于接口写在内部还是外部，具体可以看情况而定，如果功能比较庞大，

#### 布局文件命名规范

* 以 `模块` + `类型` 来命名，例如

    * `home_activity.xml`
    
    * `setting_fragment.xml`
    
    * `menu_item.xml`
    
    * `address_dialog.xml`
    
* 这样写的好处在于，由于 res 文件夹下是没有层级概念的

* 通过前缀的命名可以帮助我们更好定位到同一模块下的资源

* 例如分享对话框中，有对话框 Root 布局和 Item 布局

    * `share_dialog.xml`（Root 布局）
    
    * `share_item.xml`（Item 布局）
    
#### 资源文件命名规范

* 如果是业务模块下的资源，以 `模块` + `类型` 来命名，例如分享对话框的资源：

    * `share_link_ic.png`（复制链接）

    * `share_moment_ic.png`（分享到朋友圈）

    * `share_qq_ic.png`（分享到 QQ 好友）
    
    * `share_qzone_ic.png`（分享到 QQ 空间）
    
    * `share_wechat_ic.png`（分享到微信好友）
    
* 如果和业务模块不相干的资源，以 `作用` + `类型` 来命名，例如通用的控件样式资源：

    * `button_rect_selector.xml`（通用直角按钮样式）

    * `button_round_selector.xml`（通用圆角按钮样式）
    
* 这种资源有一个共同特点，它不属于哪个模块，但是每个模块都有用到，所以不能用模块名作为文件名前缀
    
#### 接口实现规范

* 一般情况下，我们会在类中这样实现接口，这样写的好处是，可以减少对象的创建，并且代码也比较美观

```java
public final class PasswordEditText extends EditText
        implements View.OnTouchListener,
        View.OnFocusChangeListener, TextWatcher {

    public PasswordEditText(Context context, AttributeSet attrs, int defStyleAttr) {
        super(context, attrs, defStyleAttr);
        setOnTouchListener(this);
        setOnFocusChangeListener(this);
        addTextChangedListener(this);
    }

    @Override
    public void onFocusChange(View view, boolean hasFocus) {
        ......
    }

    @Override
    public boolean onTouch(View view, MotionEvent event) {
        ......
    }

    @Override
    public void onTextChanged(CharSequence s, int start, int before, int count) {
        ......
    }

    @Override
    public void beforeTextChanged(CharSequence s, int start, int count, int after) {}

    @Override
    public void afterTextChanged(Editable s) {}
}
```

* 但是有一个美中不足的地方，就是在实现的接口过多时，我们很难分辨是哪个方法是哪个接口的，这个时候可以使用注释的方式来解决这个问题，加上 `@link` 还可以帮助我们快速定位接口类在项目中所在的位置

```java
public final class PasswordEditText extends EditText
        implements View.OnTouchListener,
        View.OnFocusChangeListener, TextWatcher {

    public PasswordEditText(Context context, AttributeSet attrs, int defStyleAttr) {
        super(context, attrs, defStyleAttr);
        setOnTouchListener(this);
        setOnFocusChangeListener(this);
        addTextChangedListener(this);
    }
    
    /**
     * {@link OnFocusChangeListener}
     */

    @Override
    public void onFocusChange(View view, boolean hasFocus) {
        ......
    }

    /**
     * {@link OnTouchListener}
     */

    @Override
    public boolean onTouch(View view, MotionEvent event) {
        ......
    }

    /**
     * {@link TextWatcher}
     */

    @Override
    public void onTextChanged(CharSequence s, int start, int before, int count) {
        ......
    }

    @Override
    public void beforeTextChanged(CharSequence s, int start, int count, int after) {}

    @Override
    public void afterTextChanged(Editable s) {}
}
```

#### 异常捕获规范

* 请不要使用此方式捕获异常，因为这种方式会把问题给隐藏掉，会加大问题的排查难度

```java
try {
    xxxxx.xxx();
} catch (Exception e) {}
```
* 如需捕获异常，请用以下方式进行捕获

```java
// 捕获这个异常，避免程序崩溃
try {
    // 目前发现在 Android 7.1 主线程被阻塞之后弹吐司会导致崩溃，可使用 Thread.sleep(5000) 进行复现
    // 查看源码得知 Google 已经在 Android 8.0 已经修复了此问题
    // 主线程阻塞之后 Toast 也会被阻塞，Toast 因为超时导致 Window Token 失效
    mHandler.handleMessage(msg);
} catch (WindowManager.BadTokenException | IllegalStateException ignored) {
    // android.view.WindowManager$BadTokenException：Unable to add window -- token android.os.BinderProxy is not valid; is your activity running?
    // java.lang.IllegalStateException：View android.widget.TextView has already been added to the window manager.
    e.printStackTrace();
}
```

* 必须要在 try 块中说明崩溃的缘由，并注明抛出的异常信息，并在代码中输出对应的日志

#### Activity 跳转约定

* 应当将 Intent 中的 key 常量保存到一个管理类中，又或者定在目标的 Activity 中

```java
public class IntentKey {

    /** id */
    public static final String ID = "id";
    /** token */
    public static final String TOKEN = "token";
    /** 订单 */
    public static final String ORDER = "order";
    /** 余额 */
    public static final String BALANCE = "balance";
    /** 时间 */
    public static final String TIME = "time";
    /** URL */
    public static final String URL = "url";
    /** 路径 */
    public static final String PATH = "path";
    /** 其他 */
    public static final String OTHER = "other";

    .....
}
```

* 如果跳转的 Activity 需要传递参数，应该在目标的 Activity 中定义静态的 `start` 又或者 `newIntent `方法

```java
public final class WebActivity extends Activity {

    public static void start(Context context, String url) {
        Intent intent = new Intent(context, WebActivity.class);
        intent.putExtra(IntentKey.URL, url);
        context.startActivity(intent);
    }
}
```

```java
public final class WebActivity extends Activity {

    public static Intent newIntent(Context context, String url) {
        Intent intent = new Intent(context, WebActivity.class);
        intent.putExtra(IntentKey.URL, url);
        return intent;
    }
}
```

* 如果创建的 Fragment 需要传递参数，应该在目标的 Fragment 中定义静态的 newInstance 方法

```java
public final class WebFragment extends Fragment {

    public static WebFragment newInstance(String url) {
        WebFragment fragment = new WebFragment();
        Bundle bundle = new Bundle();
        bundle.putString(IntentKey.URL, url);
        fragment.setArguments(bundle);
        return fragment;
    }
}
```

* 如果跳转的 Activity 或者创建的 Fragment 不需要传任何参数，可以不需要定义这些静态方法

#### 第三方框架使用规范

* 集成一些第三方框架或者 SDK，必须注明作用和出处，以便出现问题时能够快速核查和反馈

```groovy
// 权限请求框架：https://github.com/getActivity/XXPermissions
implementation 'com.hjq:xxpermissions:9.8'
```

* 不能选择功能两套相同的框架，应当引用最合适的一套框架进行开发，由此来降低代码的耦合度

* 使用第三方库必须要依赖指定的版本号，而不能使用 + 号来指定依赖库最新的版本号

* 使用第三方开源库出现问题或者 Bug 时应及时通知到开源库的作者，如果没有及时回复就根据实际情况对问题进行修复

* 尽量避免 Copy 第三方库的技术代码到项目中，特别是在放置到项目业务模块中，因为这样会增加项目的复杂度，从而降低可维护性

* 如果出现问题不能找到开源库的作者，如果需要修改，应当将这些代码抽取到单独的 Module 中

* 能用框架就用成熟框架，尽量不要自己编写或者修改框架，如果有需要，要对这块进行严格测试
    
#### 代码注释规范

* 类注释规范：author 是创建者（必填项）、time 是创建时间（必填项）、desc 是类的描述（必填项），doc 是文档地址（非必填），github 是开源地址（如果项目是开源的则必填，否则不填）

```java
/**
 *    author : 黄锦群
 *    github : https://github.com/getActivity/XXPermissions
 *    time   : 2018/06/15
 *    desc   : 权限请求实体类，参考 {@link Manifest.permission}
 *    doc    : https://developer.android.google.cn/reference/android/Manifest.permission?hl=zh_cn
 *             https://developer.android.google.cn/guide/topics/permissions/overview?hl=zh-cn#normal-dangerous
 */
public final class Permission {
    ....
}
```

* 方法注释规范：方法注释可根据实际情况而定，建议尽量用规范的命名来减少不必要的注释

```java
/**
 * 设置请求的对象
 *
 * @param activity          当前 Activity，可以传入栈顶的 Activity
 */
public static XXPermissions with(FragmentActivity activity) {
    return ....;
}
```

* 字段注释规范：根据字段的作用而定，建议尽量用规范的命名来减少不必要的注释

```java
/** 请求的权限组 */
private static final String REQUEST_PERMISSIONS = "request_permissions";

/** 权限回调对象 */
private OnPermissionCallback mCallBack;
```

* 变量注释规范（如果 API 是比较常见并且容易理解可以不用写，如果是复杂并且羞涩难懂则需要写上）

```java
// 设置保留实例，不会因为屏幕方向或配置变化而重新创建
fragment.setRetainInstance(true);
```

#### String ID 命名规范

* 以 `模块` + `功能` 来命名，例如

```xml
<!-- 主界面 -->
<string name="home_nav_index">首页</string>
<string name="home_nav_found">发现</string>
<string name="home_nav_message">消息</string>
<string name="home_nav_me">我的</string>
<string name="home_exit_hint">再按一次退出</string>

<!-- 登录界面 -->
<string name="login_register">注册</string>
<string name="login_phone_hint">请输入手机号</string>
<string name="login_password_hint">请输入密码</string>
<string name="login_forget">忘记密码？</string>
<string name="login_text">登录</string>
<string name="login_other">其他登录方式</string>

<!-- 注册界面 -->
<string name="register_title">注册</string>
<string name="register_hint">手机号仅用于登录和保护账号安全</string>
<string name="register_login">登录</string>
<string name="register_password_hint1">设置密码</string>
<string name="register_password_hint2">再次输入密码</string>
<string name="register_password_input_error">两次密码输入不一致，请重新输入</string>

<!-- 设置界面 -->
<string name="setting_title">设置</string>
<string name="setting_language">语言切换</string>
<string name="setting_language_simple">简体中文</string>
<string name="setting_language_complex">繁体中文</string>
```

#### Anim ID 命名规范

* 应用到某个模块 View

```xml
login_left_balloon_view.xml
login_right_balloon_view.xml
```

* 应用到全局 Activity

```xml
left_in_activity.xml
left_out_activity.xml
```

* 应用到全局 Dialog

```xml
bottom_in_dialog.xml
bottom_out_dialog.xml
```

#### View ID 命名规范

* 应该以`控件的缩写` + `模块名` + `作用` 来命名，例如

```xml
@+id/R.id.rg_login_type

@+id/R.id.et_login_phone

@+id/R.id.et_login_sms

@+id/R.id.et_login_password

@+id/R.id.btn_login_commit
```

* View 和 Layout 控件缩写表，这里列举最常见的几个

|   名称  |  缩写 |
| :-----: | :----: |
| TextView | tv |
| EditText | et |
| Button | btn |
| ImageView | iv |
| ImageButton | ib |
| ListView | lv |
| RecyclerView | rv |
| RadioButton | rb |
| RadioGroup | rg |
| ProgressBar | pb |
| CheckBox | cb |
| TableLayout | tl |
| ScrollView | sv |
| LinearLayout | ll |
| RelativeLayout | rl |
| FrameLayout | fl |

#### Style 样式命名规范

* 如果只是主题相关的样式，以 `Theme` 命名结尾，否则以 `Style` 命名结尾，命名要求尽量简洁，并且需要有代码注释，示例如下：

```xml
<!-- 应用主题样式 -->
<style name="AppTheme" parent="Theme.AppCompat.DayNight.NoActionBar">
    .....
</style>

<!-- 全屏主题样式 -->
<style name="FullScreenTheme" parent="AppTheme">
    .....
</style>

<!-- 闪屏页主题样式 -->
<style name="SplashTheme" parent="FullScreenTheme">
    .....
</style>
```

---

```xml
<!-- 默认圆角按钮样式 -->
<style name="ButtonStyle" parent="Widget.AppCompat.Button.Borderless">
    .....
</style>

<!-- 不带圆角按钮样式 -->
<style name="RectButtonStyle" parent="ButtonStyle">
    .....
</style>

<!-- 默认文本框样式 -->
<style name="EditTextStyle">
    .....
</style>

<!-- 验证码按钮样式 -->
<style name="CountdownViewStyle">
    .....
</style>
```

#### 资源使用规范

* `Color` 和 `Dimens` 允许写死在代码中，但是如果某个色值引用得比较多（例如主题强调色、通用背景色），需要进行抽取和统一

* 对于一些常用并且样式比较统一的控件，例如 `Button`、`EditText` 等，我们对这些控件的样式进行抽取到 `style.xml` 中来

* String 建议不要写死在 Java 和 Xml 代码中，如果项目没有国际化的需求，可以考虑直接写死，如果项目后续可能有国际化的需求，则不能直接写死在布局文件中

#### XML 编码规范

* 不推荐用 `dp` 作为字体单位，虽然在大部分手机上面 `dp` 和 `sp` 计算是差不多的，但是会有一部分老年用户群，例如咱们的爸爸妈妈爷爷奶奶，他们通常会把手机显示的字体大小调大，这样他们才不需要带眼镜看手机，如果我们用 `dp` 作为字体单位，无论手机怎么调整字体大小，应用的字体大小都不会有任何的变化，所以这种操作显然是非常不人性化的。

```xml
<!-- 错误写法示例 -->
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="老铁"
    android:textSize="18dp" />

<!-- 正确写法示例 -->
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="老铁"
    android:textSize="18sp" />
```

* 不能根据设计图给定的宽高把 `TextView` 或者 `Button` 的宽高定死，而是通过 `wrap_content` 的方式和 `padding` 来调整 View 的宽高，因为在不同手机上面字体大小不一致，在字体显示比较小的手机上面会显示正常，但是在字体显示比较大的平板上面文字上半部分极有可能会出现被裁剪的情况，所以我们不能把宽高定死，而是通过 `padding` 来调整到想要的控件大小。

```xml
<!-- 错误写法示例 -->
<Button
    android:layout_width="180dp"
    android:layout_height="60dp"
    android:gravity="center"
    android:text="提交" />

<!-- 正确写法示例 -->
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:gravity="center"
    android:paddingStart="80dp"
    android:paddingTop="20dp"
    android:paddingEnd="80dp"
    android:paddingBottom="20dp"
    android:text="提交" />
```

* `ImageView` 的宽高任一项定义成 `match_parent ` 时，另外一项不能写死大小，而是应该使用 `wrap_content`，否则很可能会导致图片变形，另外还需要使用 `android:adjustViewBounds="true"` 属性，否则 `ImageView` 无法根据图片的宽高来调整自己的宽高。

```xml
<!-- 错误写法示例 -->
<ImageView
    android:layout_width="match_parent"
    android:layout_height="300dp"
    android:src="@drawable/example_bg" />

<!-- 正确写法示例 -->
<ImageView
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:adjustViewBounds="true"
    android:src="@drawable/example_bg" />
```

* XML 节点编写应该规范，在没有子节点的情况下，应当以 `/>` 节点结尾，如果有则以 `</xxx.xxx.xxx>` 节点结尾

```xml
<!-- 错误写法示例 -->
<androidx.recyclerview.widget.RecyclerView
    android:layout_width="match_parent"
    android:layout_height="match_parent">
</androidx.recyclerview.widget.RecyclerView>

<!-- 正确写法示例 -->
<androidx.recyclerview.widget.RecyclerView
    android:layout_width="match_parent"
    android:layout_height="match_parent" />
```

---

```xml
<!-- 错误写法示例 -->
<TextView
    android:layout_width="match_parent"
    android:layout_height="match_parent">
</TextView>

<!-- 正确写法示例 -->
<TextView
    android:layout_width="match_parent"
    android:layout_height="match_parent" />
```

#### 预览属性约定

* 应该在某个 Layout 文件根布局中定义 tools:context 属性，以便在布局文件中快速定位到对应的类

    * `tools:context=".ui.activity.HomeActivity"`
    
    * `tools:context=".ui.fragment.SettingFragment"`
    
    * `tools:context=".ui.adapter.HomeAdapter"`
    
    * `tools:context=".ui.dialog.PersonDataDialog"`

```xml
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".ui.activity.HomeActivity">

</FrameLayout>
```


* 此外，tools 属性还有各种各样的用途，例如 RecyclerView 的 tools 属性

```xml
<androidx.recyclerview.widget.RecyclerView
    android:id="@+id/rv_pay_list"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:overScrollMode="never"

    tools:listitem="@layout/item_dialog_pay_password"
    tools:itemCount="9"

    tools:layoutManager="androidx.recyclerview.widget.GridLayoutManager"
    tools:spanCount="3" />
```

* tools 这种命名不止可以应用于 RecyclerView，还可以应用于其他 View 的属性，比如常用的 TextView 和 ImageView

```xml
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    tools:text="学生姓名" />

<ImageView
    android:id="@+id/iv_home_course_image"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    tools:src="@drawable/bg_home_placeholder" />
```
        
* 如果某个 TextView 显示的字符串是一成不变的，那么可以直接定义在布局文件中，如果是动态变化的，那么应该使用 `tools:text` 预览属性，而不应该使用 `android:text`，其他布局属性也同理

#### 致谢

* [阿里巴巴Android开发手册.pdf](阿里巴巴Android开发手册.pdf)

* [阿里巴巴Java开发手册.pdf](阿里巴巴Java开发手册.pdf)

#### 作者其他开源项目

* 安卓技术中台：[AndroidProject](https://github.com/getActivity/AndroidProject)

* 网络框架：[EasyHttp](https://github.com/getActivity/EasyHttp)

* 吐司框架：[ToastUtils](https://github.com/getActivity/ToastUtils)

* 权限框架：[XXPermissions](https://github.com/getActivity/XXPermissions)

* 标题栏框架：[TitleBar](https://github.com/getActivity/TitleBar)

* 悬浮窗框架：[XToast](https://github.com/getActivity/XToast)

* 国际化框架：[MultiLanguages](https://github.com/getActivity/MultiLanguages)

* Gson 解析容错：[GsonFactory](https://github.com/getActivity/GsonFactory)

* 日志查看框架：[Logcat](https://github.com/getActivity/Logcat)

#### Android技术讨论Q群：78797078

#### 微信公众号：Android轮子哥

![](https://raw.githubusercontent.com/getActivity/Donate/master/picture/official_ccount.png)

#### 如果您觉得我的开源库帮你节省了大量的开发时间，请扫描下方的二维码随意打赏，要是能打赏个 10.24 :monkey_face:就太:thumbsup:了。您的支持将鼓励我继续创作:octocat:

![](https://raw.githubusercontent.com/getActivity/Donate/master/picture/pay_ali.png) ![](https://raw.githubusercontent.com/getActivity/Donate/master/picture/pay_wechat.png)

## License

```text
Copyright 2021 Huang JinQun

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```