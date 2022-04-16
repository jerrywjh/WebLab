# JSP 开发环境的安装和配置- JDK+Tomcat+Eclipse+MySQL

因为网上没有特别合适的关于JSP+Tomcat+MySQL+Eclipse的开发环境的安装和配置教程，很多初学者也是比较懵。为了这门课，单独写一个开发环境的配置教程。

Web开发分为前端(Browser side)和后端(Server side）两个部分。 其中HTML，CSS， Javascript属于前端技术，其运行环境就是浏览器(Web browser), 可以用Sublime, VS Code, Vim等普通的文本编辑器来开发。

但是Web后端(Server Side)的情况就比较复杂了：

1. 如果使用Java作为开发语言，具体来说就是用JSP + Servlet来开发，就需要Java程序的运行环境JDK/JRE.
2. 还需要一个Web服务器(具体来说是个应用服务器,如Tomcat)来运行Web服务端的程序.
3. 出于项目管理的需要，一般来讲，还需要使用集成开发工具(IDE)，如Eclipse, Netbean等。
4. 一些特定的功能还需要相应的库(Lib)来支持。
5. 在绝大多数的情况下，都需要使用数据库来存储和管理数据，因此还需要数据库软件和服务，如MySQL, SQL Server, Oracle等。

由于涉及的软件比较多，而且都是不同公司或开发者维护的开源软件，软件之间也存在版本和兼容性的问题，现以2022年4月左右在Windows上的安装和配置进行整理如下 （Mac 或是Linux下的安装配置请自行研究）：

**说明如下:**
1. 这个教程适用于Windows下的开发环境，不是服务端的部署环境。
1. 不涉及J2EE方面各种复杂的框架，面向JSP的初学者。

 ## 第一步: 安装JDK 

要运行Java或是JSP程序，Java的运行环境是必须的。所以第一步就是要安装JDK(Java Development Kit). 很多情况下，你的电脑里已经安装过JDK.如果版本不是很老的话，可以用以前安装过的JDK也可以。 

#### 版本: JDK 17

目前官方JDK最新的版本是JDK18. 但18这个版本是个临时的版本，半年后就过期了。JDK17是Long-Term-Support的版本，因此建议使用JDK17.

#### 下载地址: https://www.oracle.com/java/technologies/downloads/#java17 

下载那个Windows 版本的Installer或是MSI Installer就可以，下载后安装即可.

**注意**:  JDK17缺省的安装路径是C:\Program Files\Java\jdk-17.  当然安装到其他路径也可以，但需要记住具体的安装位置，因为后面配置其他软件的时候需要选择JDK的所在的目录。

## 第二步：安装Tomcat

JSP需要运行在一个Web服务器的环境中，具体说，需要一个JSP/Servlet的应用服务器. 这一类的软件有很多，最常用的就是Tomcat.

>  什么是JSP/Servlet的应用服务器？
>  基本上你可以理解为一个Web服务器+JSP/Servlet的运行环境.

#### 版本：Tomcat 9.0. 

目前最新的Tomcat版本是10.0，但10.0的版本和以前的版本有兼容性问题，把javax.\*的包都改成jakarta.\*的命名了。不建议使用10.0的版本。推荐9.0的版本。

#### 下载地址: https://tomcat.apache.org/download-90.cgi 

对Windows用户来说，下载那个 32bit/64bit Windows Service Install就可以。下载完安装该软件.
需要注意的是：

* 该软件是服务类软件，是始终运行于电脑后台的。
* 安装过程中有个服务端口(connector Port)的设置，需要你记下来，缺省的应该是8080.
* 安装过程中还需要选择JDK/JRE的路径，如果缺省的路径不对，你需要手动选择在第一步下载的JDK的安装目录。

安装完毕后，访问http://localhost:8080, 如能出现 Apache Tomcat的页面，说明安装成功了

**如何启动和停止服务**：

* 安装完毕后，可以在右下角的系统托盘中的Apache Tomcat中来启动/停止/配置Tomcat服务。
* 在Windows的服务列表中也可以看到Apache Tomcat, 也可以在Windows Services中进行Tomcat服务的启动和停止。  
* 也可以运行安装目录中的脚本/批处理文件来启停服务.  startup.bat  shutdown.bat


## 第三步： 安装Eclipse

#### 版本：Eclipse最新版 2022-03
#### 下载地址: https://www.eclipse.org/downloads/

**注意**：Eclipse是个通用的IDE，对于JSP开发来说，选择Eclipse IDE for Enterprise Java and Web Developers的版本。

1. 点击 **Download Packages** -> 选择**Eclipse IDE for Enterprise Java and Web Developers.** -> **Windows x86_64**
1. 下载完毕后，解压缩到一个目录下，就可以直接用了。 一般来讲，可以解压缩到c: \ ,  c:\Program files, 或是个人的用户目录下。
1. 解压缩后运行Eclipse,  开始会提示你设置Workspace, 这个一般建议放到个人的用户主目录下面。


## 第四步： 安装MySQL服务

### 版本： MySQL Community Server 8.0
下载地址：https://dev.mysql.com/downloads/mysql/
点击那个"MySQL Installer for Windows", 进入下载页面，然后选择那个大的文件下载( mysql-installer-community-8.0.xx.x.msi).

**注意**：
1. 不要去下载那些Enterprise, cloud, cluster的版本，是收费的！要下载MySQL Community server.
2. Oracle的网站和产品设计都非常反人类，要仔细操作。这种公司...。
3. 安装过程中,除了MySQL Server服务外，把MySQL Workbench + MySQL Connector/J (JDBC)  一起安装上去
4. 安装MySQL serve的时候，选择Developer Default (或者Development computer模式) 。
5. 需要设置root用户的密码。

安装完毕后，可以启动MySQL Workbench来连接数据库，如果能用root用户+密码可以正常连接数据库，说明数据库服务已经正常运行。也可以在Windows服务中查看和管理MySQL 服务的状态。


## 其他

### 为Web project引入MySQL Driver

把mysql-connector-java-8.xxxx.jar 文件copy到 webapp/WEB-INF/lib目录下就可以了

* 缺省情况下，Mysql connector的jar文件安装在 c:\Program Files(x86)\MySQL\Connector J 8.0\ 的目录下。



