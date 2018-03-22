# eclipse--maven项目没有自动编译的问题

 项目上右键-->properties-->Java compiler-->building-->enable project specific setting-->build path problems-->选中abort  
 Incomplete build path/Circular dependencies  这两个选项修改为Warning

 比较好用，第一个自动编译的问题解决了。

 但工作空间中有好几个项目，这样一个个的改感觉太麻烦了，找了一下全局的解决方案：Preferences->java->compiler->Building，其后的操作与上面的一致。
