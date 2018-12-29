**课程计划**

 - 第一天：
    - 1、电商行业的背景介绍--电子商务
    - 2、淘淘商城的系统架构
        - a) 功能介绍
        - b) 架构讲解
    - 3、工程搭建--后台工程
        - a) 使用maven搭建工程（工程大）
        - b) 使用maven的tomcat插件启动工程
    - 4、SVN的使用
 - 第二天：
    - 1、服务中间件dubbo--远程调用技术
    - 2、SSM框架整合
    - 3、整合测试
    - 4、商品列表查询功能实现
 - 第三天：
    - 1、商品类目选择
    - 2、图片上传
        - a) 图片服务器FastDFS
        - b) 图片上传功能实现
    - 3、富文本编辑器KindEditor的使用
    - 4、商品添加功能完成
 - 第四天：
    - 1、前台系统搭建
    - 2、CMS系统的实现--内容管理系统
        - a) 内容分类管理
        - b) 内容管理
    - 3、前台内容动态展示
 - 第五天：
    - 1、Redis服务器搭建--缓存
    - 2、向业务逻辑中添加缓存
    - 3、使用redis做缓存
    - 4、缓存同步
    - 5、Solr服务器安装--搜索
 - 第六天：
    - 1、Solrj使用测试--Solr服务的java客户端
    - 2、把数据库中的数据导入索引库
    - 3、搜索功能的实现
 - 第七天：
    - 1、Solr集群搭建--SlorCloud
    - 2、使用solrj管理solr集群
    - 3、把搜索功能切换到集群版
 - 第八天：
    - 1、什么是MQ--消息队列
    - 2、MQ的应用场景
    - 3、ActiveMQ的使用方法
    - 4、使用消息队列实现商品同步
 - 第九天：
    - 1、商品详情页面展示--动态展示 jsp + redis
    - 2、使用freemarker实现网页静态化
    - 3、ActiveMq同步生成静态网页
 - 第十天：
    - 1、Nginx的安装--访问静态资源
    - 2、Nginx配置虚拟机
    - 3、Nginx实现反向代理
    - 4、Nginx实现负载均衡
    - 5、SSO系统工程搭建--单点登录系统
 - 第十一天：
    - 1、SSO注册功能实现
    - 2、SSO登录功能实现
    - 3、通过token获得用户信息
    - 4、Ajax跨域请求（jsonp）
 - 第十二天：
    - 1、购物车实现
    - 2、订单确认页面展示
 - 第十三天：
    - 1、订单系统完成
    - 2、系统部署--上线流程
 - 第十四天~十六天：
    - 项目实战--需求、分组、实现
    - 项目总结

## **1、电商行业的背景介绍--电子商务**
> &emsp;&emsp;近年来，中国的电子商务快速发展，交易额连创新高，电子商务在各领域的应用不断拓展和深化、相关服务业蓬勃发展、支撑体系不断健全完善、创新的动力和能力 不断增强。电子商务正在与实体经济深度融合，进入规模性发展阶段，对经济社会生活的影响不断增大，正成为我国经济发展的新引擎。
&emsp;&emsp;中国电子商务研究中心数据显示，截止到2012年底，中国电子商务市场交易规模达7.85万亿人民币，同比增长30.83%。其中，B2B电子商务交易额达6.25万亿，同比增长27%。而2011年全年，中国电子商务市场交易额达6万亿人民币，同比增长33%，占GDP比重上升到13%；2012年，电子商务占GDP的比重已经高达15%。预计2013年我国电子商务规模将突破十万亿大关。

