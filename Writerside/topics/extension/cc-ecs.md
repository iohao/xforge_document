# ECS

**可以保证各平台计算一致性(Tween和Timer功能除外)**

ECS 的全称是 Entity(实体)、Component(组件)、System(系统)。

Entity（实体）
> 实体它在ECS中扮演的是组件的“载体”，实体是不包含任何数据和业务逻辑的。它的数据结构很简单只有一个ID。所有加在该实体上的组件就会与这个ID关联，通过实体就可以访问到身上的组件和组件上面的数据。

Component（组件）
> 组件只包含数据，组件本身没有办法改变数据(人为规定的)。组件上的数据描述了实体的某一个特征。想要组件产生作用就必须把组件加载到实体上，单独的组件是没有任何意义的。

System（系统）
> 真正包含业务逻辑的就是系统。系统所关心的东西就是包含一个或者多个组件的集合，系统通过该集合捕获有该集合中所有组件的实体。之后就可以操作这些实体，可以删除，在实体上增加或者删除组件，改变组件上的数据等待。这就是系统做的事情。

## 安装

在项目根目录执行
```Shell
npm run package
```

选择```模块```，找到```cc-ecs```。

## 使用

```TS
import {ecs, tween, timer, ecsclass, filter, EcsComponent, EcsSingleton, EcsEntity, EcsSystem} from 'db://pkg/@gamex/cc-ecs';

// 实体
class MyEntity extends EcsEntity {
    // 允许回收
    static allowRecycling = true;
}

// 组件
@ecsclass('MyComponent')
class MyComponent extends EcsComponent<MyEntity> {
    // 允许回收
    static allowRecycling = true;
    public count = 0;

    // 因为开启回收，触发删除后重制数据
    protected onRemove(){
        this.count = 0;
    }
}

// 单例组件
@ecsclass('MySingleton')
class MySingleton extends EcsSingleton{
    
}

// 系统
class MySystem extends EcsSystem {
    private filter = filter.all(MyComponent);
    execute(dt: number) {
        // 查询所有符合条件的实体
        this.query(this.filter).forEach(entity => {
            console.log(entity.get(MyComponent).count);
        })

        // 添加timer
        this.timer.add(
            timer(() => {console.log('timer'); })
        );
        
        // 添加tween
        const comp = this.find(this.filter, MyComponent);
        this.tween.add(
            tween(comp).to(1, {count: 100})
        );

        // 驱动timer和tween
        this.timer.step(dt);
        this.tween.step(dt);
    }
}

// 创建实体并添加组件
const entity = ecs.createEntity(MyEntity, node);
entity.add(MyComponent);

// 单例组件，不依附于实体而存在，一般用于存储全局数据
ecs.getSingleton(MySingleton);

// 将系统注册到ecs中
ecs.addSystem(MySystem);
// 驱动系统运行
ecs.execute(dt);
```
