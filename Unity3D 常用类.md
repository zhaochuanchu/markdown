### Quaternion

### Animation  
Loop Time，勾选这个选项之后，如果 Animator 处于播放这个动画状态时，在播放完第一遍这个动画片段之后，会自动循环从起始帧再次开始播放动画，如此循环往复。如果我们不勾选这个选项，例如 Animator 一直处于播放这个动画的状态，那么动画会定格在动画的结束帧，直到我们通过 Animator 切换这个 Animator 状态机的状态，切换到其他的动画；
Loop Pose 和 Cycle Offset，在勾选了 Loop Time 之后生效的两个选项，Loop Pose 用于控制动画循环播放时，从结束帧切换到起始帧时，动画的动作可以无缝的衔接上，Cycly Offset 就是用于控制循环的时候起始帧偏移用的；
