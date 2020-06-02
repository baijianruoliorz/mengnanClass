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


以及自己昨天总结的快速开发工具的使用，这个项目没有使用，以前做的分布式电商使用了，，虽然没有做完，也一并开启，方便大家

主要写一写人人开源怎样使用

这个项目做很久了 但是如果让我使用人人开源快速开发还是得看视频，那么，不如写个笔记，记录一下怎么使用

以后自力更生---2020.06.01
  by:liqiqiorz
  
  
首先是renren-fast的使用：

把renren-fast直接粘贴到项目里面：就像这个项目一样，找到里面的db文件夹，把sql语句执行
这已经把表权限设计都设计好了 static里面的application就是一些常规配置：mysql,redis,shiro..
默认使用dev环境，所以在dev.yml里面继续看配置

renrenfast-vue ：npm install就行啦

人人generator:

首先在application.yml里面改mysql配置，生成数据库
在generator.properties里面mainpath:例如：com.atguigu
包名模块名
作者可以填自己信息：比如邮箱
表前缀改成自己的
然后启动在80端口启动了直接访问
在renren-fast里面点所有表民，点生成代码
点压缩包里面的main resources mapper --mapper文件
在main java下面就有指定的代码
将main文件直接粘贴到对应moudle文件 
然后resources里面有个src里面是前端代码可以删去
再到java文件夹里面就是生成的业务代码

接下来就是改的过程：
首先你会看到很多报错
首先缺少common.utils.pageutils 和query，R工具类 记住这个包名位置，就这样创建
直接在renren-fast里面的src-main-java-io-renren-common-utils -----找到pageutil和query，R，复制到common模块
然后一堆mybatis,shrio,,,等等的依赖都没有，建议见一个common moudle来映入这些依赖
common里面引入mp，lombok , httpcomponents---A为httpcore(这个是R的报错)，还有mysql驱动：mysql:connentor
然后query报错(org.apache....commons.lang.stringutils)这里依赖再renren-fast的pom里面找到commons-lang
放到common的pom里面就行
还有一个SQLFilter(再renren-fast的common-xxs文件夹，整个复制到common模块)
还有一个Constant再renren-fast utils里面的 Constant复制到common模块的utils
业务代码还有requiresPermission报错--shiro直接删 其他的controller都会有shiro注解，不想用直接删

此时可以调整一下逆向工程，生成controller取消Shrio注解
在renren-gengrator(直接复制到子模块就行)找到resource里面的template文件，里面很多vm文件
找到controller.java.vm 里面都有requiresPermission注解，直接删了就行（注释也行把shiro注解应用也删去
在重启逆向工程重新生成controller继续生成代码
此时只需使用controller(当然你也可以在开始使用时直接这么做)就可以替换掉以前的controller
这时候的业务代码是没有mp的一些注解的，要自己配置一下
common模块会有servlet异常(在xxsFilter)，在pom里面加servlet-api(A) (gv):javax-servlet version2.5 加个scope是provided:表示打包不需要带上
因为tomcat里面有 然后可以吧xss里面的xsshttpservletrequire,xssfilter删掉(防攻击的可以在以后用sercurity)
sqlfilter还会报错：缺少rrexceprion 可以在renren-fast的common-exception里面找到并复制（放utils里面）

报错解决完了要配置业务代码的一些数据库啥的，而且业务类的实体类主键并没有自增为了不再每一个实体类傻逼一样的调整，可以在配置文件
yml或者properties里面调整db-config id-type:auto（表示自增）

单元测试有个@runwith不用管。。
然后就可以注入一些service来测试一些crud啦


以上，就是逆向工程的使用方法。功能不全自己改




看了一下readme ,,这是什么魔鬼布置，相信我，我的ide里面是这样写的



放不出来图片，，不怎么会用这里的md，可能需要Oss保存再用地址？？这样有些麻烦，反正项目里面也教如何使用Oss呢~
