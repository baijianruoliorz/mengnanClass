**首先这个码农很佛，也很弱，重点是弱。**

唉，因为同学太厉害了啊。。所以显得自己就很弱~

下面由liqiqiorz(就是我，嗯）对自己使用的这个框架进行进一步的说明讲解，我的目标是把这个项目开源：即谷粒课堂，不同于教程的
是，这里面加入了我自己写好的大量注解以及部分方法可能会有多种实现方式，最终把这个项目变成**学习笔记**供以后使用。

所以说这个项目大概是对我之前学习的一个总结，学JAVA之间还学习了GO所以划水了好长时间呢！因为我也已经做过好几个项目了，从入门的博客，到中级的商城，租房，再到分布式的人力资源管理系统
大多都是跟着教程，而缺乏自己的思考，所以这个项目想对自己更负责任一些，不如把它变成一个我自己的笔记，以后有什么需求再这上面抄抄改改就行了。
然后这边这个项目的复杂度对我来说也是蛮大的，毕竟是分布式+B2C的一个项目。。

所以开源之后，即使得不到什么支持，总之对自己有利就行~~

自己总结了一下写这个项目时所用的技术：后端：springboot+springCloud+mybatisP+mysql+easyExcel+Echarts and so on...
前端：主要学习了nuxt+vue-admin-template-master模板，也利于SEO，弥补ajax的缺陷，里面囊括的就很多啦
中间件：这个项目是没有MQ，seata（其实这两个也就是为用而用，会改配置就行，这种在秒杀场景是常客）的，但是加入了微信支付和阿里的Oss和视频点播技术。
虚拟机可以用也不用，我用的是阿里云的虚拟机完成的（榨干它最后的资本价值~
设计模式：B2C

build目录：一些编译的文件，类似于JAVA中的class文件，不需要去改
config：配置，项目中最基本配置，比如端口啊环境啊都可以在这里面修改~注意useEslint:false  这个检测的太严格了。。。
dev 和prop就是些环境，有base_api:可以改成本地默认访问后端地址
node_moudles:依赖
src:{#重要的打*
api:定义要调用的方法*
assets:静态资源
components:插件，放一些有趣的小玩意
icons:图标之类的~
router:路由*
store:没啥用
style:样式
utils:工具类
views：项目中的页面部分
}    ----2020.05.28
一些小细节：
console的network会列出所有的请求哦~~
登陆的话：有两个请求，浏览器中的一种机制，先做一个预请求，先测试是否连通，再请求！
请注意：配置文件修改的话，必须要重启，如果是其他代码ide会自动编译修改
所谓配置文件：比如base_url
network error:网路错误：代码有问题！
NO 'Access-Control-Allow-Origin'---一般是跨域问题：访问协议，IP，端口号，该框架端口号：9528
加注解或网关都可以解决呢！
import .. from 引入其他的JS文件
传参很多方法的
第一种就是拼接：直接+就完事了
第二种:``号里面直接可以{}
由于后端用的是requestBody获取的对象，所以不用params,而要用data获取数据
为了防止中文名字，所以Oss里面保存的不是JPG而是PNG
这里面分类规则是parentId=0
这个项目：执行全局异常处理就是后台代码的问题，当然可能是前端没有给默认值
netWork error:未解决跨域/路径写错了/后端更新服务器未重启
nacos:先引入依赖再配置文件再添加启动类注解就行了。。
feign再调用端写代码哦~
引入注册中心不注册的话不能启动会有 no server available的提示呢！
报错的话多看第一行和最后一行。。

Copyright (c) 2020-present Xiangrui Yang QQ:1099462011

这篇READMEv1.0作于---2020.05.28，写项目的第七天。
READMEV1.X ---写项目一直在更新一些细节问题
提交于--2020.06.02

前端C端：https://github.com/baijianruoliorz/vue-user

前端B端：https://github.com/baijianruoliorz/vue-admin

初步接口：
https://github.com/baijianruoliorz/guli_parent
