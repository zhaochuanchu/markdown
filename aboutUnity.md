# 关于unity
---
## 快捷键    
* ctrl+s 保存法
* F2 重命名
* F11 全屏
* ctrl+鼠标滑轮 放大和缩小界面
* ctrl+l 选中当前行 重复可以继续选择下一行
* ctrl+x 剪切当前行
* ctrl+enter 在下一行添加新行
* ctrl+shift+enter 在上一行添加新行
* ctrl+p 播放
* ctrl+shift+p 暂停
* ctrl+shift+f 输入法简繁切换
* shift 输入法直接实现中英文切换 不要再切换输入法了
* ctrl+d 在选中Gameobject后直接复制
* ctrl+z 撤销
* ctrl+y/ctrl+shift+z 恢复撤销
* ctrl+shift+p 打开命令行
* shift+方向键 逐个选中字母
* ctrl+方向键 逐个跳过单词
* alt+方向键 逐个识别词中的跳过英文单词
* ctrl/alt+shift+方向键 逐个跳过并选中
* shift 可以一下选很多行
* 技巧之间相互配合
* vs2015 F5调试 ctrl+F5运行
* shift 输入法切换中英文
* shift+space 输入法切换圆角半角
* ctrl+. 输入法切换中英文标点(在VS中隐藏智能提示)
* VS2015 ctrl+k+c注释多行 ctrl+k+u取消注释多行
* 在类或方法前面/// 自动生成summary(很爽)
* 按住shift 在拖动UI物体,可以实现直左直右(直上直下)
* ctrl+tab 切换文件/选项卡

---
## 一些常见的翻译
`script脚本` `manual手册` `canvas画布` `invoke调用` `inverse反向` `velocity速率` `sorting layer渲染层级` `GC 垃圾回收(器)` `IL托管代码`  `CLR Common Language Runtime公共语言运行时` `native本地的原生的` `cache缓存` `Garbage Collecter(GC)垃圾回收器` `field字段` `airty元数(参数个数)` `Framework Class Library(FCL)` `current当前的`
`SQLServer[sikəu 'sə:və]` `ADO.Net(a do 直接这样读)` `cast 投射` `shadow 阴影` `Texture 纹理`
***
## 关于unity的视角调节
* 多多F12查看C#源码,还是中文的注释贼爽
* 按住右键拖动以自己为中心环视
* alt+左键拖动以聚焦Object为中心环视
* alt+右键拖动和鼠标滑轮 放近放远
* 按住滑轮拖动可以平移视野 方便观察
* 选中T工具(操作UI界面大小)的时候,先点边角,按住alt键拖动时会以中心对称拖动,同样的,先点边角,按住shift键拖动,图片(或GameObject会) **等比** 放大或缩小. 也可以同时按住shift和alt,以中心点等比例放大
* Text组件添加shadow 加黑色阴影,添加outline,给字体添加外边框增加清晰度
> 在这里写一下提示性内容吧

