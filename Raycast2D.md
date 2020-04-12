## `Raycast(2D)`

### 和3D的区别

> 1. `Physics2D.Raycast`的返回值为`RaycastHit2D`结构体
> 2. 前两个参数不能简化为一个参数`Ray`，因为`Ray`是两个`Vector3`，在`2D`中不需要使用`Vector3`
> 3. 在`Debug.DrawLine`中，方向使用`transform.up`而不是`transform.forward`
> 4. 

### `RaycastHit2D`结构体变量

> - collider
> - point
> - 等

### 不检测到自身的collider

```
Physics2D.queriesStartInColliders = false;
```

