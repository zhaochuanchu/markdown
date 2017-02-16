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
* ctrl+. 输入法切换中英文标点
* VS2015 ctrl+k+c注释多行 ctrl+k+u取消注释多行
---
## 一些常见的翻译
`script脚本` `manual手册` `canvas画布` `invoke调用` `inverse反向` `velocity速率` `sorting layer渲染层级` `GC 垃圾回收(器)` `IL托管代码`  `CLR Common Language Runtime公共语言运行时` `native本地的原生的` `cache缓存` `Garbage Collecter(GC)垃圾回收器` `field字段`
***
## 关于unity的视角调节
* 多多F12查看C#源码,还是中文的注释贼爽
* 按住右键拖动以自己为中心环视
* alt+左键拖动以聚焦Object为中心环视
* alt+右键拖动和鼠标滑轮 放近放远
* 按住滑轮拖动可以平移视野 方便观察
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
