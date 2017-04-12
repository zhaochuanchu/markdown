# DOTween  
使用扩展方法,可以直接从组件调用方法.几乎所有的方法都返回Tweener或者Sequence以保持其引用.二者都可以保存为Tween(Sequence为两个Tweener的差异)  
Tween可以理解为一种衔接动画,过渡方式,补间动画以保证UI界面的平滑性和流畅性.  
该系统主要分为四个模块 `全局设置` `具体设置` `全局控制` `具体控制`  
其中全局的方法均为DOTween的静态方法,并且其中很多具有过滤选项.

### DOTween静态方法(Tweener也有对应的实例方法)
* CompleteAll/Complete(bool withCallbacks = false)
* FlipAll/Flip()
* GotoAll/Goto(float to, bool andPlay = false)
* KillAll/Kill(bool complete = true, params object[] idsOrTargetsToExclude)
* PauseAll/Pause()
* PlayAll/Play()
* PlayBackwardsAll/PlayBackwards()
* PlayForwardAll/PlayForward()
* RestartAll/Restart(bool includeDelay = true)
* RewindAll/Rewind(bool includeDelay = true)
* SmoothRewindAll/SmoothRewind()
* TogglePauseAll/TogglePause()

### DO前缀(立即执行)
* AudioMixer  
  * DOSetFloat
* AudioSource
  * DOFade(float to,float duration)  
  控制AudioSource的volume(音量)
  * DOPitch(float to,float duration)   
  控制AudioSource的Pitch(声调)
* Camera(待深入)
* Light  
  * DOColor(Color to, float duration)  
  控制Light的color(颜色)
  * DOIntensity(float to, float duration)  
  控制Light的Intensity(强度)  
  * DOShadowStrength(float to, float duration)  
  控制Light的ShadowStrength(阴影强度)
  * DOBlendableColor(Color to, float duration)  
  控制light的Color,使用此方法会允许其它的Tweener使用DOBlendableColor复合控制此Color.
* LineRenderer  
  * DOColor(Color2 startValue, Color2 endValue, float duration)  
  控制LineRenderer的Color
* Material(待深入)
* transform(带Vector3参数的方法都有对应的 **local** 版本)  
  * DoMove(Vector3 to, float duration, [bool snapping=false])  
  控制transform的平滑移动
  * DOMoveX/DOMoveY/DOMoveZ(float to, float duration, bool snapping)  
  控制transform单方向移动  
  * DOJump(Vector3 endValue, float jumpPower, int numJumps, float duration, bool snapping)  
  控制transform的跳跃
  * DORotate(Vector3 to, float duration, RotateMode mode)  
  控制transform的旋转
  * DOLookAt(Vector3 towards, float duration, AxisConstraint axisConstraint = AxisConstraint.None, Vector3 up = Vector3.up)  
  控制transform的朝向
  * DOScale(float/Vector3 to, float duration)  
  控制transform的缩放  
  * DOScaleX/DOScaleY/DOScaleZ(float to, float duration)  
  控制transform的单方向缩放  
  * DOPunchPosition(Vector3 punch, float duration, int vibrato, float elasticity, bool snapping)  
  指定一个移动方向,之后 **弹性返回** 初始位置(position)
  * DOPunchRotation(Vector3 punch, float duration, int vibrato, float elasticity)  
  指定一个旋转方向,之后 **弹性返回** 初始旋转(Roation)
  * DOPunchScale(Vector3 punch, float duration, int vibrato, float elasticity)  
  指定一个缩放vector3,之后 **弹性返回** 初始缩放(Scale)  
```
Punch应当是一种弹性计算的算法,大概是三角函数振幅逐渐减小的算法,模拟弹性
```
  * DOShakePosition(float duration, float/Vector3 strength, int vibrato, float randomness, bool snapping, bool fadeOut)  
  位置的随机震动效果
  * DOShakeRotation(float duration, float/Vector3 strength, int vibrato, float randomness, bool fadeOut)  
  旋转的随机震动效果
  * DOShakeScale(float duration, float/Vector3 strength, int vibrato, float randomness, bool fadeOut)  
  缩放的随机震动效果  
```
我猜测Shake大概是三角函数振幅总体减小趋势,但是中间随机反弹增大的算法,模拟震动
```
  * DOPath(Vector3[] waypoints, float duration, PathType pathType = Linear, PathMode pathMode = Full3D, int resolution = 10, Color gizmoColor = null)  
  指定transform的移动路径
  * 其它的待补充.
* UGUI许多组件都有扩展方法


---
### Set前缀  `这些方法可以应用于任何tween,调整其算法.`   
* SetAs(Tween tween \ TweenParams tweenParams)  
  设置Tween 包括(id,ease,loops,delay,timeScale,callbacks等)
* SetEase(Ease easeType \ AnimationCurve animCurve \ EaseFunction customEase)  
设置缓动函数(几十种Ease枚举) 在http://easings.net/zh-cn 中可以查阅其效果 
* SetAutoKill(bool autoKillOnCompletion = true)  
  在动画结束后自动Kill该tweener(如果想重复利用该Tweener,可以SetAutoKill(false);)
* SetId(object id)  
  为该tweener设置任何类型(如int,string,枚举等)的Id,这将作为DOTween的静态方法的过滤条件
* SetLoops(int loops, LoopType loopType = LoopType.Restart)  
  为该tweener设置循环次数和循环类型
* SetRecyclable(bool recyclable)  
  如果设置为true,该tweener被kill后会被回收(回收到缓存池吗?有点不懂)
* SetRelative(bool isRelative = true)[位移时常用]  
  如果设置为true,endValue将会被计算为endValue+startValue.  
  即向X轴移动1米有两种表示方式:  
  * transform.DOMoveX(transform.position.x+1,duration)
  * transform.DOMoveX(1,duration).SetRelative();  
  可以看出第二种表示方式更直接
* SetUpdate(UpdateType updateType, bool isIndependentUpdate = false)  
  * 设置插值动画的更新类型,可以选择.Update,fixedUpdate,LateUpdate(如果发现tweener动画有卡顿可以尝试改变updateType).isIndependentUpdate如果设置为true,该tweener动画的执行将不依赖于Unity的Time.timeScale(对于做游戏暂停的时候保证UI动画正常执行有重要意义)  

---
### On前缀(callback 满足条件时执行回调函数)`可利用lambda表达式` 
* OnComplete(TweenCallback callback)  
  Tweener结束后调用
* OnKill(TweenCallback callback)
* OnPlay(TweenCallback callback)
* OnPause(TweenCallback callback)
* OnRewind(TweenCallback callback)
* OnStart(TweenCallback callback)
* OnStepComplete(TweenCallback callback)  
  每一loop结束后调用
* OnUpdate(TweenCallback callback)  
  每一帧调用
 
---
### Others  
* From(bool isRelative = false) 
* SetDelay(float delay)
* SetSpeedBased(bool isSpeedBased = true)
  