![](https://s1.ax2x.com/2018/11/06/5mvch6.png)

### **1.1、11.11**
![](https://s1.ax2x.com/2018/11/06/5mvazB.png)

 - 结论：
    - 1、电商行业很挣钱，找互联网相关的工作。
    - 2、电商行业技术要求很高、高可用、海量数据的存储。

### **1.2、电商行业技术特点**
 - 技术新
 - 技术范围广
 - 分布式
 - 高并发、集群、负载均衡、高可用
 - 海量数据
 - 业务复杂
 - 系统安全

## **2、淘淘商城的系统架构**
### **2.1、淘淘商城介绍**
> &emsp;&emsp;淘淘网上商城是一个综合性的B2C平台，类似京东商城、天猫商城。会员可以在商城浏览商品、下订单，以及参加各种活动。
&emsp;&emsp;管理员、运营可以在平台后台管理系统中管理商品、订单、会员等。
&emsp;&emsp;客服可以在后台管理系统中处理用户的询问以及投诉。

 - 电商模式：
    - B2B：商家到商家。阿里巴巴、1688(批发)、慧聪网、铭万网。
    - B2C：商家(京东)到用户。京东(自营)。
    - C2C：用户到用户。淘宝(赶集)。
    - B2B2C：商家(天猫)到商家(耐克)到用户。天猫(开发票)。
    - O2O：线上到线下。百度外卖、美团外卖、饿了么。

### **2.2、功能介绍**
![](https://s1.ax2x.com/2018/11/06/5mvyxJ.png)

 - 后台管理系统：管理商品、订单、类目、商品规格属性、用户管理以及内容发布等功能。
 - 前台系统：用户可以在前台系统中进行注册、登录、浏览商品、首页、下单等操作。
 - 会员系统：用户可以在该系统中查询已下的订单、收藏的商品、我的优惠券、团购等信息。
 - 订单系统：提供下单、查询订单、修改订单状态、定时处理订单。
 - 搜索系统：提供商品的搜索功能。
 - 单点登录系统：为多个系统之间提供用户登录凭证以及查询登录用户的信息。

### **2.3、系统架构**
#### **2.3.1、传统架构**
![](https://s1.ax2x.com/2018/11/06/5mvvrl.png)
 
 - 存在的问题：
    - 1、功能耦合度高
	- 2、系统维护成本高
	- 3、如果并发量大，无法解决高并发的问题

#### **2.3.2、1000个并发**
![](https://s1.ax2x.com/2018/11/06/5mvrkp.png)

 - 存在的问题：
    - 1、系统无法有效进行水平扩展（集群不能针对功能模块）
    - 2、用户存在重复登录的问题
        - 针对第二点：需要session共享，是以session广播的形式，比较消耗资源（宽带）。
 - 如果要达到10000并发
    - 需要20台服务器做tomcat集群。
    - 注意：当tomcat集群中节点数量增加，服务能力先增加后下降。所以集群中节点数量不能太多，一般也就`5个`左右。

#### **2.3.3、分布式架构（10000个并发）**
 - 需要按照功能点把系统`拆分`，拆分成独立的功能。单独为某一个节点添加服务器。需要系统之间配合才能完成整个业务逻辑。叫做`分布式`。
    ![](https://s1.ax2x.com/2018/11/06/5mvLpK.png)
 - 分布式架构：多个子系统相互协作才能完成业务流程。系统之间需要进行`通信`。
 - **集群**：`同一个工程部署到多台服务器上`。相当于同一个工程代码拷贝多份部署到多台服务器，每台服务器单独独立部署运行。
 - 分布式架构：
    - 把系统按照模块拆分成多个子系统，多个子系统相互协作才能完成业务流程系统之间需要进行通信。
 - 优点：
    - 1、把模块拆分，`使用接口通信`，`降低`模块之间的`耦合度`。
    - 2、把项目拆分成若干个子项目，不同的团队负责不同的子项目。
    - 3、增加功能时只需要再增加一个子项目，调用其他系统的接口就可以。
    - 4、可以`灵活`的进行分布式`部署`。
 - 缺点：
    - 1、系统之间交互需要使用远程通信，接口开发`增加工作量`。
    - 2、各个模块有一些通用的`业务逻辑无法共用`。

#### **2.3.4、基于SOA的架构**
> SOA：Service Oriented Architecture `面向服务的架构`。也就是把工程拆分成`服务层`、`表现层`两个工程。服务层中包含业务逻辑，只需要对外提供服务即可。表现层只需要处理和页面的交互，业务逻辑都是调用服务层的服务来实现。

![](https://s1.ax2x.com/2018/11/06/5mvEB3.png)

#### **2.3.5、淘淘商城系统架构**
![](https://s1.ax2x.com/2018/11/06/5mve1G.png)


## **3、技术选型和开发环境**
### **3.1、技术选型**
 - Spring、SpringMVC、Mybatis
 - JSP、JSTL、jQuery、EasyUI、KindEditor（富文本编辑器）
 - Redis（缓存服务器，单点登录，购物车）
 - Solr（全文搜索）
 - dubbo（分布式服务框架）
 - HttpClient（HTTP 协议访问客户端）
 - ActiveMQ（消息队列）
 - Quartz（定时任务）
 - FastDFS（图片服务器）
 - FreeMarker（网页静态化）
 - Nginx（反向代理服务器）
 - MyCat（数据库中间件）

### **3.2、开发工具版本和环境**
 - Eclipse Mars.2 Release (4.5.2)
 - Maven 3.5.4
 - Tomcat 7.0.47（Maven Tomcat Plugin）
 - JDK 1.7
 - Mysql 5.7
 - Dubbo 2.5.3
 - Nginx 1.8.0
 - Redis 3.0.0
 - ActiveMQ 5.13.0
 - Win10 操作系统
 - SVN （版本管理）

## **4、工程搭建--后台工程**
### **4.1、使用maven的好处**
 - 使用maven管理工程的好处如下：
    - 1) jar包的管理
    - 2) 工程之间的依赖管理
    - 3) 自动打包
    - 4) 统一的版本的控制

### **4.2、后台工程搭建分析**
详解如下：
```
Maven的常见打包方式：jar、war、pom
pom工程一般都是父工程，管理jar包的版本、maven插件的版本、统一的依赖管理。聚合工程。

taotao-parent：父工程，打包方式pom，管理jar包的版本号。
    |          项目中所有工程都应该继承父工程。
    |--taotao-common：通用的工具类、通用的pojo。打包方式jar
    |--taotao-manager：服务层工程。聚合工程。pom工程
        |--taotao-manager-pojo：打包方式jar
        |--taotao-manager-dao：打包方式jar
        |--taotao-manager-interface：打包方式jar
        |--taotao-manager-service：打包方式war (为了发布服务的方便)
    |--taotao-manager-web：表现层工程。打包方式war
```

### **4.3、工程搭建**
Maven相关配置：

 - M2Eclipse是eclipse中的Maven插件。（低版本的ecplise需要手动安装，高版本的eclipse自带，本博主用的是高版本的ecplise）
 - M2Eclipse是MyEclipse中自带的Maven插件。
    - 注意：
        - 如果我们单独用命令行的方式进行maven的使用时，我们用户的配置文件默认在~/.m2/setting.xml
        - 如果我们使用Eclipse或者MyEclipse的方式进行maven的使用时，我们用户的配置文件可以想放哪里就放哪里，只需要指定配置文件的路径即可。
 - 本地仓库目录：默认位置在：~/.m2/repository
 - 因为我们使用eclipse开发，所以我们把本地仓库放到我们安排好的目录中，需要在eclipse中指定用户的配置文件路径即可。如下图：
    ![](https://s1.ax2x.com/2018/11/06/5mv1dE.png)
 - 本地仓库的使用，我们既可以提前下好所需要的jar包，也可以边开发边联网下载！

Eclipse相关配置：

 - eclipse 设置默认编码为Utf-8
 - 需要设置的几处地方为：
    - Window --> Preferences --> General --> Content Type --> Text --> JSP 最下面设置为UTF-8
    - Window --> Preferences --> General --> Workspace   面板Text file encoding 选择UTF-8
    - Window --> Preferences --> Web --> JSP Files 面板选择 ISO 10646/Unicode(UTF-8)
    - Window --> Preferences --> General --> Workspace 面板 New text file line delimiter 选择 Unix

#### **4.3.1、taotao-parent**
 - 父工程必须是pom工程。
    - 创建步骤如下：
    （1）    
    ![](https://s1.ax2x.com/2018/11/06/5mvUon.png)
    （2）
    ![](https://s1.ax2x.com/2018/11/06/5mvtx2.png)
    （3）
    ![](https://s1.ax2x.com/2018/11/06/5mvACQ.png)
 - pom.xml
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
    http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.taotao</groupId>
	<artifactId>taotao-parent</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<packaging>pom</packaging>
	<!-- 集中定义依赖版本号 -->
	<properties>
		<junit.version>4.12</junit.version>
		<spring.version>4.2.4.RELEASE</spring.version>
		<mybatis.version>3.2.8</mybatis.version>
		<mybatis.spring.version>1.2.2</mybatis.spring.version>
		<mybatis.paginator.version>1.2.15</mybatis.paginator.version>
		<mysql.version>5.1.32</mysql.version>
		<slf4j.version>1.6.4</slf4j.version>
		<jackson.version>2.4.2</jackson.version>
		<druid.version>1.0.9</druid.version>
		<httpclient.version>4.3.5</httpclient.version>
		<jstl.version>1.2</jstl.version>
		<servlet-api.version>2.5</servlet-api.version>
		<jsp-api.version>2.0</jsp-api.version>
		<joda-time.version>2.5</joda-time.version>
		<commons-lang3.version>3.3.2</commons-lang3.version>
		<commons-io.version>1.3.2</commons-io.version>
		<commons-net.version>3.3</commons-net.version>
		<pagehelper.version>3.4.2-fix</pagehelper.version>
		<jsqlparser.version>0.9.1</jsqlparser.version>
		<commons-fileupload.version>1.3.1</commons-fileupload.version>
		<jedis.version>2.7.2</jedis.version>
		<solrj.version>4.10.3</solrj.version>
		<dubbo.version>2.5.3</dubbo.version>
		<zookeeper.version>3.4.7</zookeeper.version>
		<zkclient.version>0.1</zkclient.version>
		<activemq.version>5.13.0</activemq.version>
		<freemarker.version>2.3.23</freemarker.version>
		<quartz.version>2.2.2</quartz.version>
	</properties>
    <!-- 统一依赖jar包版本的管理， 其下的标签dependencies只是版本的管理，并不是依赖jar包-->
	<dependencyManagement>
		<dependencies>
			<!-- 时间操作组件 -->
			<dependency>
				<groupId>joda-time</groupId>
				<artifactId>joda-time</artifactId>
				<version>${joda-time.version}</version>
            </dependency>
            <!-- Apache工具组件 -->
            <dependency>
            	<groupId>org.apache.commons</groupId>
            	<artifactId>commons-lang3</artifactId>
            	<version>${commons-lang3.version}</version>
            </dependency>
            <dependency>
            	<groupId>org.apache.commons</groupId>
            	<artifactId>commons-io</artifactId>
            	<version>${commons-io.version}</version>
            </dependency>
            <dependency>
            	<groupId>commons-net</groupId>
            	<artifactId>commons-net</artifactId>
            	<version>${commons-net.version}</version>
			</dependency>
			<!-- Jackson Json处理工具包 -->
			<dependency>
				<groupId>com.fasterxml.jackson.core</groupId>
				<artifactId>jackson-databind</artifactId>
				<version>${jackson.version}</version>
            </dependency>
            <!-- httpclient -->
            <dependency>
            	<groupId>org.apache.httpcomponents</groupId>
            	<artifactId>httpclient</artifactId>
            	<version>${httpclient.version}</version>
			</dependency>
			<!-- quartz任务调度框架 -->
			<dependency>
				<groupId>org.quartz-scheduler</groupId>
				<artifactId>quartz</artifactId>
				<version>${quartz.version}</version>
            </dependency>
            <!-- 单元测试 -->
            <dependency>
            	<groupId>junit</groupId>
            	<artifactId>junit</artifactId>
            	<version>${junit.version}</version>
				<scope>test</scope><!-- test表示该范围传递不到下面去 -->
			</dependency>
			<!-- 日志处理 -->
			<dependency>
				<groupId>org.slf4j</groupId>
				<artifactId>slf4j-log4j12</artifactId>
				<version>${slf4j.version}</version>
            </dependency>
            <!-- Mybatis -->
            <dependency>
            	<groupId>org.mybatis</groupId>
            	<artifactId>mybatis</artifactId>
            	<version>${mybatis.version}</version>
			</dependency>
			<dependency>
				<groupId>org.mybatis</groupId>
				<artifactId>mybatis-spring</artifactId>
				<version>${mybatis.spring.version}</version>
            </dependency>
            <!-- mybatis分页 相关的，暂时没有用到 -->
            <dependency>
            	<groupId>com.github.miemiedev</groupId>
            	<artifactId>mybatis-paginator</artifactId>
            	<version>${mybatis.paginator.version}</version>
			</dependency>
			<!-- 分页插件pagehelper -->
			<dependency>
				<groupId>com.github.pagehelper</groupId>
				<artifactId>pagehelper</artifactId>
				<version>${pagehelper.version}</version>
            </dependency>
            <!-- MySql -->
            <dependency>
            	<groupId>mysql</groupId>
            	<artifactId>mysql-connector-java</artifactId>
            	<version>${mysql.version}</version>
            </dependency>
            <!-- 连接池 -->
            <dependency>
            	<groupId>com.alibaba</groupId>
            	<artifactId>druid</artifactId>
            	<version>${druid.version}</version>
            </dependency>
            <!-- Spring -->
            <dependency>
            	<groupId>org.springframework</groupId>
            	<artifactId>spring-context</artifactId>
            	<version>${spring.version}</version>
            </dependency>
            <dependency>
            	<groupId>org.springframework</groupId>
            	<artifactId>spring-beans</artifactId>
            	<version>${spring.version}</version>
            </dependency>
            <dependency>
            	<groupId>org.springframework</groupId>
            	<artifactId>spring-webmvc</artifactId>
            	<version>${spring.version}</version>
            </dependency>
            <dependency>
            	<groupId>org.springframework</groupId>
            	<artifactId>spring-jdbc</artifactId>
            	<version>${spring.version}</version>
            </dependency>
            <dependency>
            	<groupId>org.springframework</groupId>
            	<artifactId>spring-aspects</artifactId>
            	<version>${spring.version}</version>
            </dependency>
            <dependency>
            	<groupId>org.springframework</groupId>
            	<artifactId>spring-jms</artifactId>
            	<version>${spring.version}</version>
            </dependency>
            <dependency>
            	<groupId>org.springframework</groupId>
            	<artifactId>spring-context-support</artifactId>
            	<version>${spring.version}</version>
            </dependency>
            <!-- JSP相关 -->
            <dependency>
            	<groupId>jstl</groupId>
            	<artifactId>jstl</artifactId>
            	<version>${jstl.version}</version>
            </dependency>
            <dependency>
            	<groupId>javax.servlet</groupId>
            	<artifactId>servlet-api</artifactId>
            	<version>${servlet-api.version}</version>
            <scope>provided</scope>
            </dependency>
            <dependency>
            	<groupId>javax.servlet</groupId>
            	<artifactId>jsp-api</artifactId>
            	<version>${jsp-api.version}</version>
                <scope>provided</scope>
            </dependency>
            <!-- 文件上传组件 -->
            <dependency>
            	<groupId>commons-fileupload</groupId>
            	<artifactId>commons-fileupload</artifactId>
            	<version>${commons-fileupload.version}</version>
            </dependency>
            <!-- Redis客户端 -->
            <dependency>
            	<groupId>redis.clients</groupId>
            	<artifactId>jedis</artifactId>
            	<version>${jedis.version}</version>
            </dependency>
            <!-- solr客户端 -->
            <dependency>
            	<groupId>org.apache.solr</groupId>
            	<artifactId>solr-solrj</artifactId>
            	<version>${solrj.version}</version>
            </dependency>
            <!-- dubbo相关 -->
            <dependency>
            	<groupId>com.alibaba</groupId>
            	<artifactId>dubbo</artifactId>
            	<version>${dubbo.version}</version>
            </dependency>
            <dependency>
            	<groupId>org.apache.zookeeper</groupId>
            	<artifactId>zookeeper</artifactId>
            	<version>${zookeeper.version}</version>
            </dependency>
            <dependency>
            	<groupId>com.github.sgroschupf</groupId>
            	<artifactId>zkclient</artifactId>
            	<version>${zkclient.version}</version>
            </dependency>
            <!-- activemq -->
            <dependency>
            	<groupId>org.apache.activemq</groupId>
            	<artifactId>activemq-all</artifactId>
            	<version>${activemq.version}</version>
            </dependency>
            <dependency>
            	<groupId>org.freemarker</groupId>
            	<artifactId>freemarker</artifactId>
            	<version>${freemarker.version}</version>
            </dependency>
        </dependencies>
    </dependencyManagement>
    <build>
        <finalName>${project.artifactId}</finalName>
		<plugins>
			<!-- 资源文件拷贝插件 -->
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-resources-plugin</artifactId>
				<version>2.7</version>
				<configuration>
					<encoding>UTF-8</encoding>
				</configuration>
			</plugin>
			<!-- java编译插件 -->
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.2</version>
				<configuration>
					<source>1.7</source>
					<target>1.7</target>
					<encoding>UTF-8</encoding>
				</configuration>
			</plugin>
		</plugins>
		<!-- 统一插件版本的管理，pluginManagement是控制版本的，如果在子工程要使用该插件，需要在子工程中再配置坐标 -->
		<pluginManagement>
			<plugins>
				<!-- 配置Tomcat插件 -->
				<plugin>
					<groupId>org.apache.tomcat.maven</groupId>
					<artifactId>tomcat7-maven-plugin</artifactId>
					<version>2.2</version>
				</plugin>
				<!-- 配置打包时跳过测试 ，首次配置使用的时候会自动联网进行下载 -->
				<plugin>
					<groupId>org.apache.maven.plugins</groupId>
					<artifactId>maven-surefire-plugin</artifactId>
					<version>2.12.4</version>
				</plugin>
			</plugins>
		</pluginManagement>
	</build>
</project>
```

#### **4.3.2、taotao-common**
 - taotao-common：是通用的工具类、通用的pojo。打包方式jar。需要继承父工程。
 - 新建一个Maven Project，不使用骨架进行创建该工程。
    ![](https://s1.ax2x.com/2018/11/06/5mvNvz.png)
 - pom.xml
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
    http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>com.taotao</groupId>
		<artifactId>taotao-parent</artifactId>
		<version>0.0.1-SNAPSHOT</version>
	</parent>
	<artifactId>taotao-common</artifactId>
	<dependencies>
		<!-- 时间操作组件 -->
		<dependency>
			<groupId>joda-time</groupId>
			<artifactId>joda-time</artifactId>
		</dependency>
		<!-- Apache工具组件 -->
		<dependency>
			<groupId>org.apache.commons</groupId>
			<artifactId>commons-lang3</artifactId>
		</dependency>
		<dependency>
			<groupId>org.apache.commons</groupId>
			<artifactId>commons-io</artifactId>
		</dependency>
		<dependency>
			<groupId>commons-net</groupId>
			<artifactId>commons-net</artifactId>
		</dependency>
		<!-- Jackson Json处理工具包 -->
		<dependency>
			<groupId>com.fasterxml.jackson.core</groupId>
			<artifactId>jackson-databind</artifactId>
		</dependency>
		<!-- httpclient -->
		<dependency>
			<groupId>org.apache.httpcomponents</groupId>
			<artifactId>httpclient</artifactId>
		</dependency>
		<!-- quartz任务调度框架 -->
		<dependency>
			<groupId>org.quartz-scheduler</groupId>
			<artifactId>quartz</artifactId>
		</dependency>
		<!-- 单元测试 -->
		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<scope>test</scope><!-- test表示该范围传递不到下面去 -->
		</dependency>
		<!-- 日志处理 -->
		<dependency>
			<groupId>org.slf4j</groupId>
			<artifactId>slf4j-log4j12</artifactId>
		</dependency>
	</dependencies>
</project>
```

#### **4.3.3、taotao-manager**
 - taotao-manager：是聚合工程。打包方式pom。需要继承父工程。
 - 新建一个Maven Project，不使用骨架进行创建该工程。
    ![](https://s1.ax2x.com/2018/11/06/5mvkkS.png)
 - pom.xml
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
    http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>com.taotao</groupId>
		<artifactId>taotao-parent</artifactId>
		<version>0.0.1-SNAPSHOT</version>
	</parent>
	<artifactId>taotao-manager</artifactId>
	<packaging>pom</packaging>
	<dependencies>
        <!-- 配置对taotao-common的依赖-->
		<dependency>
			<groupId>com.taotao</groupId>
			<artifactId>taotao-common</artifactId>
			<version>0.0.1-SNAPSHOT</version>
		</dependency>
	</dependencies>
</project>
```

#### **4.3.4、taotao-manager-pojo**
 - taotao-manager-pojo：是一个Maven模块工程，打包方式jar。
 - 新建一个Maven 模块工程，不使用骨架进行创建该工程。过程同下图。不再赘述！
 - pom.xml
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
    http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>com.taotao</groupId>
		<artifactId>taotao-manager</artifactId>
		<version>0.0.1-SNAPSHOT</version>
	</parent>
	<artifactId>taotao-manager-pojo</artifactId>
</project>
```

#### **4.3.5、taotao-manager-dao**
 - taotao-manager-dao：是一个Maven模块工程，打包方式jar。
 - 新建一个Maven 模块工程，不使用骨架进行创建该工程。
    ![](https://s1.ax2x.com/2018/11/06/5mvIza.png)
 - pom.xml
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
    http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>com.taotao</groupId>
		<artifactId>taotao-manager</artifactId>
		<version>0.0.1-SNAPSHOT</version>
	</parent>
	<artifactId>taotao-manager-dao</artifactId>
	<dependencies>
		<!-- 配置对taotao-manager-pojo的依赖 -->
		<dependency>
			<groupId>com.taotao</groupId>
			<artifactId>taotao-manager-pojo</artifactId>
			<version>0.0.1-SNAPSHOT</version>
		</dependency>
		<!-- 配置对mybatis的依赖 -->
		<!-- Mybatis -->
		<dependency>
			<groupId>org.mybatis</groupId>
			<artifactId>mybatis</artifactId>
		</dependency>
		<dependency>
			<groupId>org.mybatis</groupId>
			<artifactId>mybatis-spring</artifactId>
		</dependency>
		<!-- mybatis分页 相关的，暂时没有用到 -->
		<dependency>
			<groupId>com.github.miemiedev</groupId>
			<artifactId>mybatis-paginator</artifactId>
		</dependency>
		<!-- 分页插件pagehelper -->
		<dependency>
			<groupId>com.github.pagehelper</groupId>
			<artifactId>pagehelper</artifactId>
		</dependency>
		<!-- MySql -->
		<dependency>
			<groupId>mysql</groupId>
			<artifactId>mysql-connector-java</artifactId>
		</dependency>
		<!-- 连接池 -->
		<dependency>
			<groupId>com.alibaba</groupId>
			<artifactId>druid</artifactId>
		</dependency>
	</dependencies>
</project>
```

#### **4.3.6、taotao-manager-interface**
 - taotao-manager-interface：是一个Maven模块工程，打包方式jar。
 - 新建一个Maven 模块工程，不使用骨架进行创建该工程。过程同上图。不再赘述！
 - pom.xml
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
    http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>com.taotao</groupId>
		<artifactId>taotao-manager</artifactId>
		<version>0.0.1-SNAPSHOT</version>
	</parent>
	<artifactId>taotao-manager-interface</artifactId>
	<dependencies>
		<!-- 配置对taotao-manager-pojo的依赖 -->
		<dependency>
			<groupId>com.taotao</groupId>
			<artifactId>taotao-manager-pojo</artifactId>
			<version>0.0.1-SNAPSHOT</version>
		</dependency>
	</dependencies>
</project>
```

#### **4.3.7、taotao-manager-service**
 - taotao-manager-service：是一个Maven模块工程，注意：`打包方式war`。
 - 新建一个Maven 模块工程，不使用骨架进行创建该工程。过程同上图。不再赘述！
 - 注意：需要在目录webapp下补齐所缺的目录WEB-INF和文件web.xml
 - pom.xml
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
    http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>com.taotao</groupId>
		<artifactId>taotao-manager</artifactId>
		<version>0.0.1-SNAPSHOT</version>
	</parent>
	<artifactId>taotao-manager-service</artifactId>
	<packaging>war</packaging>
	<dependencies>
		<!-- 配置对taotao-manager-dao的依赖 -->
		<dependency>
			<groupId>com.taotao</groupId>
			<artifactId>taotao-manager-dao</artifactId>
			<version>0.0.1-SNAPSHOT</version>
		</dependency>
        <!-- 配置对taotao-manager-interface的依赖：服务层发布服务要通过该接口 -->
        <dependency>
            <groupId>com.taotao</groupId>
            <artifactId>taotao-manager-interface</artifactId>
            <version>0.0.1-SNAPSHOT</version>
        </dependency>
		<!-- 配置对spring的依赖 -->
		<!-- Spring -->
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-context</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-beans</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-jdbc</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-aspects</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-jms</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-context-support</artifactId>
		</dependency>
	</dependencies>
</project>
```
 - web.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
	xmlns="http://java.sun.com/xml/ns/javaee" 
	xsi:schemaLocation="http://java.sun.com/xml/ns/javaee 
	http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd" 
	version="2.5">
	<display-name>taotao-manager-service</display-name>
	<welcome-file-list>
		<welcome-file>index.html</welcome-file>
		<welcome-file>index.htm</welcome-file>
		<welcome-file>index.jsp</welcome-file>
		<welcome-file>default.html</welcome-file>
		<welcome-file>default.htm</welcome-file>
		<welcome-file>default.jsp</welcome-file>
	</welcome-file-list>
	<!-- 暂时不需要配置什么东西 -->
</web-app>
```

#### **4.3.8、taotao-manager-web**
 - taotao-manager-web：是一个Maven工程，注意：`打包方式war`。需要继承父工程。
 - 新建一个Maven工程，不使用骨架进行创建该工程。过程同上图。不再赘述！
 - 注意：需要在目录webapp下补齐所缺的目录WEB-INF和文件web.xml
 - pom.xml
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
    http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>com.taotao</groupId>
		<artifactId>taotao-parent</artifactId>
		<version>0.0.1-SNAPSHOT</version>
	</parent>
	<artifactId>taotao-manager-web</artifactId>
	<packaging>war</packaging>
	<dependencies>
		<!-- 配置对taotao-common的依赖-->
		<dependency>
			<groupId>com.taotao</groupId>
			<artifactId>taotao-common</artifactId>
			<version>0.0.1-SNAPSHOT</version>
		</dependency>
        <!-- 配置对taotao-manager-interface的依赖：表现层调用服务要通过该接口 -->
        <dependency>
            <groupId>com.taotao</groupId>
            <artifactId>taotao-manager-interface</artifactId>
            <version>0.0.1-SNAPSHOT</version>
        </dependency>
		<!-- 配置对spring的依赖 -->
		<!-- Spring -->
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-context</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-beans</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-jdbc</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-aspects</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-jms</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-context-support</artifactId>
		</dependency>
		<!-- JSP相关 -->
		<dependency>
			<groupId>jstl</groupId>
			<artifactId>jstl</artifactId>
		</dependency>
		<dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>servlet-api</artifactId>
			<scope>provided</scope>
		</dependency>
		<dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>jsp-api</artifactId>
			<scope>provided</scope>
		</dependency>
		<!-- 文件上传组件 -->
		<dependency>
			<groupId>commons-fileupload</groupId>
			<artifactId>commons-fileupload</artifactId>
		</dependency>	
	</dependencies>
</project>
```
web.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
	xmlns="http://java.sun.com/xml/ns/javaee" 
	xsi:schemaLocation="http://java.sun.com/xml/ns/javaee 
	http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd" 
	version="2.5">
	<display-name>taotao-manager-web</display-name>
	<welcome-file-list>
		<welcome-file>index.html</welcome-file>
		<welcome-file>index.htm</welcome-file>
		<welcome-file>index.jsp</welcome-file>
		<welcome-file>default.html</welcome-file>
		<welcome-file>default.htm</welcome-file>
		<welcome-file>default.jsp</welcome-file>
	</welcome-file-list>
	<!-- 暂时不需要配置什么东西 -->
</web-app>
```

### **4.4、使用maven的tomcat插件启动web工程**
 - 启动taotao-manager-web工程。
 - 需要在taotao-manager-web工程的pom中，配置tomcat插件。配置启动的端口号和工程名称。
 - 在taotao-manager-web的pom文件中添加如下配置：
 - pom.xml
```xml
	<build>
		<plugins>
			<!-- 配置Tomcat插件  -->
			<plugin>
				<groupId>org.apache.tomcat.maven</groupId>
				<artifactId>tomcat7-maven-plugin</artifactId>
				<configuration>
					<port>8081</port>
					<path>/</path>
				</configuration>
			</plugin>
		</plugins>
	</build>
```
 - 在taotao-manager-web工程的webapp目录下新建启动首页jsp文件index.jsp
```xml
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>
	<h1>hello 淘淘商城</h1>
</body>
</html>
```
 - 先把工程taotao-parent、taotao-common安装到本地仓库中。然后再启动tomcat插件。否则会报如下错误：
    ![](https://s1.ax2x.com/2018/11/06/5mv8Bh.png)
    - 右键项目taotao-parent --> Run As --> Maven install
    - 右键项目taotao-common --> Run As --> Maven install
 - 选中工程taotao-manager-web，再启动tomcat插件：
    - 选中项目右键--> Run As --> Maven build... --> 在Goals中输入：clean tomcat7:run
 - 测试：访问地址：http://localhost:8081/

### **4.5、使用maven的tomcat插件启动聚合工程**
 - 由于聚合工程taotao-manager也是web工程（聚合工程中有web工程），所以它的启动该是怎样的呢？
 - 由于聚合工程taotao-manager没有表现层，但我们也打成了一个war包，我们是该运行聚合工程taotao-manager的整体？还是运行其中的web工程taotao-manager-service呢？
    - 答：运行他们两个都可以，但是不建议运行聚合工程中的web工程taotao-manager-service，因为运行该工程需要依赖dao，dao依赖pojo，这些依赖需要先安装至本地仓库中，该工程才可以运行，如果dao更改一下，taotao-manager-service想运行就需要重新安装至本地仓库，很麻烦！所以我们直接运行聚合工程taotao-manager该多好呢！聚合工程taotao-manager知道自己的里面有什么模块，它会把这几个模块打成一个war包运行。
 - 那么下面我们使用maven的tomcat插件启动聚合工程：
 - 需要在taotao-manager工程的pom中，配置tomcat插件。配置启动的端口号和工程名称。
 - 在聚合工程taotao-manager的pom文件中添加如下配置：
 - pom.xml
```xml
	<build>
		<plugins>
			<!-- 配置Tomcat插件  -->
			<plugin>
				<groupId>org.apache.tomcat.maven</groupId>
				<artifactId>tomcat7-maven-plugin</artifactId>
				<configuration>
					<port>8080</port>
					<path>/</path>
				</configuration>
			</plugin>
		</plugins>
	</build>
```
 - 在taotao-manager-service工程的webapp目录下新建启动首页jsp文件index.jsp
```xml
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>
	<h1>hello 淘淘商城</h1>
</body>
</html>
```
 - 先把工程taotao-parent、taotao-common安装到本地仓库中。然后再启动tomcat插件。
    - 右键项目taotao-parent --> Run As --> Maven install
    - 右键项目taotao-common --> Run As --> Maven install
 - 选中工程taotao-manager，再启动tomcat插件：
    - 选中项目右键--> Run As --> Maven build... --> 在Goals中输入：clean tomcat7:run
 - 测试：访问地址：http://localhost:8080/

## **5、SVN的使用**
### **5.1、SVN服务端**
 - SVN服务端使用VisualSVN，一般一个项目组只有一个svn，并不是每个开发者都需要安装服务端。
 - windows版本的安装可参考链接：https://www.cnblogs.com/chenmingjun/p/9916910.html
 - VisualSVN Server 的使用图解（windows版本）参考链接：https://www.cnblogs.com/chenmingjun/p/9926589.html

### **5.2、SVN客户端**
 - 客户端使用Eclipse的svn插件，在提供的Eclipse中已经安装好，直接使用即可。
 - 如果想自己安装：可参考链接：https://www.cnblogs.com/chenmingjun/p/9459401.html
 - 访问地址：https://DESKTOP-TEE3ASS:8443/svn/taotao-hm28/
    - https://{svn服务ip地址}/svn/{仓库名称}/
 - SVN 客户端的使用参考链接：https://www.cnblogs.com/chenmingjun/p/9926849.html
