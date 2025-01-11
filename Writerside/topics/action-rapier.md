# 确定性物理引擎推荐

通过npm引入 @dimforge/rapier3d-compat 或 @dimforge/rapier2d-compat
然后tsconfig.json要里的compilerOptions，添加"allowSyntheticDefaultImports": true

使用时直接
`import RAPIER from ‘@dimforge/rapier2d-compat’;`
或
`import RAPIER from ‘@dimforge/rapier3d-compat’;`

例如

```
import RAPIER from '@dimforge/rapier2d-compat';
RAPIER.init().then(()=>{
   const world = new RAPIER.World({x:0,y:-98});
});
```

> 但需要注意的是，小游戏环境下`WebAssembly.instantiate`方法与标准不一致，它的第一个参数需要是文件路径，所以如果需要在小游戏环境下运行，需要去修改一下源码

