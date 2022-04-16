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
1. 没有涉及J2EE方面的内容，仅适用于JSP的初学者。

 ## 第一步: 安装JDK 

要运行Java或是JSP程序，Java的运行环境是必须的。所以第一步就是要安装JDK(Java Development Kit). 很多情况下，你的电脑里已经安装过JDK.如果版本不是很老的话，可以用以前安装过的JDK也可以。 
我们这里还是采用重新安装的最新版本。目前官方JDK最新的版本是JDK18，下载地址是https://www.oracle.com/java/technologies/downloads/#jdk18-windows
下载那个Installer或是MSI Installer就可以，下载后安装即可.

注意: 
* JDK18缺省的安装路径是C:\Program Files\Java\jdk-18.  当然安装到其他路径也可以，但需要记住具体的安装位置，因为后面配置其他软件的时候需要选择JDK的路径。

## 第二步：安装Tomcat

JSP需要运行在一个Web服务器的环境中，具体说，需要一个JSP/Servlet的应用服务器. 这一类的软件有很多，最常用的就是Tomcat.

>  什么是JSP/Servlet的应用服务器？
>  基本上你可以理解为一个Web服务器+JSP/Servlet的运行环境.

目前最新的版本是10.0，其实8.0，9.0的版本也是可以的。我们这里还是以最新的1.0为例来说明。
软件下载地址为https://tomcat.apache.org/download-10.cgi  对Windows用户来说，下载那个 32bit/64bit Windows Service Install就可以。
下载完安装该软件.
需要注意的是：

* 该软件是服务类软件，是始终运行于电脑后台的。很多同学不太理解 **应用程序**和**服务**这两类软件的区别。
* 安装过程中有个服务端口(connector Port)的设置，需要你记下来，缺省的应该是8080.
* 安装过程中还需要选择JDK/JRE的路径，如果缺省的路径不对，你需要手动选择在第一步下载的JDK的安装路径。

Tomcat安装成功后，会自动启动服务，你可以在Windows的桌面右下角的系统托盘处找到Apache Tomcat的图标。


## 第三步： 
