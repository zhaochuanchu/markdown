# U3D Attribute 整理

### ContextMenu   
在Inspector的ContextMenu中增加选项(点击脚本组件右上角的小齿轮) 并执行指定的函数   
用法示例:
```
public class TestMenu : MonoBehaviour {
    [ContextMenu ("Do Something")]
    void DoSomething () {
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

### HeaderAttribute  
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

### MultilineAttribute
在string类型上使用,可以在Editor上输入多行文字(像Text组件的那样)

### Range  
在int或者float类型上使用,限制输入值的范围 比较常用
