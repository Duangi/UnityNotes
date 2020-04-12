## ```Raycast(3D)```

#### 定义

`Raycast`表示从某一个特定的点，向某一个特定的方向射出一条不可见的射线，当射线碰到的物体拥有**`collider`**时，会将碰撞信息记录下来

#### 通用函数

```
Physics.Raycast(Vector3 origin,Vector3 direction,RaycastHit hitinfo,float distance,int LayerMask,QueryTriggerInteraction)
```

> `origin`：发射点 `direction`:射线方向  `hitinfo`:碰撞信息 
>
> `distance`射线最大长度 `layermask` 指定层
>
> `QueryTriggerInteraction` Trigger是否交互 

返回值为`bool`类型

#### 注意事项

> 1. 通常使用过程中，`Raycast`前两个参数，会使用`Ray`来代替
> 2. 一般使用前三个参数，后面几个参数为可选项
> 3. 为了在游戏界面能显示出射线，通常使用`Debug.DrawLine()`
> 4. 当物体有`collider` 时，才能被`Raycast`检测到
> 5. `DrawLine()`只有在Gizmos按钮按下时可见



#### 例子

```
Ray ray;
ray = new Ray(transform.position, transform.forword);
RaycastHit = hitInfo;

if(Physics.Raycast(ray, out hitInfo, 				maxInstance,mask,QueryTriggerInteraction.Ignore))
{
	//Ignore代表：如果collider打开了IsTrigger开关，则该碰撞体会被这条射线忽略
	Debug.Log(hitInfo.collider);
	
	//Debug.DrawLine(transform.position,hitInfo.point, 		Color.red);
	Debug.DrawRay(transform.position, hitInfo.point, 		Color.yellow);	
}
else
{
	Debug.DrawLine(ray.origin, ray.origin + 				ray.direction * 100, Color.green);
}

```

#### 射线穿透

`RaycastAll()`

返回值变为了`HitInfo`的数组

由于返回值的改变，参数中的`HitInfo`也就没有必要了。

```
RaycastHit[] hits;
hits = Physics.RaycastAll(ray,maxDistance,mask);
//
```



#### 鼠标点击屏幕

> 1. 将鼠标点击的位置转换成，从摄像机到点击位置的一条射线
> 2. 通过这条射线，就可以知道在世界坐标中你想点击的那个点。

```
Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);
RaycastHit hitInfo;
if(Physics.Raycast(ray,out hitInfo,200)){

}
```

