# UGUI Inspector Component

### Canvas (画布)  
一切UI元素都必须是Canvas的子对象.注意,在Hierarchy界面中创建的Canvas,它的rectTransform属性是交由系统自动控制的.
* renderMode [枚举]  
  画布是在世界中还是重叠模式?
  * *Screen Space-Overlay* (屏幕控件-覆盖模式): 2D|UI,始终显示在屏幕最前方.画布的画面永远“覆盖”其他普通的3D画面，如果屏幕尺寸被改变，画布将自动改变尺寸来匹配屏幕
  * *Screen Space-Camera*(屏幕控件-摄影机模式): 2D及3D|UI,绑定到指定摄像机,可显示3D内容,同时UI可以进行3D方面的旋转,UI可以获得3D效果.在该模式下，画布会被放置到摄影机前方。在这种渲染模式下，画布看起来 绘制在一个与摄影机固定距离的平面上。所有的UI元素都由该摄影机渲染，因此摄影机的设置会影响到UI画面
  * *World Space*：3D|UI,存在于3D空间中的UI 在此模式下,画布被视为与场景中其他普通游戏对象性质相同的类似于一张面片(Plane)的游戏物体.此时,画布已经不对应屏幕了...厉害.画布的尺寸可以通过RectTransform设置,所有的UI元素可能位于普通3D物体的前面或者后面显示.当UI为场景的一部分时可以使用这个模式(**跟随人物的血条或名称**)
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
  * *Constant Pixel Size*(PC): 像素大小始终不变.即一个100*100的图片在任何的分辨率下都占用100*100的像素.一般PC上会使用这种方式,因为PC端分辨率差异并不大
  * *Scale with Screen Size*(移动): 不关心图片的实际像素大小,而只关心Width及Height值,这个值如果是1000,那么100高度的图片在任何分辨率下都只占用屏幕1/10的尺寸.一般移动端会使用这种方式因为,移动端分辨率差异较大.
  * *Constant Physical Size*: 根据物理单位进行缩放
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





  ---
