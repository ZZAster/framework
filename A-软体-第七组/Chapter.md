# Accord.NET - A Machine Learning Framework
![Accord.NET](https://raw.githubusercontent.com/ZZAster/framework/development/A-软体-第七组/Picture-framework/accord-logo.png)

---
# Absract
The Accord.NET Framework is a .NET machine learning framework created to extended the features of original AForge.NET library. It combines with audio and image processing libraries which was completely written by C#. So Accord.NET can be used as a complete framework for compute vision, compute audition, signal processing and statistics applications for .NET users.<br>

This chapter aims to provide several different point of views to this software's architecture. At first, an outside views will be given to analys and introduce the basical information of Accord.NET. Second, we will give a closer look at the code module underlying architecure. Last, we will analys deeply the existing problem or technical debts and try to give some useful solutions.<br>
*有待进行修改以及添加引用*

---
# Table of Contents

---
# Introduction
Nowadays, machine learning and data analysis are becoming the hottest and most promising areas of programming. When dealing with various issues related to machine learning and data analysis, programmers need to use many complex algorithms to solve the problem. It’s quite cumbersome to write your own algorithmic functions, and the .NET framework developed by Microsoft at the time lacked such a library that supports multiple algorithms. Thus Andrew Kirillov developed AForge.NET which is a computer vision and artificial intelligence library completely written by C# for .NET Framework and the source code and binaries of the project are available under the terms of the Lesser GPL and the GPL (GNU General Public License). <br>

And then, on April 1, 2012, Andrew Kirillov announced the end of the public support for the library, temporarily closing the discussion forums. The last release of the AForge.NET Framework was made available on July 17, 2013. However, since its release 3.0 in 2015, the Accord.NET project started to incorporate most of the original AForge.NET source code in its codebase, continuing its support and development under the Accord.NET name.<br>

The Accord.NET is a framework for scientific computing in .NET which is extended from AForge.NET. The framework is comprised of multiple librares encompassing a wide range of scientific computing applications, such as statistical data processing, machine learning, pattern recognition, including but not limited to, computer vision and computer audition. The framework offers a large number of probability distributions, hypothesis tests, kernel functions and support for most popular performance measurements techniques. It support many useful libraries such as Accord.Math, Accord.Imaging, Accord.Audio and so on for .NET machine learning developer.<br>

This chapter aims at analys Accord.NET Framework as a software system. Thus, /* the summary of the entire article structure *(有待进行修改补充以及添加引用)* */

---
# Stakeholders
As a a project home on GitHub, Accord.NET has many stakeholders. The role of Accord.NET is mainly reflected in providing libraries for .NET applications. The libraries are below:  

* Scientific computing  
* Signal and image processing  
* Support libraries  

*Table1:The StakeHolders of Accord.NET*  

| Stakeholder class | Description |
|---|---|
| Acquirers | The original author is César Roberto de Souza. The offical site of this software accepts donations from users. |
| Communicators | The team of the software has a mailbox, feedback@accord-framework.net to get the feedback from users. The developers of the team are also the communicators. Besides, users can talk with each others on the community. |
| Developer | There are 11 active contributors on GitHub in the past 12 months. This project has a relatively large team, in the top 10% of all project teams on Open Hub. And so far, there are 72 contributors in the history of the software. |
| Tester | All the bugs can be reported by posted on the community or mailed to the team. The menbers of the team or others will pick up the problem. |
| Users | Accord.NET has many kinds of users. Take professionals for an example, there are many essays published in the world. It's a very famous project. And it can be used to build other software. |
| Maintainers | The application is maintained by the developing team with decreasing Y-O-Y commits. The rule and standard will be confirmed by the team. |
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
