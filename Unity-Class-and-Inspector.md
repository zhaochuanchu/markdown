# UGUI Inspector Component

### Canvas   
一切UI元素都必须是Canvas的子对象.注意,在Hierarchy界面中创建的Canvas,它的rectTransform属性是交由系统自动控制的.
* renderMode [枚举]  
  画布是在世界中还是重叠模式?
  * *Screen Space-Overlay* (屏幕控件-覆盖模式)  
  2D|UI,始终显示在屏幕最前方.画布的画面永远“覆盖”其他普通的3D画面，如果屏幕尺寸被改变，画布将自动改变尺寸来匹配屏幕
  * *Screen Space-Camera*(屏幕控件-摄影机模式)  
  2D及3D|UI,绑定到指定摄像机,可显示3D内容,同时UI可以进行3D方面的旋转,UI可以获得3D效果.在该模式下，画布会被放置到摄影机前方。在这种渲染模式下，画布看起来 绘制在一个与摄影机固定距离的平面上。所有的UI元素都由该摄影机渲染，因此摄影机的设置会影响到UI画面
  * *World Space*  
  3D|UI,存在于3D空间中的UI 在此模式下,画布被视为与场景中其他普通游戏对象性质相同的类似于一张面片(Plane)的游戏物体.此时,画布已经不对应屏幕了...厉害.画布的尺寸可以通过RectTransform设置,所有的UI元素可能位于普通3D物体的前面或者后面显示.当UI为场景的一部分时可以使用这个模式(**跟随人物的血条或名称**)
* Pixel perfect [bool]  
  (只在支持2DUI的前两种模式下可用).是否以像素的形式来显示UI.UI呈现无抗锯齿的精度?文档中说,强制画布中的元素与像素对齐.使边缘清晰不模糊
* Sort Order [int]  
  不同Canvas的渲染顺序
* Target display  
  未知,感觉是个鸡肋
* Render Camera [Camera]  
  (只在Screen Space-Camera模式下可用),设定渲染摄像机
* Plane Distance [int]  
  (只在Screen Space-Camera模式下可用),指定摄像机与Canvas的距离
* Sorting Layer [枚举]  
  (只在支持3DUI的后两种模式下可用),指定3D渲染顺序
* Event Camera [Camera]  
  (只支持在World-Camera模式下可用),用来指定接受事件的摄像机.可以通过画布上的GraphicRaycaster组件发射射线产生事件.

### Canvas Scaler  
Canvas的比例调节  
Unity在移动设备上的自适应依靠的是组件本身的Anchors(锚点)和Canvas上的CanvasScaler.
* UI Scale Mode [枚举]:  
UI缩放模式
  * *Constant Pixel Size*(PC)  
  像素大小始终不变.即一个100*100的图片在任何的分辨率下都占用100*100的像素.一般PC上会使用这种方式,因为PC端分辨率差异并不大
  * *Scale with Screen Size*(移动)  
  不关心图片的实际像素大小,而只关心Width及Height值,这个值如果是1000,那么100高度的图片在任何分辨率下都只占用屏幕1/10的尺寸.一般移动端会使用这种方式因为,移动端分辨率差异较大.
  * *Constant Physical Size*  
  根据物理单位进行缩放
* Scale factor [int]  
比例因子,UI会根据该因子进行放大或缩小
* Reference Pixels Per Unit [int]  
未知,应该是鸡肋
* Reference Resolution(参考分辨率)  
(只在Scale with Screen Size模式下可用) 该尺寸是你拼UI时的尺寸.然后Unity根据实际在移动设备上的尺寸来决定是帮你拉大还是缩小
  * X [int]:长
  * Y [int]:宽
* Screen Match Mode [枚举]  
(只在Scale with Screen Size模式下可用),屏幕匹配模式
  * *Match Width or Height* (推荐使用这种模式)
  * *Expend* (延伸)
  * *Shrink*
* Match [0-1]  
(只在Scale with Screen Size模式下可用)竖版匹配Width,横版匹配Height

### Graphic Raycaster  
通过射线检测解决鼠标穿透UI的问题?

### Rect Transform  
继承自Transform,UI物体会自带该组件.
* (RectPosition)(位置信息)  
当四个锚点不重合时,下面四个属性会变,变成显示另外四个截然不同的属性
  * Pos X(Left)
  * Pos Y(Top)
  * Width(Right)
  * Height(Bottom)
  * Pos Z  
  Z轴坐标 默认是0
* Ancohors(锚点)  
下面X,Y互相组合的四个点,构成锚点.同时也代表四条锚线,围成一个锚框.(Minx,Miny),(Maxx,Maxy)分别是左下角和右上角的两个锚点.子物体的rect四个顶点分别与这四个锚点保持距离不变.
  * Min X
  * Min Y
  * Max X
  * Max Y
* Pivot(中心点)  
UI元素的旋转和缩放是围绕pivot进行的.RectTransform组件中,Pivot属性是一个正规化的二维向量,用来描述中心点在本身矩形大小的位置.默认值为(0.5, 0.5).即几何中心.  
  * X [0-1]  
  中心点的横轴位置
  * Y [0-1]  
  中心点的纵轴位置
* Roation(旋转角)  
表示该UI的旋转角度
  * X
  * Y
  * Z
* Scale(缩放比例)  
表示该UI的放大缩小比例
  * X
  * Y
  * Z

