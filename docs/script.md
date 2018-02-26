# Script
> 记录经常使用的脚本数据

## 升级Golang依赖包
原始脚本在 [https://gist.github.com/andy-zhangtao/e3fb38852bd381505e7d89cc9d2038f8](https://gist.github.com/andy-zhangtao/e3fb38852bd381505e7d89cc9d2038f8)
<script src="https://gist.github.com/andy-zhangtao/e3fb38852bd381505e7d89cc9d2038f8.js"></script>

### 脚本执行过程

1. 从Github clone指定工程(工程由参数传递，因此$1就是工程git路径。例如https://github.com/andy-zhangtao/DDog.git。当前仅支持Https方式，不支持ssh方式)
2. 然后会切换到指定分支(通过GITBRANCH判断,如果为空，则是master。 如果有值，则会切换到此分支。大小写及空格敏感)。
3. 在工程目录当中执行dep操作。 当前不支持进入二级目录执行dep操作
4. dep执行之后，会读取Git操作所需要的数据(GITEMAIL,GITUSR和GITPASS)。如果数据均存在，则执行git push操作。

### 注意点
1. 所有操作都是在/tmp/dep目录中进行，因此注意/tmp剩余空间是否满足操作需要
2. 如果执行失败，当前不会返回更详尽的日志。 所以需要人工确认git分支，用户名，口令等信息是否正确。
