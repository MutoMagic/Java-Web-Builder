# Java-Web-Builder
**build.xml** 想必大家对这东西并不陌生。在这个项目诞生之前，笔者都是全量build，为此也受到了不少的伤害。那时候的笔者是迫需要一个能增量打包的工具，于是就百度、Google翻查各种相关资料，该项目就是在这种情况下奇葩的诞生了。

> 黑历史：测试期间笔者用自己的一个项目作为实验材料，结果整个项目都被吞掉了 QAQ

## 项目说明
1. 整个项目也就5个文件，分别是：

    **ant-contrib-1.0b3.jar** &emsp; 一个灰常好用的Ant拓展包，详见 http://ant-contrib.sourceforge.net/  
    **build.xml** &emsp; Ant的构建文件，详见 http://ant.apache.org/  
    **build.properties** &emsp; build配置文件  
    **delete\_file\_list.txt** &emsp; 需要删除的文件列表，与增量编译有关（当前版本中并无卵用）  
    **deploy\_file\_list.txt** &emsp; 需要部署的文件列表，与增量编译有关  

2. 笔者的Ant版本：Apache Ant(TM) version 1.9.6 compiled on June 29 2015
3. 笔者的JDK版本：1.7.0_80

## How to use
1. 将5个文件放到你自己项目的根目录
2. 设置build.properties，这东西一次修改，到处调试(雾)。有关build.properties的配置这里说明一下：

    **cfg.project.name** &emsp; 项目名称，这个属性最终会影响到你的包名（war包）  
    **cfg.project.webroot** &emsp; webroot目录，这个我就不要多说了吧。用idea的盆友要注意了，有的时候我记得是web并不是eclipse中的webRoot  
    **cfg.build.type**	 &emsp; build类型，full为全量build，incremental为增量编译  
    **cfg.build.encoding** &emsp; 编码类型，这里都是UTF-8多好，为啥还要执迷不悟非要用个GBK（乱码什么的最讨厌了）  
    **cfg.build.tomcat** &emsp; tomcat的根目录，主要用来获取jsp-api.jar和servlet-api.jar  
    **cfg.build.output** &emsp; 输出目录，也就是最终war包所在地。需要留意的是，每次build都会在里面生成一个build.log日志文件  

录什么的推荐使用绝对路径，相对路径默认是你项目的根目录。

3. 编写*\_file_list.txt 把需要编译的文件及其路径写入此文件

    src/package/fileName.java  
    webRoot/fileName.jsp

4. 运行Ant Build
  
## 常见问题
1. 有些童鞋喜欢吧jar放到lib（WEB-INF/lib）中（强迫症的童鞋注意了，前方高能反应）。笔者之所以不放入配置文件，是因为不推荐这么做。

> 修改方法：  
> &emsp; 1、在build.xml中寻找名称为build的target  
> &emsp; 2、修改taskdef的classpath属性为jar文件路径

## License

    Copyright 2015 muto
    
    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at
    
        http://www.apache.org/licenses/LICENSE-2.0
    
    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