### Text  
* Text [string]  
Text组件上显示的内容
* Font  
选择显示文本的字体
* Font Style [枚举]  
文本显示的风格
  * Normal  
  正常
  * Bold  
  粗体
  * Italic  
  斜体
  * Bold And Italic  
  粗体加斜体
* Font Size [int]  
文本中文字的大小
* Line Spacing [int]  
行间距 (Text组件公开字间距属性,但是可以通过脚本控制这一属性)
* Rich Text [bool]  
富文本开关(Use Emotions and Colors) 支持更多的组合语法(Html的标签风格) 而且标签可以互相嵌套 如下例:  
`<b>text</b>:加粗`  
`<i>text</i>:斜体`  
`<size=5>text</size>:设置字体大小`  
`<color=green>text</color>:设置字体颜色`  
`<color=#00ff00ff>text</color>:自定义字体颜色`
* Alignment  
设置上下和左右对齐方式
* Align By Geomtry [bool]  
使用区段的字形几何执行水平对齐,而不是字形指标。
这可以导致更好的拟合左和右对齐,但可能会导致不正确的定位当试图覆盖多个字体(如专业轮廓字体)上。貌似是鸡肋
* Horizontal Overflow [枚举]  
控制文本水平溢出
  * Wrap  
  当文本达到水平边界,将会自动换行
  * OverFlow   
  文本可以超出水平边界继续显示
* Vertical Overflow [枚举]  
控制文本垂直溢出
  * Truncate  
   文本不显示超出垂直边界的部分
  * OverFlow  
  文本可以超出垂直边界继续显示
* Best Fit [bool]  
勾选之后,编辑器发生变化,显示Min Size和Max Size.即文本的大小将要由Text的组件的边界决定.最小可以显示到Min Size.最大可以显示到Max Size
  * Min Size [int]
  * Max Size [int]
  * 当边框很大时，文字最大显示Max Size字体大小；当边框很小时，文字最小显示Min Size字体大小，边框显示不了MinSize字体大小就不再显示文字了
* Colors  
字体的颜色
* Material  
字体的材质
* Raycast Target[bool]  
射线对象,为true时,可以接受射线(相应事件?),为flase时,消息会透传

### Button
* Interactable [bool]  
是否支持交互(触摸,鼠标,键盘).当为flase时,按钮会变暗
* Transition [枚举]  
Button转变(过渡)状态的三种模式
  * None  
   状态变化时没有任何显示
  * Color Tint   
  通过颜色的切换来区别Button的不同状态
    * Target Graphics [Image]  
    目标图像,就是Button的图片
    * Normal Color [Color]   
    正常状态下的颜色
    * Highlight Color [Color]  
    高亮状态下的颜色,表示Button被选中,或鼠标移到Button内的时候显示
    * Press Color [Color]  
    被点击状态下的颜色.
    * Disabled Color [Color]  
    Button不可用时的颜色.(Interactable为false时)
    * Color Multiple [int]  
    对不同状态颜色的显示系数
    * Fade Duration [int]  
    颜色渐变持续时间 默认0.1s
  * Sprite Swap  
  通过图片的切换来区别Button的不同状态
    * Target Graphics [Image]  
    目标图像,就是Button的图片
    * Highlight Sprite  
    高亮状态下的图片
    * Press Sprite  
    被点击状态下的图片
    * Disabled Sprite  
    不可用状态下的图片.(Interactable为false时)
  * Animation  
  通过动画的切换来区别Button的不同状态,有点高级.先不使用.每个状态对应的动画名需要与动画状态机中的状态名保持一致.通过Animation动画窗口可以设定每个动画状态的动画剪辑.
* Navigation [枚举]  
通过非鼠标点击的方式(键盘,手柄)切换button的焦点.使被选中的Button(高亮状态)切换到下一个Button,可以点击Visualize,可以在Scene界面看到Button的互相切换连接线  
  * None  
  该Button不参与切换
  * Vertical  
  垂直切换
  * Horizontal  
  水平切换
  * Automatic  
  自动切换
  * Explicit  
  显性指定上下左右切换到哪个按钮
* On Click() [事件]  
可以为该Button绑定多个方法,点击该Button时会调用这些方法.

### Image
* Source Image [Sprite]  
图片源,这要求图片(.jpg)等导入之后,把图片的Texture Type属性设置为Sprite(2D and UI)再使用.
* Color [Color]  
图片的渲染颜色
* Material  
图片的材质
* Raycast Target [bool]  
射线对象,为true时,可以接受射线(响应事件?),为flase时,消息会透传
* Image Type [枚举]  图片类型
 * Simple  
  没有任何特殊效果
    * Preserve Aspect [bool]  
    默认是false.如果勾选该选项.图像的高度和宽度会保持原比例.
  * Sliced  
  改变Image大小时,border(可使用Sprite Editor编辑九宫切图)内的会正常放大缩小,而border的边角只会延伸,不会放大.
    * Fill Center [bool]  
    中心图片是否填补 默认是true
  * Tiled  
  改变Image大小时,会按原大小自动扩展很多个图片平铺整个Image.
  * Filled  
    * Fill Method [枚举]  
    填充方式
      * Horizontal   
      水平填充
      * Vertical  
      垂直填充
      * Radial 90  
      辐射旋转90度
      * Radial 180  
      辐射旋转180度
      * Radial 360 (默认)    
      辐射旋转360度
    * Fill Origin [枚举]   
    填充起点 (Top,Bottom,Left,Right)
    * Fill Amount [int]  
    当前填充的程度(0~1)
    * Clockwise [bool]  
    是否按照顺时针方向 默认true

### Mask


  ---
