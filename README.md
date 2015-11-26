# Java-Web-Builder
build.xml想必大家对这东西并不陌生。在这个build.xml诞生之前，笔者都是全量build，为此也受到了不少的伤害。
那时候啊笔者是迫的需要一个能增量打包的工具，于是百度、Google翻查各种资料，终于在2015-11-26这一天该项目奇葩的诞生了。

	<s>黑历史：测试期间笔者用自己的一个项目作为实验材料，结果整个项目都被吞掉了</s> QAQ
	雾：幸好有svn，可惜是一个星期前的XD

## 项目说明
1. 整个项目也就5个文件，分别是：

	* ant-contrib-1.0b3.jar		一个灰常好用的Ant拓展包，详见 http://ant-contrib.sourceforge.net/
	* build.xml			Ant的构建文件，详见 http://ant.apache.org/
	* build.properties		build配置文件
	* delete_file_list.txt		需要删除的文件列表，与增量编译有关（当前版本中并无卵用）
	* deploy_file_list.txt		需要部署的文件列表，与增量编译有关

2. 笔者的Ant版本：Apache Ant(TM) version 1.9.6 compiled on June 29 2015
3. 笔者的JDK版本：1.7.0_80

## How to use
1. 将5个文件放到你自己项目的根目录
2. 设置build.properties，这东西一次修改，<s>到处调试(雾)</s>。有关build.properties的配置这里说明一下：

	* cfg.project.name	项目名称，这个属性最终会影响到你的包名（war包）
	* cfg.project.webroot	webroot目录，这个我就不要多说了吧。用idea的盆友要注意了，有的时候我记得是web并不是eclipse中的webRoot
	* cfg.build.type	build类型，full为全量build，incremental为增量编译
	* cfg.build.encoding	编码类型，这里都是UTF-8多好，为啥还要执迷不悟非要用个GBK（乱码什么的最讨厌了）
	* cfg.build.tomcat	tomcat的根目录，主要用来获取jsp-api.jar和servlet-api.jar
	* cfg.build.output	输出目录，也就是最终war包所在地。需要留意的是，每次build都会在里面生成一个build.log日志文件

  目录什么的推荐使用绝对路径，相对路径默认是你项目的根目录。
  
## 常见问题
1. 有些童鞋喜欢吧jar放到lib（WEB-INF/lib）中（强迫症的童鞋注意了，前方高能反应）。
   笔者之所以不放入配置文件，是因为不推荐这么做（其实懒得这么弄了XD）。
   修改方法：
   >	在build.xml中找到buildtarget，修改taskdef的属性classpath即可。

## License

Copyright [2015] [muto]

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