***
## 关于unity3D界面的操作技巧
* 在Hierarchy窗口中把一个Gameobject拖入另一个Gameobject里 则此Gameobject坐标会以后者为原点 即后者移动得话前者也会在世界视图中跟着移动
* scene窗口上的五个小功能切换 用来调节视角 位置 旋转 大小 快捷键分别是qwer(鼠标在scene视图中使用快捷键) t主要用于2维设计
* 材质（material）可以直接拖到scene窗口 也可以拖到对应的Hierarchy窗口 使GameObject使用相应的材质
* scene上面的Global表示世界坐标 local表示自身坐标
* script-脚本 c#脚本实质相当于自定义组件 可以直接将脚本文件拖入inspector窗口 该窗口包含Gaeobject的众多组件(compenent) 实现脚本与Gameobject的绑定 **或者直接在inspector窗口中add component 随便输入一个名字 选择new script 选择language包括c sharp和JavaScript**
* 可以利用console窗口输出自己想看到的东西
* 同一类物体(操作相同的)利用tag标签属性 统一进行判断碰撞和碰撞后处理
* 碰撞检测三种1.碰撞器 2.触发器(is Trigger) 触发器碰撞器均为同一个组件sphere collider(碰撞机)
* 在组件界面左上角有一个勾选框 打钩代表激活此gameObject 不打钩代表不激活
* 发布游戏 将场景拖入file-build settings界面 发布场景的时候默认进入拖动列表的第一个场景
* 开发时可以取消lighting的自动渲染 提高开发效率 只需要发布的时候build渲染一下即可
* ambient source环境源 可以用天空盒(skybox)渲染,也可以指定颜色渲染.
* camera属性中的projection perspective远景(默认的) 和Orthographic正交视野
* rigidbody组件中的constraints可以锁定位移和旋转 对于刚体的运动有重要意义
* 动画效果的Duration属性代表动画的持续时间
* **这个技巧不错 在命名脚本的时候 unity3d会自动把大写字母的两个单词分开提高阅读性**
* 将一个小数强制转换成float可以直接在后面加f如 0.58f *这个以前比较忽略*
* 依附在组件上的声音 如果Gameobject被销毁 声音也会跟着消失 所以在播放类似"爆炸""破坏"等音效时候(需要销毁Gameobject的场合)不能使用组件的形式播放音效
* 优化:对于Unity3D自带的SendMessage来说，它的最大的诟病，是它的效率问题。对于这一问题，可以用Delegate取而代之，据网上说，Delegate的效率10倍与SendMessage。
但是并不是说不能使用SendMessage，毕竟他底层封装了反射机制，使用十分方便，只是不可频繁使用。
* >对于优化的一个不错的想法 有人希望借助优化脚本来提高性能所以不想继承monoBehaviour:
但是如果你要用Unity，就该放手写脚本（当然蹩脚程序一个obj挂几十个compent的当我没说过），千万不要患上性能强迫症去花大把时间构造性能强大结构复杂的脚本。
通常，一个游戏（Unity开发桌面程序或者动画同理）流畅与否取决于画面渲染，而不是脚本。脚本制作只要记住一点，只优化大量循环的代码就行了。经典的代码例如角色控制器，AI等。
其他代码尽可能简洁。非游戏开发一般是不需要考虑这么多的，测试的时候注意有没有特别卡的地方就好了。如果客户特别强调性能的话就要多花功夫了。
继承MonoBehaviour是有很多好处的，调试方便，思维顺畅，这些都是可以大大加快开发进程的，与追求性能相比，追求开发速度意义远大于性能。
* 也有人说需要引擎来管理你的脚本就继承，不需要就不继承，差不多就这样
* >c#和java命名有所不同
不同语言有不同的习惯，简答的说：
Java的变量名、属性名、方法名，C#的变量名，这些标识符遵循“骆驼命名法”，标识符首字母小写，组成标识符的每个单词首字母大写。
Java的类名，C#的属性名、方法名、类名，这些标识符遵循“帕斯卡命名法”，标识符首字母大写，组成表字符的美国单词首字母大写。
这两种命名法的规定其实相当详细复杂，我说的只是简单的规则，仅供参考。

* unity中三种调用其它脚本函数的方法
>* 第一种，被调用脚本函数为static类型，调用时直接用  脚本名.函数名()。很不实用……
>* 第二种，GameObject.Find("脚本所在物体名").SendMessage("函数名");  此种方法可以调用public和private类型函数
>* 第三种，GameObject.Find("脚本所在物体名").GetComponent<脚本名>().函数名();此种方法只可以调用public类型函数

* unity要注意状态数据和配置数据的分离
* unity3d的inspector界面是可以锁定的！ 在拖动资源的时候锁定inspector界面显得格外方便！
* unity中三种获取GameObject的方法
>* 在message中通过传进来的参数(component)的GameObject获取 这种获取方法必须触发事件 且该事件和该GameObject是绑定的
>* 直接在脚本中声明public GameObject在inspector界面中拖入该Object以直接获取对该GameObject的引用
>* 通过标签获取GameObject
>* 通过GameObject.find(String name)方法获取GameObject，如 **GameObject.Find("Score").GetComponent<Text>()** 或者 **GameObject.Find("Canvas/Score").GetComponent<Text>()**

* *组件或者游戏物体的激活装填只影响unity提供的事件调用，自定义的方法并不受影响*

* 命名空间下可以有子命名空间 引入一个命名空间不能使用子命名空间下的类和方法 详见图片:`命名空间的疑惑`
* onMouse系列事件需要被检测的物体有碰撞器

* 如果你没有时间的话，那么学新技术不如学基础、学应用不如学思想。技术虽然一直在变，但是越是基础和越是抽象的技术变化越慢，越是偏向应用越是具体的技术变化越是快，从性价比上说，学习基础知识性价比更高


* 仿佛突然懂得属性和字段的区别 属性
      public Component rigidbody { get; }
      public Transform transform { get; }

* 选择UGUI吧
* IL是.NET框架中中间语言（Intermediate Language）的缩写
* VS2015即时窗口很有用,输入属性或者字段可以直接查看其值

