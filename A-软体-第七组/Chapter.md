# Accord.NET - A Machine Learning Framework
**By [Gong Zheng](https://github.com/ZZAster), [Lai MingJun](https://github.com/JunSerena), [Cheng YiXing](https://github.com/CCIyx) and [Tang ZhengTing](https://github.com/leotzt).**<br>
*Wuhan University*<br>
![Accord.NET](https://raw.githubusercontent.com/ZZAster/framework/development/A-软体-第七组/Picture-framework/accord-logo.png)<br>
*The Accord.NET logo taken from it's [official website](http://accord-framework.net/index.html).*

---
# Absract
The Accord.NET Framework is a .NET machine learning framework created to extended the features of original AForge.NET library. It combines with audio and image processing libraries which was completely written by C#. So Accord.NET can be used as a complete framework for compute vision, compute audition, signal processing and statistics applications for .NET users[[1]](https://en.wikipedia.org/wiki/Accord.NET).<br>

This chapter aims to provide several different point of views to this software's architecture. At first, an outside views will be given to analys and introduce the basical information of Accord.NET. Second, we will give a closer look at the code module underlying architecure. Last, we will analys deeply the existing problem or technical debts and try to give some useful solutions.<br>

---
# Table of Contents
- Intruduction
- Stackholder
- Context View
- Funcition View
- ...(some views)
- Evolution Perspective
- Conclution
- Referencies

---
# Introduction
Nowadays, machine learning and data analysis are becoming the hottest and most promising areas of programming. When dealing with various issues related to machine learning and data analysis, programmers need to use many complex algorithms to solve the problem. It’s quite cumbersome to write your own algorithmic functions, and the .NET framework developed by Microsoft at the time lacked such a library that supports multiple algorithms. Thus Andrew Kirillov developed AForge.NET which is a computer vision and artificial intelligence library completely written by C# for .NET Framework and the source code and binaries of the project are available under the terms of the Lesser GPL and the GPL (GNU General Public License)[[1]](https://en.wikipedia.org/wiki/Accord.NET).<br>

And then, on April 1, 2012, Andrew Kirillov announced the end of the public support for the library, temporarily closing the discussion forums. The last release of the AForge.NET Framework was made available on July 17, 2013. However, since its release 3.0 in 2015, the Accord.NET project started to incorporate most of the original AForge.NET source code in its codebase, continuing its support and development under the Accord.NET name.<br>

The Accord.NET is a framework for scientific computing in .NET which is extended from AForge.NET. The framework is comprised of multiple librares encompassing a wide range of scientific computing applications, such as statistical data processing, machine learning, pattern recognition, including but not limited to, computer vision and computer audition[[2]](http://accord-framework.net/index.html). The framework offers a large number of probability distributions, hypothesis tests, kernel functions and support for most popular performance measurements techniques. It support many useful libraries such as Accord.Math, Accord.Imaging, Accord.Audio and so on for .NET machine learning developer.<br>

This chapter aims at analys Accord.NET Framework as a software system. Thus, we will firstly analyze the outside look of this system which includes introduction, stakeholder and some part of context view. And then we will see some view points of Accord.NET, analyzing the inner architecture of it. Finally, some problems and the related solution or opinion will be given through the evolution perspective.

---
# Stakeholders
As a a project home on GitHub, Accord.NET has many stakeholders. The role of Accord.NET is mainly reflected in providing libraries for .NET applications. The libraries are below:  

* Scientific computing  
* Signal and image processing  
* Support libraries  

*Table1:The StakeHolders of Accord.NET*  

| Stakeholder class | Description |
|---|---|
| Acquirers | Now it's a open source project, and the cost is based on the donations. The original author is César Roberto de Souza. |
| Communicators | The team of the software has a mailbox, feedback@accord-framework.net to get the feedback from users. The developers of the team are also the communicators. Besides, users can talk with each others on the community. |
| Developer | There are 11 active contributors on GitHub in the past 12 months. This project has a relatively large team, in the top 10% of all project teams on Open Hub. And so far, there are 72 contributors in the history of the software. |
| Tester | All the bugs can be reported by posted on the community or mailed to the team. The menbers of the team or others will pick up the problem. |
| Users | Accord.NET has many kinds of users. Take professionals for an example, there are many essays published in the world. It's a very famous project. And it can be used to build other software. |
| Maintainers | The rule and standard will be confirmed by the team. The application is maintained by the developing team with decreasing Y-O-Y commits. Over the last twelve months, it has seen a substantial decrease in development activity.|
| Competitors | There are some similar project, such as SHOUGUN, CVWS.NET, Emgu CV and so on.  |
| Learners | This project is a open source project, it provides learners a lot of algorithms to learn about machine learning. |

*Table	3:	Most	active	contributors	in	trems	of	number	of	commits. *

| Contributor | 12 Month Commits | All Time Commits | Language |
|---|---|---|---|
| cesarsouza | 331 | 2126 | C# |
| AlexJCross | 9 | 73 | XML |
| Anders Gusuafsson | 0 | 41 | XML |
| Alex Risman | 0 | 24 | C# |

*(缺少图片的完善，以及Power And Interest的分析)*

---
# Context View
Next we will introduce the context view of Accord.NET Framework which defines the relationships, dependencies, and interactions between the system and its environment. 

This desribe what the system does and does not do; where the boundaries are between it and the outside world; and how the system interacts with other systems, orgnizations, add people across these boundaries.

## System Scope
According to the introduction of Accord.NET's official website, Accord.NET Framework defined as a ".NET machine learning framework combined with audio and image processing libraries completely written in C#." 

"Machine learning made in a minute.", The website of Accord.NET also describe the application direction and design concept this system.
> It is a complete framework for building production-grade computer vision, computer audition,     signal processing and statistics applications even for commercial use. 

And we can see that it has sufficient libaries which can solve related problems about machine learning:


>- Scientific Computing<br>
    - Accord.Math<br>
    - Accord.Statistics<br>
    - Accord.MachineLearning<br>
    - Accord.Neuro<br>
    
>- Signal and Image Processing<br>
    - Accord.Imaging<br>
    - Accord.Audio<br>
    - Accord.Vision<br>

>- Support libraries<br>
    - Accord.Controls<br>
    - Accord.Controls.Imaging<br>
    - Accord.Controls.Audio<br>
    - Accord.Controls.Vision<br>

## External Entities
The relationship between Accord.NET Framwork and outside envoriment can be showed in Figure 3.<br>
![Accord.NET](https://raw.githubusercontent.com/ZZAster/framework/development/A-软体-第七组/Picture-framework/context_view.png)<br>
*Figure3 Context View*

As the picture showed, external entities can be divided in groups as follows:

### Competitors

As a machine learning framework specifically developed for .NET, Accord.NET has many competitors in the field. For example, Tensorflow is a powerful machine learning framework developed by Google and .NET Framwork application can install Tensorflowsharp through NuGet to complete the call to function of tensorflow framework. And there also are other competitors such as paddlepaddle of baidu, EmguCV and so on.

### Developing languages and Software Platform

- Languages: C#
- Platform : Accord.NET can be installed on Linux and OS X with Mono, and in windows, it can runs through Visual Studio which is the main IDE of Accord.NET.

### Building and Dependencies
We can see from above that Accord.NET can be building with VS and Mono on three mainly Operation Systems(Windows, Linux and OS X). There we only shows the dependencies of VS 2017, Linux and OS X:

- With Visual Studio 2017
>Please download and install the following dependencies:<br>
[T4 Toolbox for Visual Studio 2017](https://github.com/hagronnestad/T4Toolbox/releases/tag/vs2017-b1)<br>
[Sandcastle Help File Builder (with VS2017 extension)](https://github.com/EWSoftware/SHFB/releases)<br>
[NUnit 3 Test Adapter](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.NUnit3TestAdapter)<br>
[Visual C++ Redistributable for Visual Studio 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48145&751be11f-ede8-5a0c-058c-2ee190a24fa6) (both x64 and x86)

- With Mono in Linux
```bash
# Install Mono
sudo apt-get install mono-complete monodevelop monodevelop-nunit git autoconf make

# Clone the repository
git clone https://github.com/accord-net/framework.git

# Enter the directory
cd framework

# Build the framework solution using Mono
./autogen.sh
make build
make samples
make test
```

- With Mono in OS X

```bash
# Install Mono
brew update
brew cask install mono-mdk pkg-config automake

# Clone the repository
git clone https://github.com/accord-net/framework.git

# Enter the directory
cd framework

# Set some environment variables with OSX-specific paths
export PKG_CONFIG_PATH=/Library/Frameworks/Mono.framework/Versions/Current/lib/pkgconfig/
export MONO=/Library/Frameworks/Mono.framework/Versions/Current/bin/mono
export XBUILD=/Library/Frameworks/Mono.framework/Versions/Current/bin/xbuild

# Build the framework solution using Mono
./autogen.sh
make build
make samples
make test
```
### Other Entities
- Version Control: GitHub
- Testing tools: Almost all [testing applications](https://github.com/ZZAster/framework/tree/development/Tools) are runs on Visual Studio written in C#.
- How to call it: For the reason of Accod.NET being developed completely by C#, it is mainly called by C# programming project. But Accord.NET also support other programming languages compitable with .NET such as VB.NET and C++/CTL.


---

---
# References
1. Wikipedia - Accord.NET.<br>

2. Accord.NET Framework's Official Website.<br>
