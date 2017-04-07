# U3D Attribute 整理

### ContextMenu   
在Inspector的ContextMenu中增加选项(点击脚本组件右上角的小齿轮) 并执行指定的函数(执行该Attribute后面的方法显示的不一定要和函数名相同)--并且只能执行 **无参** 的方法  
善用此方法可以在 **不执行游戏的情况下** 测试某些方法    
用法示例:
```
public class TestMenu : MonoBehaviour {
    [ContextMenu ("Do Something")]
    void Do () {
        Debug.Log ("Perform operation");
    }
}
```


### ContextMenuItem
可以在Inspector上面对变量追加一个右键菜单,并执行指定的函数  
用法示例:  
```
public class Sample : MonoBehaviour {
    [ContextMenuItem("Reset", "ResetName")]
    public string name = "Default";
    void ResetName() {
        name = "Default";
    }
}
```

### DisallowMultipleComponent  
对一个MonoBehaviour的子类使用这个属性,那么在同个GameObject上面,最多只能添加一个该Class的实例.尝试添加多个的时候,会出现提示(貌似大多数class都有这个需求吧)

### Header  
这个属性可以在Inspector中变量的上面增加Header(可以有效的理清楚各个变量的类别并显示在面板上)  
用法示例:  
```
public class ExampleClass : MonoBehaviour {
    [Header("生命值")]
    public int CurrentHP = 0;
    public int MaxHP = 100;

    [Header("魔法值")]
    public int CurrentMP = 0;
    public int MaxMP = 0;
}
```

### HideInInspector  
在变量上使用这个属性,可以让public的变量在Inspector上隐藏,也就是无法在Editor中进行编辑.适用于需要在代码中暴露在外面但是不希望在面板中直接操作的变量

### Multiline
在string类型上使用,可以在Editor上输入多行文字(像Text组件的那样)
### TextArea  
该属性可以把string在Inspector上的编辑区变成一个TextArea(和Multiline作用差不多啊)

### Range  
在int或者float类型上使用,限制输入值的范围 比较常用  
示例:`[Range(0, 100)] public int HP`

### RequireComponent
在class上使用,组件依赖.添加对另一个Component的依赖.当该Class被添加到一个GameObject上的时候,如果这个GameObject不含有依赖的Component,会自动添加该Component.且该Componet不可被移除.(除非先将脚本移除)  
示例:`[RequireComponent(typeof(Rigidbody))]
public class TestRequireComponet : MonoBehaviour {...}`

### SerializeField  
在变量上使用该属性,可以强制该变量进行序列化,即可以在Editor上对变量的值进行编辑,即使变量是private的也可以.在UI开发中经常可见到对private的组件进行强制序列化的用法.

### Space
使用该属性可以在Inspector上增加一些空位,参数是空位的高度.可以用于将逻辑不同的变量分开
示例`[Space(10)]`

### Tooltip
这个属性可以为变量上生成一条tip,当鼠标指针移动到Inspector上时候显示(显示该变量的详细信息)

###
