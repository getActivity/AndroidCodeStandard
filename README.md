# Android 代码规范文档

* 码云地址：[Gitee](https://gitee.com/getActivity/AndroidCodeStandard)

* 鸿洋力荐：[荐一份 Android 代码规范建议文档](https://mp.weixin.qq.com/s/Zv1zVom69RFrMJ1q8tP8Lw)

* 做开源几年了，被很多人夸过，你的代码写得比较规范，[甚至有人质疑自己代码的写法](https://github.com/getActivity/AndroidProject/issues/55)，但是迟迟没有出一个代码规范，说来惭愧，只是因为我早几年写的代码还不够规范，不敢出来误导大家，而代码规范是后续才慢慢养成的，在这个过程中，我不仅参考了大公司出的代码规范文档，也研究了很多关于谷歌源码的编码规范，同时我也在无时不刻在思考，如何能写出让别人更好理解的代码，自打入行以来，我就在一直在这个问题上面探索。

* 为什么要做成一个开源项目？因为项目会长期更新，大家如果对里面一些规范表示不能理解的或者感觉写得不太对的，又或者有什么想要补充的，随时欢迎你通过 **[issue](https://github.com/getActivity/AndroidCodeStandard/issues/new)** 反馈给我，大家的建议很重要，是我做好这件事的关键，我会认真对待和思考提出的每一个建议。同时我也相信一份好的代码规范经得住大众的反复推敲和不断实践，在这里也欢迎你提出自己的想法和建议。

* 这份代码规范文档开始编写的时间是 2020 年 7 月，中间不断地修改和补充，于 2021 年 1 月发布定稿，同年 2 月，纠正和补充了一些代码规范，从 0 到 1，从不成熟到成熟，整个过程耗时 200 多天。原因是我积累了很多开发的好习惯，但是一直没有任何记录，在短时间将这些东西全部输出几乎不可能，所以我前面花了很多时间回忆和总结，这段时间内我做的最多的一件事是，代码写着写着就去写代码规范文档，直到后面发布初稿时，我又投入了大把的时间和精力来做这件事。大家心中可能都有一个疑问，我为什么不用网上写的，直接照抄照搬，又或者直接采用阿里的，这样不是简单轻松多了？关于这个问题，可以跟大家谈谈我的想法，我看过很多关于 Android 代码规范文档，但是我感觉存在一些问题，可以跟大家分享一下：

    1. 说服力低：是很多代码规范文档只告诉你应该这样写，但是基本没有人提及这样写的好处，那样写不好的地方。他们只会告诉你规则，但是从不告诉你前因后果，这样写出来的代码规范难以服众。

    2. 不够全面：例如后台接口规范、接口实现规范、异常捕获规范、第三方框架使用规范、代码硬编码规范、资源硬编码规范、多模块规范；这些是我们开发中所避不开的东西，但是现在网上的代码规范文档却很少有人提及。

    3. 不够细致：我举个最简单的例子，很多代码规范文档都会说 **String ID** 以 **模块 + 作用** 来命名，但是没有人提及过在其他情况下的处理，例如：`确定取消` 这种字符串，虽然在很多模块中使用到了，但是它却不属于任何模块的，这个时候该怎么命名？这个虽然是小细节，但足以看出文档在细节处理上不够完美和严谨。

#### 更新日志

* 2021 年 3 月 28 日：[新增代码美观性要求](https://github.com/getActivity/AndroidCodeStandard/commit/692ada016c99db72e61fb75e20a7178d385bf669)

* 2021 年 3 月 11 日：[新增版本命名规范](https://github.com/getActivity/AndroidCodeStandard/commit/68f242c839ae040aaf4624fb8243137366b89cc9)

* 2021 年 2 月 23 日：[<br>补充代码规范原则<br>补充参数传递规范](https://github.com/getActivity/AndroidCodeStandard/commit/1a1ad4a7c26ff75e588b689c51ab126fe32c78a1)

* 2021 年 2 月 21 日：[<br>补充多模块规范<br>补充代码硬编码规范<br>补充资源硬编码规范<br>补充 Color ID 命名规范<br>补充写代码规范文档的原因<br>纠正公开成员变量命名方式<br>添加谷歌代码样式指南链接](https://github.com/getActivity/AndroidCodeStandard/commit/be4847c2c476031484bac97dec036228900e2f60)

* 2021 年 2 月 11 日：[补充异常捕获规范标准](https://github.com/getActivity/AndroidCodeStandard/commit/80688b1dc84ccf752d6c33e5e57291fd67ca2eef)

* 2021 年 2 月 9 日：[补充字符串 equals 使用规范](https://github.com/getActivity/AndroidCodeStandard/commit/78348cc554e89010a5c31b3bc05c8beeb3925b43)

* 2021 年 2 月 7 日：[补充做成开源项目的原因](https://github.com/getActivity/AndroidCodeStandard/commit/578d6e37b640adf9d3687c3eb562ff0ae58a131b)

* 2021 年 2 月 6 日：[补充注释规范和标准](https://github.com/getActivity/AndroidCodeStandard/commit/db7b469b5fe014d818ecdb14f070c8f58c93113c)

* 2021 年 2 月 6 日：[纠正后台返回金额的处理方式](https://github.com/getActivity/AndroidCodeStandard/commit/1bb107522a7e440d0632690aca798de1bd6d88a3)

* 2021 年 2 月 5 日：[新增文本间距的问题阐述](https://github.com/getActivity/AndroidCodeStandard/commit/35ac8b16a6c9066dd1185e733ed12838f7befba5)

* 2021 年 2 月 5 日：[修改全局变量为成员变量](https://github.com/getActivity/AndroidCodeStandard/commit/f9cd3730e6c08e79be012133e6e4d89b315580aa)

* 2021 年 2 月 5 日：[优化描述的语言艺术](https://github.com/getActivity/AndroidCodeStandard/commit/2cb35de115327227d37b9efc6477505011d939f5)

* 2021 年 2 月 5 日：[添加码云地址](https://github.com/getActivity/AndroidCodeStandard/commits/master)

* 2021 年 2 月 5 日：[第一次提交代码](https://github.com/getActivity/AndroidCodeStandard/commit/490a8d3e3695dd30a952ded71969fda83daaa58c)

#### 目录

* [前言](#前言)

* [代码规范原则](#代码规范原则)

* [常规规范](#常规规范)

* [后台接口规范](#后台接口规范)

* [变量命名规范](#变量命名规范)

* [包名命名规范](#包名命名规范)

* [方法命名规范](#方法命名规范)

* [类文件命名规范](#类文件命名规范)

* [接口文件命名规范](#接口文件命名规范)

* [接口实现规范](#接口实现规范)

* [异常捕获规范](#异常捕获规范)

* [参数传递规范](#参数传递规范)

* [代码美观性要求](#代码美观性要求)

* [第三方框架使用规范](#第三方框架使用规范)

* [多模块规范](#多模块规范)

* [代码注释规范](#代码注释规范)

* [代码硬编码规范](#代码硬编码规范)

* [布局文件命名规范](#布局文件命名规范)

* [资源文件命名规范](#资源文件命名规范)

* [String ID 命名规范](#string-id-命名规范)

* [Color ID 命名规范](#color-id-命名规范)

* [Anim ID 命名规范](#anim-id-命名规范)

* [View ID 命名规范](#view-id-命名规范)

* [Style 命名规范](#style-命名规范)

* [XML 编码规范](#xml-编码规范)

* [预览属性约定](#预览属性约定)

* [资源硬编码规范](#资源硬编码规范)

* [版本命名规范](#版本命名规范)

* [致谢](#致谢)

#### 前言

* 代码规范是我们每个程序员要做的事，假设我们按照自己的喜好来写代码，那么很可能出现的问题就是**我看不懂你的代码**或者**你看不懂我的代码**，这样会给后续维护形成**巨大的障碍**。这个时候问题来了，如何让代码不分你我，或许只需要一套规则，你和我都认可并且遵守的代码规范守则。

* 那么你的疑问可能又来了，怎么样才能算好的代码规范，答案只有一个，真正好的代码规范就是别人的代码你一眼就能看懂，更不需要反复去看。之所以这样并不是因为看的人 Review 代码的能力有多强，而是写代码的人愿意遵守规则，他知道自己想这么写，但是知道你会看不懂，所以换了一种方式来写，这种方式就是**代码规范**。

* 代码规范：一个好的代码规范可以帮助我们快速了解和熟悉相关的业务，降低后续维护的成本（二次开发或者排查问题）。

* 代码不规范：代码不规范会导致项目可读性变差，具体表现为**难分辨和难理解**，在无形之中加大项目后续维护的成本。

* 经验总结：**编码不规范，同行泪两行**

#### 代码规范原则

* 在讲之前，我们先想一个问题，代码规范的出现是为了什么？不就为了让我们更好地进行团队协作和项目维护吗？没错的，所以代码规范原则应该围绕这两个目标进行。

    * **特事特办**：代码规范文档只能解决 **99.99%** 场景下的问题，特殊情况应该要特殊处理，违背者需要给出**合理的解释**，建议在代码中直接**用注释注明**，这样可以**减少沟通成本**，否则在一般情况下应当要遵守代码规范文档上的约束。

    * **以人为本**：我们应该衡量不同写法带来的优点和缺点，然后根据当前项目的实际需求做出合适的选择或者变化。规则是人定的，不是**一成不变**的。在制定新的规则或者修改旧的规则之前应当先**参考和分析**谷歌或者知名公司的做法，然后与团队中的各个成员**沟通和协商好**。
    
    * **实事求事**：任何代码规范都应该追求在实际开发中发挥的作用或者效果，规则始终是规则，不能单纯为了制定规则而编写代码规范，而是更应该追求写法的实用性，实用性应该从**代码理解的难易程度**、**代码可维护性**、**代码可复用性**、**代码可扩展性**等方面因素综合考虑，其次是考虑**代码的视觉美观性**。

#### 常规规范

* 使用 **0px** 代替 **0dp**，这样就可以在获取时避免系统进行换算，提升代码的执行效率。

* 字符串比较，应该用 `"xxx".equals(object)`，而不应该用 `object.equals("xxx")`，因为 **object** 对象可能为空，我们应该把不为空的条件放置在表达式的前面。

* 尽量采用 **switch case** 来判断，如果不能实现则再考虑用 **if else**，因为在多条件下使用 **switch case** 语句判断会更加简洁。

* 不推荐用 **layout_marginLeft**，而应该用 **layout_marginStart**；不推荐用 **layout_marginRight**，而应该用 **layout_marginEnd**，原因有两个，一个是适配 Android 4.4 **反方向特性**（可在开发者选项中开启），第二个是 XML 布局中使用 **layout_marginLeft** 和 **layout_marginRight** 会有代码警告，**padding** 属性也是同理，这里不再赘述。

* 如果在 **layout_marginStart** 和 **layout_marginEnd** 的值相同的情况下，请替换使用 **layout_marginHorizontal**，而 **layout_marginTop** 和 **layout_marginBottom** 也同理，请替换使用 **layout_marginVertical**，能用一句代码能做的事不要写两句，**padding** 属性也是同理，这里不再赘述。

* **过期** 和 **高版本** 的 API 一定要做对应的兼容（包含 Java 代码和 XML 属性），如果不需要兼容处理的，需要对警告进行抑制。

* 在能满足需求的情况下，尽量用 **invisible** 来代替 **gone**，因为 **gone** 会触发当前整个 View 树进行重新测量和绘制。

* **api** 和 **implementation**，在能满足使用的情况下，优先选用 **implementation**，因为这样可以[减少一些编译时间](https://www.jianshu.com/p/8962d6ba936e)。

* **ListView** 和 **RecyclerView** 都能实现需求的前提下，优先选用 **RecyclerView**，具体原因不解释，大家应该都懂。

* **ScrollView** 和 **NestedScrollView** 都能实现需求的前提下，优先选用 **NestedScrollView**，是因为 **NestedScrollView** 和 **RecyclerView** 支持相互嵌套，而 **ScrollView** 是不支持嵌套滚动的。

* 不能在项目中创建副本文件，例如创建 `HomeActivity2.java`、`home_activity_v2.xml` 类似的副本文件，因为这样不仅会增加项目的维护难度，同时对编译速度也会造成一定的影响，正确的做法应该是在原有的文件基础上面修改，如果出现需求变更的情况，请直接使用 **Git** 或者 **SVN** 进行版本回退。

* 如果一个类不需要被继承，请直接用 **final** 进行修饰，如果一个字段在类初始化过程中已经赋值并且没有地方进行二次赋值，也应当用 **final** 修饰，如果一个字段不需要被外部访问，那么需要用 **private** 进行修饰。

* 每个小组成员应当安装[阿里巴巴代码约束插件](https://plugins.jetbrains.com/plugin/10046-alibaba-java-coding-guidelines)，并及时地对插件所提示的**代码警告**进行处理或者抑制警告。

* 应用图标应该放在 **mipmap** 目录下，其他图片资源应当放到 **drawable** 目录下，具体原因可以看[谷歌官方文档](https://developer.android.google.cn/guide/topics/resources/providing-resources)对这两个文件夹给出的介绍：

|    目录        | 资源类型                                                     |
| :---------- | :----------------------------------------------------------- |
|  `drawable` | 位图文件（`.png`、`.9.png`、`.jpg`、`.gif`）或编译为以下可绘制对象资源子类型的 XML 文件：位图文件九宫格（可调整大小的位图）状态列表形状动画可绘制对象其他可绘制对象请参阅 [Drawable 资源](https://developer.android.google.cn/guide/topics/resources/drawable-resource)。 |
|  `mipmap`   | 适用于不同启动器图标密度的可绘制对象文件。如需了解有关使用 `mipmap` 文件夹管理启动器图标的详细信息，请参阅[管理项目概览](https://developer.android.google.cn/tools/projects#mipmap)。 |

#### 后台接口规范

* 后台返回的 **id 值**，不要使用 **int** 或者 **long** 类型来接收，而应该用 **string** 类型来接收，因为我们不需要对这个 **id 值**进行运算，所以我们不需要关心它是什么类型的。

* 后台返回的**金额数值**应该使用 **String** 来接收，而不能用**浮点数**来接收，因为 **float** 或者 **double** 在数值比较大的时候会容易丢失精度，并且还需要自己手动转换出想要保留的小数位，最好的方式是后台返回什么前端就展示什么，而到了运算的时候，则应该用 **BigDecimal** 类来进行转换和计算，当然金额在前端一般展示居多，运算的情况还算是比较少的。

* 我们在定义后台返回的 Bean 类时，不应当将一些我们没有使用到的字段添加到代码中，因为这样会消耗性能，因为 Gson 是通过**反射**将后台字段赋值到 Java 字段中，所以我们应当避免一些不必要的字段解析，另外臃余的字段也会给我们排查问题造成一定的阻碍。

* 如果后台给定的字段名不符合代码命名的时候，例如当遇到 `student_name` 这种命名时，我们应当使用 Gson 框架中的 **@SerializedName** 注解进行重命名。

* 请求的接口参数和返回字段必须要写上注释，除此之外还应该备注对应的后台接口文档地址，以便我们后续能够更好地进行维护和迭代。

* 后台返回的 Bean 类字段不能直接访问，而应该通过生成 **Get** 方法，然后使用这个 **Get** 方法来访问字段。

* 接口请求成功的提示可以不显示，但请求失败的提示需要显示给到用户，否则会加大排查问题的难度，也极有可能会把问题掩盖掉，从而导致问题遗留到线上去。

#### 变量命名规范

* **严禁使用中文或者中文拼音**进行重命名

* 使用**驼峰式命名风格**（单词最好控制在三个以内）

* 局部变量或者公开的成员变量应该以作用来命名，例如：

```java
public String name;
public TextView nameView;
public FrameLayout nameLayout;
```

```java
// 命名规范附带技巧（当布局中同个类型的控件只有一个的时候，也可以这样命名）
public TextView textView;
public RecyclerView recyclerView;
```

* 非公开的成员变量必须以小 **m** 开头，例如：

```java
private String mName;
private TextView mNameView;
private FrameLayout mNameLayout;
```

```java
// 命名规范附带技巧（当布局中同个类型的控件只有一个的时候，也可以这样命名）
private TextView mTextView;
private RecyclerView mRecyclerView;
```

* 布尔值命名规范，无论是局部变量还是成员变量，都不应该携带 **is**，例如：

```java
// 不规范写法示例
private boolean mIsDebug;
boolean isDebug;
```

```java
// 规范写法示例
private boolean mDebug;
boolean debug;
```
        
* 静态变量则用小 **s** 开头，例如：

```java
static Handler sHandler;
```

* 常量则需要用大写，并且用下划线代替驼峰，例如：

```java
static final String REQUEST_INSTALL_PACKAGES;
```

* 有细心的同学可能会发现一个问题，为什么我们最常用的 Glide 和 OkHttp 的源码中，非公开的成员变量为什么没有用小 `m` 开头？但是谷歌的 SDK 源码和 Support 库就有呢？那究竟是用还是不用呢？这个问题其实很好回答，我们可以先从体量上分析，首先谷歌的开发人员和项目数量肯定是最多的，那么谷歌在这块的探索和研究肯定是多于 Glie 和 OkHttp 的，其次是 Glide 和 OkHttp 的源码都有一个特点，很多类都维持在 1k 行代码左右，而谷歌源码很多类都接近 10k 行代码，例如 Activity 的源码在 API 30 上面有 8.8k 行代码，所以谷歌在这块略胜一筹，如果非要二选一，我选择谷歌的代码风格，并不是说 Glide 和 OkHttp 命名风格不好，是因为或许在未来的某一天，可能会有新的图片请求框架和网络请求框架来代替 Glide 和 OkHttp，但是基本不可能会出现有代替 Android SDK 或者 Support 库的一天。

* 最后让我们静静地欣赏一下 **Activity** 类中成员变量的命名：

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

* 不允许包名中携带**英文大写**

* 包名应该以**简洁的方式**命名

* 包名要按照**模块**或者**作用**来划分

* 请不要在某一包名下放置**一些无关的类**

#### 方法命名规范

* initXX：初始化相关方法，使用 **init** 为前缀标识，如初始化布局 **initView**

* isXX：方法返回值为 boolean 型的请使用 **is** 或 **check** 为前缀标识

* getXX：返回某个值的方法，使用 **get** 为前缀标识，例如 **getName**

* setXX：设置某个属性值，使用 **set** 为前缀标识，例如 **setName**

* handleXX/processXX：对数据进行处理的方法，例如 **handleMessage**

* displayXX/showXX：弹出提示框和提示信息，例如 **showDialog**

* updateXX：更新某个东西，例如 **updateData**

* saveXX：保存某个东西，例如 **saveData**

* resetXX：重置某个东西，例如 **resetData**

* clearXX：清除某个东西，例如 **clearData**

* removeXX：移除数据或者视图等，例如 **removeView**

* drawXX：绘制数据或效果相关的，使用 **draw** 前缀标识，例如 **drawText**

#### 类文件命名规范

* 业务模块：请以 **模块 + 类型** 来命名，例如：

```text
HomeActivity.java

SettingFragment.java

HomeAdapter.java

AddressDialog.java
```

* 技术模块：请以类的 **作用** 来命名，例如：

```text
CrashHandler.java

GridSpaceDecoration.java

PickerLayoutManager.java
```

#### 接口文件命名规范

* 如果是监听事件可以参考 **View** 的写法及命名：

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

* 如果是回调事件可以参考 **Handler** 的写法及命名：

```java
public class Handler {

    public interface Callback {

        boolean handleMessage(Message msg);
    }
}
```

* 至于接口写在内部还是外部，具体可以视实际情况而定，如果功能比较庞大，就可以考虑抽取成外部的，只作用在某个类上的，则就可以直接写成内部的。

#### 接口实现规范

* 一般情况下，我们会在类中这样实现接口，这样写的好处是，可以减少对象的创建，并且代码也比较美观。

```java
public final class PasswordEditText extends EditText implements View.OnTouchListener, View.OnFocusChangeListener, TextWatcher {

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
    public void beforeTextChanged(CharSequence s, int start, int count, int after) {
        ......
    }

    @Override
    public void afterTextChanged(Editable s) {
        ......
    }
}
```

* 但是有两个美中不足的地方，就是在实现的接口过多时，我们很难分辨是哪个方法是哪个接口的，这个时候可以使用注释的方式来解决这个问题，加上 **@link** 还可以帮助我们快速定位接口类在项目中所在的位置；另外一个是 **implements** 修饰符换行的问题，合理的换行会使代码更加简单直观。

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
    public void beforeTextChanged(CharSequence s, int start, int count, int after) {
        ......
    }

    @Override
    public void afterTextChanged(Editable s) {
        ......
    }
}
```

#### 异常捕获规范

* 请不要使用此方式捕获异常，因为这种方式会把问题给隐藏掉，从而会加大后续排查问题的难度。

```java
try {
    Xxx.xxx();
} catch (Exception e) {}
```

* 如需捕获异常，请用以下方式进行捕获，列出具体的异常类型，并在代码中输出对应的日志。

```java
// 捕获这个异常，避免程序崩溃
try {
    // 目前发现在 Android 7.1 主线程被阻塞之后弹吐司会导致崩溃，可使用 Thread.sleep(5000) 进行复现
    // 查看源码得知 Google 已经在 Android 8.0 已经修复了此问题
    // 主线程阻塞之后 Toast 也会被阻塞，Toast 因为显示超时导致 Window Token 失效
    mHandler.handleMessage(msg);
} catch (WindowManager.BadTokenException | IllegalStateException e) {
    // android.view.WindowManager$BadTokenException：Unable to add window -- token android.os.BinderProxy is not valid; is your activity running?
    // java.lang.IllegalStateException：View android.widget.TextView has already been added to the window manager.
    e.printStackTrace();
    // 又或者上报到 Bugly 错误分析中
    // CrashReport.postCatchedException(e);
}
```

* 如果这个异常不是通过方法 throws 关键字抛出，则需要在 try 块中说明崩溃的缘由，并注明抛出的异常信息。

* 还有一个问题，有异常就一定要 `try catch` ？，这种想法其实是错的，例如我们项目用 Glide 加载图片会抛出以下异常：

```java
Caused by: java.lang.IllegalArgumentException: You cannot start a load for a destroyed activity
   at com.bumptech.glide.manager.RequestManagerRetriever.assertNotDestroyed(RequestManagerRetriever.java:348)
   at com.bumptech.glide.manager.RequestManagerRetriever.get(RequestManagerRetriever.java:148)
   at com.bumptech.glide.Glide.with(Glide.java:826)
```

* 这是因为 Activity 的销毁了而去加载图片导致的（场景：异步执行图片加载），大多人的解决方式可能是：

```java
try {
    // Activity 销毁后执行加载图片会触发 crash
    Glide.with(this)
            .load(url)
            .into(mImageView);
} catch (IllegalArgumentException e) {
    // java.lang.IllegalArgumentException: You cannot start a load for a destroyed activity
    e.printStackTrace();
}
```

* 虽然这种方式可以解决 **crash** 的问题，但是显得**不够严谨**，Glide 抛异常给外层，其实无非就想告诉调用者，调用的时机错了，正确的处理方式不是直接捕获这个异常，而是应该在外层做好逻辑判断，避免会进入出现 **crash** 的代码，正确的处理示例如下：

```java
if (isFinishing() || isDestroyed()) {
   // Glide：You cannot start a load for a destroyed activity
    return;
}
Glide.with(this)
        .load(url)
        .into(mImageView);
```

* 所以尽量不要通过捕获的方式来处理异常，除非外层真的判断不了，否则应该通过一些逻辑判断来避免进入一些会 **crash** 的代码。

#### 参数传递规范

* 应当将 Intent 中的 key 常量保存到一个管理类中，如果不想单独定义一个 IntentKey 类，也可以直接将 key 值直接定义目标的 Activity 中。

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

* 如果跳转的 Activity 需要传递参数，应该在目标的 Activity 中定义静态的 **start** 又或者 **newIntent** 方法。

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

* 如果创建的 Fragment 需要传递参数，应该在目标的 Fragment 中定义静态的 **newInstance** 方法

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

* 如果跳转的 Activity 或者创建的 Fragment 不需要传任何参数，可以不需要定义这些静态方法。

* 另外如果一个界面需要传递的参数过多（5 个以上），建议用一个对象对这些参数进行封装，然后实现 Serializable 或者 Parcelable 接口进行传递，具体写法示例：

```java
public final class VideoPlayActivity extends Activity {

    /**
     * 播放参数构建
     */
    public static final class Builder implements Parcelable {

        /** 视频源 */
        private String mVideoSource;
        /** 视频标题 */
        private String mVideoTitle;
        /** 播放进度 */
        private int mPlayProgress;
        /** 手势开关 */
        private boolean mGestureEnabled = true;
        /** 循环播放 */
        private boolean mLoopPlay = false;
        /** 自动播放 */
        private boolean mAutoPlay = true;
        /** 播放完关闭 */
        private boolean mAutoOver = true;

        public Builder() {}

        public Builder setVideoSource(File file) {
            mVideoSource = file.getPath();
            if (mVideoTitle == null) {
                mVideoTitle = file.getName();
            }
            return this;
        }

        public Builder setVideoSource(String url) {
            mVideoSource = url;
            return this;
        }

        private String getVideoSource() {
            return mVideoSource;
        }

        public Builder setVideoTitle(String title) {
            mVideoTitle = title;
            return this;
        }

        private String getVideoTitle() {
            return mVideoTitle;
        }

        public Builder setPlayProgress(int progress) {
            mPlayProgress = progress;
            return this;
        }

        private int getPlayProgress() {
            return mPlayProgress;
        }

        public Builder setGestureEnabled(boolean enabled) {
            mGestureEnabled = enabled;
            return this;
        }

        private boolean isGestureEnabled() {
            return mGestureEnabled;
        }

        public Builder setLoopPlay(boolean enabled) {
            mLoopPlay = enabled;
            return this;
        }

        private boolean isLoopPlay() {
            return mLoopPlay;
        }

        public Builder setAutoPlay(boolean enabled) {
            mAutoPlay = enabled;
            return this;
        }

        public boolean isAutoPlay() {
            return mAutoPlay;
        }

        public Builder setAutoOver(boolean enabled) {
            mAutoOver = enabled;
            return this;
        }

        private boolean isAutoOver() {
            return mAutoOver;
        }

        public void start(Context context) {
            Intent intent = new Intent(context, VideoPlayActivity.class);
            intent.putExtra(IntentKey.VIDEO, this);
            if (!(context instanceof Activity)) {
                intent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
            }
            context.startActivity(intent);
        }
    }
}
```

```java
new VideoPlayActivity.Builder()
        .setVideoTitle("速度与激情特别行动")
        .setVideoSource("http://xxxxx.mp4")
        .start(getAttachActivity());
```

#### 代码美观性要求

* 第一个大括号应当统一放在表达式后面，而不应该换行处理，例如：

```java
// 不规范写法示例
if (AppConfig.isDebug())
{
    ......
}
```

```java
// 规范写法示例
if (AppConfig.isDebug()) {
    ......
}
```

* 代码之间应当有适当的空格，空格不用多也不能少，恰到好处即可，例如：

```java
// 不规范写法示例
public static boolean isAppInstalled(Context context ,String packageName ){
    try {
        context.getPackageManager().getApplicationInfo(packageName,0);
        return   true;
    }catch( PackageManager.NameNotFoundException e ){
        e.printStackTrace();
        return false ;
    }
}
```

```java
// 规范写法示例
public static boolean isAppInstalled(Context context, String packageName) {
    try {
        context.getPackageManager().getApplicationInfo(packageName, 0);
        return true;
    } catch (PackageManager.NameNotFoundException e) {
        e.printStackTrace();
        return false;
    }
}
```

* 适当换行有助于提升代码的可读性，在单行代码较长的情况下可以考虑换行，例如：

```java
// 不规范写法示例
ScaleAnimation animation = new ScaleAnimation(1.0f, 1.1f, 1.0f, 1.1f, Animation.RELATIVE_TO_SELF, 0.5f, Animation.RELATIVE_TO_SELF, 0.5f);
textView.startAnimation(animation);
```

```java
// 规范写法示例
ScaleAnimation animation = new ScaleAnimation(1.0f, 1.1f, 1.0f, 1.1f,
        Animation.RELATIVE_TO_SELF, 0.5f, Animation.RELATIVE_TO_SELF, 0.5f);
textView.startAnimation(animation);
```

* 链式写法不能只用一行代码，而是应当遵守一句 API 换一行的策略，例如：

```java
// 不规范写法示例
GlideApp.with(this).load(url).circleCrop().into(imageView);
```

```java
// 规范写法示例
GlideApp.with(this)
        .load(url)
        .circleCrop()
        .into(imageView);
```

* 方法参数的排序，上下文参数应当统一放在最前面，而回调监听应当统一放在最后面，例如：

```java
public void openSystemFileChooser(Activity activity, FileChooserParams params, ValueCallback<Uri[]> callback) {
    ......
}
```

* 变量和方法的排序，应当根据重要程度、API 类型、执行顺序这几点来摆放，例如：

```java
// 变量排序示例
public class BaseDialog {

    public static class Builder<B extends BaseDialog.Builder<?>>

        /** 宽度和高度 */
        private int mWidth = WindowManager.LayoutParams.WRAP_CONTENT;
        private int mHeight = WindowManager.LayoutParams.WRAP_CONTENT;

        /** 是否能够被取消 */
        private boolean mCancelable = true;
        /** 点击空白是否能够取消  前提是这个对话框可以被取消 */
        private boolean mCanceledOnTouchOutside = true;

        /** 背景遮盖层开关 */
        private boolean mBackgroundDimEnabled = true;
        /** 背景遮盖层透明度 */
        private float mBackgroundDimAmount = 0.5f;

        /** Dialog 创建监听 */
        private BaseDialog.OnCreateListener mCreateListener;
        /** Dialog 显示监听 */
        private final List<BaseDialog.OnShowListener> mShowListeners = new ArrayList<>();
        /** Dialog 取消监听 */
        private final List<BaseDialog.OnCancelListener> mCancelListeners = new ArrayList<>();
        /** Dialog 销毁监听 */
        private final List<BaseDialog.OnDismissListener> mDismissListeners = new ArrayList<>();
        /** Dialog 按键监听 */
        private BaseDialog.OnKeyListener mKeyListener;
    }
}
```

```java
// 方法排序示例
public class BaseDialog {

    public static class Builder<B extends BaseDialog.Builder<?>>

        /**
         * 设置宽度
         */
        public B setWidth(int width) {
            ......
        }

        /**
         * 设置高度
         */
        public B setHeight(int height) {
            ......
        }

        /**
         * 是否可以取消
         */
        public B setCancelable(boolean cancelable) {
            ......
        }

        /**
         * 是否可以通过点击空白区域取消
         */
        public B setCanceledOnTouchOutside(boolean cancel) {
            ......
        }

        /**
         * 设置背景遮盖层开关
         */
        public B setBackgroundDimEnabled(boolean enabled) {
            ......
        }

        /**
         * 设置背景遮盖层的透明度（前提条件是背景遮盖层开关必须是为开启状态）
         */
        public B setBackgroundDimAmount(float dimAmount) {
            ......
        }

        /**
         * 设置创建监听
         */
        public B setOnCreateListener(BaseDialog.OnCreateListener listener) {
            ......
        }

        /**
         * 添加显示监听
         */
        public B addOnShowListener(BaseDialog.OnShowListener listener) {
            ......
        }

        /**
         * 添加取消监听
         */
        public B addOnCancelListener(BaseDialog.OnCancelListener listener) {
            ......
        }

        /**
         * 添加销毁监听
         */
        public B addOnDismissListener(BaseDialog.OnDismissListener listener) {
            ......
        }

        /**
         * 设置按键监听
         */
        public B setOnKeyListener(BaseDialog.OnKeyListener listener) {
            ......
        }
    }
}
```

* 代码美观性虽然不会干扰到业务的正常进行，但是对一个程序员来讲，它是对技术的一种追求和热爱，同时也是工匠精神的体现。

#### 第三方框架使用规范

* 集成一些第三方框架或者 SDK，必须注明作用和出处，以便出现问题时能够快速核查和反馈。

```groovy
// 权限请求框架：https://github.com/getActivity/XXPermissions
implementation 'com.hjq:xxpermissions:10.6'
```

* 尽量不要选择功能两套相同的框架，应当引用最合适的一套框架进行开发。

* 使用第三方库必须要依赖指定的版本号，而不能使用 `latest-version` 或者  `+` 来指定依赖库最新的版本号。

* 使用第三方开源库出现问题或者 Bug 时应及时通知到开源库的作者，如果没有及时回复就根据实际情况对问题进行修复。

* 尽量避免 Copy 第三方库的技术代码到项目中，特别是在放置到项目业务模块中，因为这样会增加项目的复杂度，从而降低可维护性。

* 如果出现问题不能找到开源库的作者，如果需要修改，应当将这些代码抽取到单独的 Module 中。

* 能用框架就用成熟框架，尽量不要自己编写或者修改框架，如果有需要，要对这块进行严格测试。

#### 多模块规范

* 模块命名规范：应该以简单明了的方式来命名

```text
app
base
widget
umeng
course
socket
live
shop
```

* 模块混淆配置：请不要使用 `proguardFiles` 语句，而是应该使用 `consumerProguardFiles` 语句，因为 `consumerProguardFiles` 语句会将混淆规则和资源代码一同打包到 **aar** 包中，这样做的好处在于：在项目编译时会将 aar 包中的混淆规则合并到主模块中。

```groovy
android {

    defaultConfig {
        // 模块混淆配置
        consumerProguardFiles 'proguard-xxx.pro'
    }
}
```

* 资源前缀限制：我们应该在模块中加入此限制，这样我们在模块中添加资源时，编译器如果发现资源名称前缀不符合规范，则会出现代码警告。这样做的好处在于，以某一名称作为前缀，可以有效避免在编译时引发的一些资源合并冲突。

```groovy
android {
    // 资源前缀限制
    resourcePrefix "xxx_"
}
```

* 框架版本管理：我们应该统一抽取框架的版本到 `config.gradle` 文件中：

```groovy
ext {

    android = [compileSdkVersion       : 28,
               minSdkVersion           : 19,
               targetSdkVersion        : 28,
               versionCode             : 40102,
               versionName             : "4.1.2",
    ]
    dependencies = [
            "appcompat"                    : "androidx.appcompat:appcompat:1.2.0",
            "material"                     : "com.google.android.material:material:1.2.0",
    ]
}
```

* 然后在每个模块下这样定义，这样做的好处是可以做到版本号的统一管理。

```groovy
apply from : '../config.gradle'

android {
    compileSdkVersion rootProject.ext.android["compileSdkVersion"]

    defaultConfig {
        minSdkVersion rootProject.ext.android["minSdkVersion"]
        targetSdkVersion rootProject.ext.android["targetSdkVersion"]
    }
}
dependencies {
    implementation rootProject.ext.dependencies["appcompat"]
    implementation rootProject.ext.dependencies["material"]
}
```

* 除此之外还有另外一种写法，我们可以把 `config.gradle` 修改成这样：

```groovy
android {
    compileSdkVersion 28

    defaultConfig {
        minSdkVersion 19
        targetSdkVersion 28
        versionName '4.1.2'
        versionCode 40102
    }
}

dependencies {
    implementation 'androidx.appcompat:appcompat:1.2.0'
    implementation 'com.google.android.material:material:1.2.1'
}
```

* 然后在每个模块上添加一句引用即可，相比上一种写方法，这种方式更强大，因为它不仅可以配置版本号，还支持统一其他的配置项。

```groovy
apply from : '../config.gradle'
```

* 具体要用哪一种，可以根据实际情况而定，如果项目采用的是组件化，则可以考虑使用第一种方式，如果项目采用的是模块化，则可以考虑使用第二种方式，当然两种一起结合用也是可以的。

#### 代码注释规范

* 类注释规范：**author** 是创建者（必填项）、**time** 是创建时间（必填项）、**desc** 是类的描述（必填项），**doc** 是文档地址（非必填），**github** 是开源地址（如果项目是开源的则必填，否则不填）

```java
/**
 *    author : Android 轮子哥
 *    github : https://github.com/getActivity/XXPermissions
 *    time   : 2018/06/15
 *    desc   : 权限请求实体类
 *    doc    : https://developer.android.google.cn/reference/android/Manifest.permission?hl=zh_cn
 *             https://developer.android.google.cn/guide/topics/permissions/overview?hl=zh-cn#normal-dangerous
 */
public final class Permission {
    ....
}
```

* 方法注释规范：方法注释可根据实际情况而定

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

* 字段注释规范：根据字段的作用而定

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

* 注释什么情况下要写？什么情况下不用写？这个问题我很有感触，代码注释写多了不好，显得太啰嗦，也会增加工作量，写少了也不好，又怕别人看不懂，也害怕给自己后面留坑。我个人的建议是尽量用规范的命名来减少不必要的注释，很多时候我们只需要换位思考一下，忘记这段代码是自己写的，再问一下自己能不能一下子读懂，如果可以的话，注释就可以不用写，否则注释还是要考虑写上。

#### 代码硬编码规范

* 请尽量避免使用硬编码，例如系统的一些常量值，不能直接写死，而是应该通过代码引用，例如：

```java
// 不规范写法示例
if (view.getVisibility() != 0) {
    return;
}

Intent intent = new Intent("android.settings.APPLICATION_DETAILS_SETTINGS");
startActivity(intent);
```

```java
// 规范写法示例
if (view.getVisibility() != View.VISIBLE) {
    return;
}

Intent intent = new Intent(Settings.ACTION_APPLICATION_DETAILS_SETTINGS);
startActivity(intent);
```

* 在项目开发中，被多次使用到的数值或者字符串也应该提取成常量来供外部引用，例如：

```java
public final class UserInfoManager {

    /** 学生 */
    public static final int TYPE_STUDENT = 0;

    /** 老师 */
    public static final int TYPE_TEACHER = 1;

    /** 家长 */
    public static final int TYPE_PATRIARCH = 2;
}
```

* 但并不代表所有的数值都需要常量化，有一些数值常量化的意义并不大，例如：

```java
ValueAnimator animator = ValueAnimator.ofInt(0, 100);
animator.setDuration(500);
animator.start();
```

* 所以衡量一个数值或者字符串是否进行常量化的标准有两点：

	* 这个数值或者字符串是否会被多次使用
	
	* 这个数值或者字符串是否具有一定的含义

#### 布局文件命名规范

* 以 **模块 + 类型** 来命名，例如：

```text
home_activity.xml

setting_fragment.xml

menu_item.xml

address_dialog.xml
```

* 这样写的好处在于，由于 res 文件夹下是没有层级概念的

* 通过前缀的命名可以帮助我们更好定位到同一模块下的资源

* 例如分享对话框中，有对话框 Root 布局和 Item 布局

```text
share_dialog.xml（Root 布局）

share_item.xml（Item 布局）
```

#### 资源文件命名规范

* 如果是业务模块下的资源，以 **模块 + 类型** 来命名，例如分享对话框的资源：

```text
share_link_ic.png（复制链接）

share_moment_ic.png（分享到朋友圈）

share_qq_ic.png（分享到 QQ 好友）

share_qzone_ic.png（分享到 QQ 空间）

share_wechat_ic.png（分享到微信好友）
```

* 如果和业务模块不相干的资源，以 **作用 + 类型** 来命名，例如通用的控件样式资源：

```text
button_rect_selector.xml（通用直角按钮样式）

button_round_selector.xml（通用圆角按钮样式）
```

* 这种资源有一个共同特点，它不属于哪个模块，但是在不同模块都有用到，所以不能用业务的模块名作为文件名前缀，最后附上常见类型名称对应表：

|   名称  |  类型 |
| :-----: | :----: |
|  ic |  图标 |
|  bg |  背景 |
|  selector |  选择器 |

#### String ID 命名规范

* 请以 **模块 + 功能** 来命名，例如：

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
<string name="setting_language_switchover">语言切换</string>
<string name="setting_language_simple">简体中文</string>
<string name="setting_language_complex">繁体中文</string>
```

* 另外有一类 String 被多个模块所引用，需要以 **common + 作用** 来命名，例如：

```xml
<string name="common_loading">加载中&#8230;</string>

<string name="common_confirm">确定</string>
<string name="common_cancel">取消</string>

<string name="common_year">年</string>
<string name="common_month">月</string>
<string name="common_day">日</string>

<string name="common_hour">时</string>
<string name="common_minute">分</string>
<string name="common_second">秒</string>
```

#### Color ID 命名规范

* 请以 **模块 + 作用 + color** 来命名，例如：

```xml
<color name="logcat_level_verbose_color">#FFBBBBBB</color>
<color name="logcat_level_debug_color">#FF33B5E5</color>
<color name="logcat_level_info_color">#FF99CC00</color>
<color name="logcat_level_warn_color">#FFFFBB33</color>
<color name="logcat_level_error_color">#FFFF4444</color>
<color name="logcat_level_other_color">#FFFFFFFF</color>
```

* 另外有一类 Color 被多个模块所引用，需要以 **common + 作用 + color** 来命名，例如：

```xml
<!-- App 样式中引用的颜色 -->
<color name="common_primary_color">@color/white</color>
<color name="common_primary_dark_color">@color/black</color>
<color name="common_accent_color">#5A8DDF</color>
<color name="common_window_background_color">#F4F4F4</color>
<color name="common_text_color">#333333</color>
<color name="common_text_hint_color">@color/panda</color>

<!-- 按钮按压时的颜色 -->
<color name="common_button_pressed_color">#AA5A8DDF</color>
<!-- 按钮禁用时的颜色 -->
<color name="common_button_disable_color">#BBBBBB</color>
<!-- 分割线的颜色 -->
<color name="common_line_color">#ECECEC</color>
```

* 还有一类 Color 是行业通用的色值，需要以 **简单直接的方式** 来命名，例如：

```xml
<!-- 透明色 -->
<color name="transparent">#00000000</color>
<!-- 白色 -->
<color name="white">#FFFFFFFF</color>
<!-- 黑色 -->
<color name="black">#FF000000</color>
<!-- 灰色 -->
<color name="gray">#FF808080</color>
<!-- 红色 -->
<color name="red">#FFFF0000</color>
<!-- 金色 -->
<color name="gold">#FFFFD700</color>
<!-- 黄色 -->
<color name="yellow">#FFFFFF00</color>
<!-- 绿色 -->
<color name="green">#FF008000</color>
<!-- 蓝色 -->
<color name="blue">#FF0000FF</color>
<!-- 紫色 -->
<color name="purple">#FF800080</color>
<!-- 粉色 -->
<color name="pink">#FFFFC0CB</color>
<!-- 橙色 -->
<color name="orange">#FFFFA500</color>
```

* 在实际开发中，我们常常会遇到类似下面这种命名方式：

```xml
<name="color_FF35BF30">#FF35BF30</color>
```

* 其实这种命名方式是不规范的，因为它对 **Color ID** 的名称定义比较模糊，会容易给别人造成误导；举个例子：假设项目中有 **200** 个地方引用了这个 `color_FF35BF30` 色值，其中有 **150** 地方是你自己引用的，另外 **50** 个地方是别人引用的，但是别人不知道你那个色值是干什么的，看到你有写就直接引用了，突然有一天产品经理心情不好要改这个色值，那么你要从 **200** 地方区分 **150** 个需要修改的地方和 **50** 个不需要修改的地方。

#### Anim ID 命名规范

* 应用到某个模块 **View**，例如：

```text
login_left_balloon_view.xml
login_right_balloon_view.xml
```

* 应用到全局 **Activity**，例如：

```text
left_in_activity.xml
left_out_activity.xml
```

* 应用到全局 **Dialog**，例如：

```text
bottom_in_dialog.xml
bottom_out_dialog.xml
```

#### View ID 命名规范

* 应该以 **控件的缩写 + 模块名 + 作用** 来命名，例如

```text
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

#### Style 命名规范

* 如果只是主题相关的样式，以 **Theme** 命名结尾，控件样式则以 **Style** 命名结尾，命名要求尽量简洁，并且需要有代码注释，示例如下：

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

#### XML 编码规范

* 不推荐用 **dp** 作为字体单位，虽然在大部分手机上面 **dp** 和 **sp** 计算是差不多的，但是会有一部分老年用户群，例如咱们的长辈，他们通常会把手机显示的字体大小调大，这样他们才不需要带眼镜看手机，如果我们用 **dp** 作为字体单位，无论手机怎么调整字体大小，应用的字体大小都不会有任何的变化，所以这种操作显然是非常不人性化的。

```xml
<!-- 不规范写法示例 -->
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:textSize="18dp" />
```

```xml
<!-- 规范写法示例 -->
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:textSize="18sp" />
```

* 不能根据设计图给定的宽高把 **TextView** 或者 **Button** 的宽高定死，而是通过 `wrap_content` 和 `padding` 的方式来调整 View 的宽高，因为在不同手机上面字体大小不一致，在字体显示比较小的手机上面会显示正常，但是在字体显示比较大的平板上面文字上半部分极有可能会出现被裁剪的情况，所以我们不能把宽高定死，而是通过 `padding` 来调整到控件的大小。不过需要注意的是，[TextView 有自带的文字间距](https://blog.csdn.net/ccpat/article/details/45226951)，我们在拿设计图给定的 `padding`值时，需要拿设计图给定的值适当减去这一部分值（一般大概是在 **2~3dp**）。

```xml
<!-- 不规范写法示例 -->
<Button
    android:layout_width="180dp"
    android:layout_height="60dp" />
```

```xml
<!-- 规范写法示例 -->
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:paddingStart="80dp"
    android:paddingTop="20dp"
    android:paddingEnd="80dp"
    android:paddingBottom="20dp" />
```

* **ImageView** 的宽高任一项定义成 `match_parent` 时，另外一项不能写死大小，而是应该使用 `wrap_content`，否则很可能会因为比例不对导致图片变形，另外还需要使用 `android:adjustViewBounds="true"` 属性，否则 `ImageView` 无法根据图片的宽高来调整自己的宽高。

```xml
<!-- 不规范写法示例 -->
<ImageView
    android:layout_width="match_parent"
    android:layout_height="300dp"
    android:src="@drawable/example_bg" />
```

```xml
<!-- 规范写法示例 -->
<ImageView
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:adjustViewBounds="true"
    android:src="@drawable/example_bg" />
```

* XML 节点编写应该规范，在没有子节点的情况下，应当以 `/>` 节点结尾，如果有则以 `</xxx.xxx.xxx>` 节点结尾

```xml
<!-- 不规范写法示例 -->
<androidx.recyclerview.widget.RecyclerView
    android:layout_width="match_parent"
    android:layout_height="match_parent">
</androidx.recyclerview.widget.RecyclerView>

<!-- 不规范写法示例 -->
<TextView
    android:layout_width="match_parent"
    android:layout_height="match_parent">
</TextView>
```

```xml
<!-- 规范写法示例 -->
<androidx.recyclerview.widget.RecyclerView
    android:layout_width="match_parent"
    android:layout_height="match_parent" />

<!-- 规范写法示例 -->
<TextView
    android:layout_width="match_parent"
    android:layout_height="match_parent" />
```

#### 预览属性约定

* 应该在布局文件根布局中定义 `tools:context` 属性，以便在布局文件中快速定位到对应的类

```xml
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".ui.activity.HomeActivity">

</FrameLayout>
```


```text
tools:context=".ui.activity.HomeActivity"

tools:context=".ui.fragment.SettingFragment"

tools:context=".ui.adapter.HomeAdapter"

tools:context=".ui.dialog.PersonDataDialog"
```

* 此外，tools 属性还有各种各样的用途，例如 **RecyclerView** 的 **tools** 属性

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

* 这种命名方式不止可以应用于 **RecyclerView**，还可以应用于其他 **View** 的属性，比如常用的 **TextView** 和 **ImageView**

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

* 如果某个 **TextView** 显示的字符串是一成不变的，那么可以直接定义在布局文件中，如果是动态变化的，那么应该使用 `tools:text` 预览属性，而不应该使用 `android:text`，其他布局属性也同理。
	
#### 资源硬编码规范

* String 硬编码规范：如果项目已经适配了多语种，则严禁写死在 Java 代码或者布局文件中，如果没有这块需求的话，也建议将 String 资源定义在 `string.xml` 文件，此项不强制要求，大家根据实际情况而定。

* Color 硬编码规范：在没有使用夜间模式的情况下，允许大部分 Color 值直接定义在布局文件中，但是如果某个色值引用得比较多（例如主题强调色、默认背景色等），需要抽取到 `color.xml` 文件中。

* Dimens 硬编码规范：允许写死在 Java 代码或者布局文件中，但是如果使用了[通配符方案](https://github.com/wildma/ScreenAdaptation)对屏幕进行适配，那么则不能直接写死。

* Style 样式规范：对于一些常用并且样式比较统一的控件，例如 **Button**、**EditText** 等，我们对这些控件的样式进行抽取到 `style.xml` 文件中来，避免属性重复定义。

#### 版本命名规范

* 版本名应该由三段整数组成

    * 第一段：代表大版本号，如果出现 UI 大改版，或者项目出现大重构时 +1

    * 第二段：代表需求版本号，一般双周发一次版，每个迭代周期 +1
    
    * 第三段：代表 Bug 版本号，发版之后出现 Bug，需要发版修复时 +1

```groovy
versionName '4.8.0'
```

* 另外版本码应当和版本名保持一定的关联性，例如：

```groovy
versionName '4.12.1'
versionCode 41201
```

* 这样的好处在于：版本名越高，版本码也会变大，不仅能方便记忆，还能帮助我们更好地管理和升级版本，在一定程度上能避免**高版本名低版本码**的 apk 能被**低版本名高版本码**的 apk 覆盖安装的情况。

#### 致谢

* [阿里巴巴Android开发手册.pdf](阿里巴巴Android开发手册.pdf)

* [阿里巴巴Java开发手册.pdf](阿里巴巴Java开发手册.pdf)

* [谷歌代码样式指南](http://source.android.com/source/code-style.html)

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

#### 微信公众号：Android轮子哥

![](https://raw.githubusercontent.com/getActivity/Donate/master/picture/official_ccount.png)

#### Android 技术分享 QQ 群：78797078

#### 如果您觉得我的开源库帮你节省了大量的开发时间，请扫描下方的二维码随意打赏，要是能打赏个 10.24 :monkey_face:就太:thumbsup:了。您的支持将鼓励我继续创作:octocat:

![](https://raw.githubusercontent.com/getActivity/Donate/master/picture/pay_ali.png) ![](https://raw.githubusercontent.com/getActivity/Donate/master/picture/pay_wechat.png)

#### [点击查看捐赠列表](https://github.com/getActivity/Donate)

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