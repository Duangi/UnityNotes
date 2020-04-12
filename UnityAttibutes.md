## `Attributes`

[TOC]

#### 简介

在游戏脚本中，写上类似`[ExecuteInEditMode]`这种代码，可以使`unity`具有某些特性。比如这个是让游戏可以在不点击开始按钮的情况下运行

#### 注意

> 没有特别说明位置的，都和using *** 写在同一个位置

##### 重命名导致的引用丢失

```
using UnityEngine.Serialization;
[FormerlySerializeAs("playerDataList")]
```

##### 不运行游戏时调用脚本

例如：需要在编辑模式下，让Camera跟随角色移动

```
//在CameraController脚本中写下：
[ExecuteInEditMode]
```

##### 不允许存在多个重复组件

```
[DisallowMultipleComponent]
```

##### 提示该方法已经过时

```
[System.Obsolete("This is the old Version,You can use ")]
```

##### 点击物体时避免选中子物体

```
//给父物体添加一个脚本，写入
[SelectionBase]
```

##### 给游戏角色添加像素风

```
[AddComponentMenu("Image Effects/PixelBoy")]
```

##### 颜色调整

```
//第一个参数表示是否允许调整color中的透明度
//第二个参数表示不能使用HDR（高动态范围图像）模式
//写在class里面
[ColorUsage(false,false)]
```

##### 通过脚本给游戏对象自动添加组件

```
[RequireComponent(typeof(Rigidbody2D))]
```

##### 在`AddComponent`中自定义添加组件

```
[AddComponentMenu("Add Skill Button Component")]
//或者放在其他栏里面
[AddComponentMenu("UI/Add Skill Button Component")]
```

##### 给脚本添加参考链接

```
//添加参考链接，可以在Inspector界面中点击问号跳转
[HelpURL("https://www.bilibili.com/video/BV11j411f7N7")]
```

##### Inspector界面中不显示Public变量

```
//写在变量前面
[HideInInspector]
```

##### 排序

```
[OnOnepAsset]//没懂
```

##### 角色升级

```
[DefaultExecutionOrder]
```

##### 在Inspector中给变量分类

```
//写在变量前面
[Header("Player Status")]

//用空格隔开
[Space]
[Space(80)]

//给变量添加范围，以Slider的形式展示
[Range(5,10)]

//给变量添加提示
[Tooltip("No.1 is Blue Team. No.2 is Red Team. You can only input 1 or 2.")]

//自定义的类/结构体在Inspector中不能显示
//在类的前面加入
[System.Serializable]

//变量输入框太小
//在变量前面加上
[TextArea(3,10)]
//最短是3行，10行之后会出现滑动条
//或者
[Multiline(20)]
```

##### 使私有变量在Inspector中可见

```
[SerializedField]
```

##### 在不点击游戏界面的情况下，调用脚本中的函数

```
//在对应的函数前面
[ContextMenu("Flee")]
//在Inspector对应的脚本中右键点击“Flee”
```

##### `Inspector`变量调用函数

```
//比如，Speed取随机值
//第一个是按钮选项名称（自定义），第二个是调用的函数的名称
[ContextMenuItem("RandomizeSpeed","RandomSpeed")]
```

##### 在unity上方界面添加测试按钮

```
//只能给Static函数使用
[UnityEditor.MenuItem("Tools/Flee")]

```

##### 没有运行游戏时调用函数

```
//例如改变颜色
[CustomEditor(typeof(Cube))]
```





