## Model面板
#### Meshes  
Mesh(网格)的相关设置
* Scale Factor:  
模型缩放.默认数值为1,可以在这里调整数值,而不必拖入场景之后再设置transform的scale属性了.
* Mesh Compression:  
网格压缩.用来降低模型的面数.一般这个选项是false,尽量让美工在Maya或3DMax里降低会比较好点.
* Read/Write Enabled:  
运行时编写Mesh以便修改数据.默认开启
* Optimize Mesh:  
该选项决定Mesh中的三角形顺序.默认开启
* Import BlendShapes:  
导入BlendShapes.默认开启
* Generate Colliders:  
生成Colliders? 开启时应当避免几何体移动? 默认关闭
* Swap UVs:   
当光照贴图(Lightmapping)物体采用了错误的UV通道时使用.默认关闭
* Generate Lightmap UVs:  
创建第二UV通道用于Lightmapping(光照贴图).默认关闭

#### Normals&Tangents  
法线和切线设置  
* Normals:  
法线的计算方式
  * Import:  
  默认选项,从源文件中导入法线
  * Calculate:  
  通过设置平滑角度(Smoothing Angle)来计算法线
  * None:  
  禁用法线.如果网格既不是法线映射,也不受实时照明的影响,使用此选项
* Tangents:  
切线的计算方式  (同法线的三个选项)

#### Materials
材质设置  
* Import Materials:  
一般按默认设置,直接导入材质即可

## Rig面板  
* Animation Type:  
动画类型.
  * None:   
  没有动画
  * legacy:  
  老版本动画,功能较少,但是不容易出错
  * Generic:  
  4.0版本推出的Mecanim动画系统中的Generic动画类型,用于普通动画
  * Humanoid:  
  4.0版本退出的Mecanim动画系统中的Humanoid动画类型,用于人形动画(提供了动画的重定向功能,也就是提供了一套动画赋予给多个体型不同的模型的解决方案)
* Avatar:  
当选择Humanoid时,该选项可用.创建一个Avatar(Mecanim系统的简化人形骨架结构到用户实际提供的骨架结构的映射,这种映射关系称为Avatar) 一般选择Create from this model,Mecanim会自动生成Acatar,最好进入Configure手动查看以便进行细调
* Optimize Game Object:  
打开此选项,会直接使用Mecanim系统的简化人形骨架结构,会提高性能(貌似动画不会那么细腻了?)默认关闭

## Animations面板
* Import Animation:  
导入动画,如果取消此勾选,该模型文件将不会导入动画信息.
* Anim.Compression:  
动画压缩
  * None:  
  不使用动画压缩
  * KeyFrame Reduction:  
  减少关键帧
  * Optimal:  
  最优分配(默认)
* Rotation Error  
* Location Error
* Scale Error  
`[注]error也有误差,偏差的含义`
这三个Error参数 是压缩的阈值 他的压缩原理是，当两帧之间移动,旋转,缩放的数值小于你当前所填的0.5时,这一帧就会被删掉.开到0.8之后动画的失真就比较严重了,值越低,动画也会越细腻,但是性能开销也会相应增大
* Clips:  
动画切分.可以在当前动画中剪切出一个片段作为动画源,也就是一个动画文件中可以有很多Animation Clips.
* Loop Time:  
动画会循环播放
* Loop Pose:  
在勾选LoopTime的同时,最好把Loop Pose也勾选,该选项使首帧和尾帧自然过渡衔接(毕竟美术不一定会做的面面俱到)
* Bake Into Pose:  
烘焙为姿势,此选项开启,就相当于人物的位移,旋转,比例均看做是人物本身姿势的变化,并不会改变Transform属性.一般都会开启(跳跃动作是不开启的因为需要Y坐标的变化)
* Loop Match:  
检查是否匹配,绿色匹配良好,红色匹配很差,可以通过Clips功能寻找匹配良好的位置.
* Mirror:  
镜像.比如有一个左转跑的动画,勾选此选项另存为一个右转跑的动画,利于动画复用
* Events:  
事件.可以在动画的某一帧添加一个事件,和程序交互.
* Mask:  
动画遮罩.可以屏蔽一部分的肢体动画
