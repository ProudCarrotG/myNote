#maven
一个依赖项管理工具，通过 `pom.xml` 文件来管理项目中应该安装哪些依赖项

# parent
```
<parent>
....
</parent>
```
父依赖项目
该项目会分析父依赖项目中所有的依赖项，包括依赖的版本等等

# dependencies
包括了需要使用的依赖项

## dependency
单个依赖项的详细内容、参数。
在 `dependencies` 下可以创建多个`dependency`