* 挂载在游戏物体上的脚本必须显式继承MonoBehaviour
* 在canvas(画布上),使用的是UGUI系统,只能添加UI元素,不能加入2DObject 3DObject,因为它们不是一个次元的,也许 不应当利用事件系统来做UI的事件处理,而且貌似也没法处理
* 踩到一个坑,**挂载在物体上的组件(包括脚本)可以理解成一个实例**,所以不要定义静态方法,这么jb坑? 无法调用静态方法?静态成员不属于实例对象，所以没法通过GC自动回收，会一直占据内存.你看到的所有Unity组件都是一个个实例，你要通过Unity的编辑器去配置.实际上到这里已经可以基本总结出何时需要使用单例了：只要你的类需要保存其他组件作为变量，那么就有必要使用单例；只要你有在Unity编辑器上进行参数配置的需求，那么就有必要使用单例；只要你的管理器需要进行加载的顺序控制，那么就有必要使用单例（比如热更新后加载ResourcesManager）；
* 继承自MonoBehaviour单例模式很简单,只需要在Awake（）里面，添加一句instance = this;其中instance是静态私有成员.如果是普通类的单例,就麻烦一些.
* 在unity游戏开发中,尽量 **避免使用静态变量或方法**. 大部分操作的对象都是实例.
* Unity3D挂载在GameObject上的脚本(即继承自MononBehaviour的类型)一定要 **避免使用构造函数**.GameObject会在编辑器的多个地方被显示，如场景编辑器内、Prefab选中时等，这些时候都需要调用它们的构造函数来初始化成员变量的默认值，以便在编辑器中显示它们。也就是说，构造函数不光在游戏运行时会被调用，它的调用时机是“未知的”。而Awake和Start只会在游戏运行时被调用，并严格定义了它们的调用时机和顺序。所以，构造函数不可以描述游戏逻辑，请用Awake和Start.很正确,完美解释了试验结果. 所以像readonly字段之类只能在构造阶段初始化的成员，尽量不要用.由于内联初始化时在构造函数中进行的,所以也无法使用 **内联初始化** .
* UGUI中的控件在Inspector中显示的绑定方法的那个东西,本质是个 **事件**,不知道可不可以自己定义的事件能否显示,能显示那就爽了
* UI图片资源需要在Inspector界面将Texture属性设置为Sprites(2D and UI)
*  [SerializeField]特性可以使私有字段序列化,并使其在Inspector面板中显示,目前找到的一种不错的设计模式
* UI元素要记得设置anchor
* Image的属性:
  * simple属性,正常
  * sliced属性,需要配合九宫切图,使sprite在拉伸时只有中间一宫放大,边框不放大,防止放大时图片失真.
  * tiled属性,不能有切图,是平铺,放大后会按照图片原来的大小,平铺整个空间.
  * filled属性,用来显示图片中的某一部分.
* UGUI中 Image"游戏物体"中的Image组件实际是它本身this.
* double result=s.ToString("#0.00");//点后面几个0就保留几位
* 界面处理和数据处理分离 button被按下后,分别向UI类和数据类发送通知.可以在同一个GameObject下挂两个脚本,一个处理数据,一个处理UI.在数据和UI耦合较大时这么处理.(也许UI界面不用这么做吧)
* Update Awake等消息方法 我个人认为 最好加上protected virtual修饰符,一是方便子类调用父类,二是方便子类重写
* 如果两个GameObject的显示优先级那个属性一样,那么在Hierarchy界面下方的GameObject会覆盖上方的GameObject,可以通过拖动来调整显示.
* 数据类变量必须隐藏(封装到属性中,对外只读),至于UI类变量,感觉可以public暴露到外面,视情况而定.
* 重写父类的方法无法修改父类的访问修饰符
* 如果不想希望让某个类实例化 可以有两种做法
  * 1.将这个类定义为抽象类... 有点不好
  * 2.偶然想到的这个方法,将构造器的访问修饰符设为 **protected** (不能是private,否则子类都无法调用此构造器,是绝对不行的),这样外界无法通过new构造这个类型的实例,然后将派生程度比较大的(你想使其能实例化的)构造器设为public.
* UI类 和数据类 分开, 然后UI类中有一个变量是数据类.
* Manager类全都挂在主角身上?
* 构造器中如果有私有字段和公有属性,一定要初始化该字段的属性
* 使用 **文档注释**  
文档注释，用于对类和方法进行注释，在类或方法前面，连续输入3个/,系统会自动补全注释。
    /// <summary>  
    /// 将物品附在格子上  
    /// </summary>  
    /// <param name="thing">物品</param>   
    /// <param name="gridItem">格子</param>
* setTrigger或者设置Animation的变量之后 在当前帧playerAnimator.GetCurrentAnimatorStateInfo(0).IsName("Jump") 还是false的 需要等到下一帧才生效
* 所谓事件的穿透,比如最顶层接受click事件,那么被其遮住的UI的click事件无法触发,如果顶层不接受click事件,那么被其遮住的UI就可以相应Click事件
* Ondrop比OnEndDrop执行得早 end最后执行
* 好程序员做一切能提高效率的事情.  
* setParent的第二个参数设置为true,其世界坐标不会改变
* 用unity做游戏实质上就是用轮子组系统的过程，无论抵制轮子还是造轮子，支持插件还是反对插件，都不重要。重要的是整体的框架是否健壮合理，中间的焊缝是否严实
