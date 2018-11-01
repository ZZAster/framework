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

Accord.NET is a open source project. It isn't acquired by anyone, so it will receive the donations from the society. As the managers says in the offical site, the donations will be used to develop the project and employ onthers to improve it.  

*Table1:The StakeHolders of Accord.NET*  

| Stakeholder class | Description |
|---|---|
| Communicators | The team of the software has a mailbox, feedback@accord-framework.net to get the feedback from users. The developers of the team are also the communicators. Besides, users can talk with each others on the community. |
| Developer | There are 11 active contributors on GitHub in the past 12 months. This project has a relatively large team, in the top 10% of all project teams on Open Hub. And so far, there are 72 contributors in the history of the software. |
| Tester | All the bugs can be reported by posted on the community or mailed to the team. The menbers of the team or others will pick up the problem. |
| Users | Accord.NET has many kinds of users. Take professionals for an example, there are many essays published in the world. It's a very famous project. And it can be used to build other software. |
| Maintainers | The rule and standard will be confirmed by the team. The application is maintained by the developing team with decreasing Y-O-Y commits. Over the last twelve months, it has seen a substantial decrease in development activity.|
| Competitors | There are some similar project, such as SHOUGUN, CVWS.NET, Emgu CV and so on. |  

Anyone can join the developing team to improve the project. And they can exchange their ideas with others in the community. And in table 2 we can see the most active conrtibutor in the past 12 months and the one during all time.   

![stakeholder](https://raw.githubusercontent.com/ZZAster/framework/development/A-软体-第七组/Picture-framework/stakeholder.png)<br>

*Table	2:	Most	active	contributors	in	trems	of	number	of	commits.*

| Contributor | 12 Month Commits | All Time Commits | Language |
|---|---|---|---|
| cesarsouza | 331 | 2126 | C# |
| AlexJCross | 9 | 73 | XML |
| Anders Gusuafsson | 0 | 41 | XML |
| Alex Risman | 0 | 24 | C# |  

The team uses C# as the major language during developing Accord.NET. The reason is that C# is powerful and easy for anyone who get the hang of C++, C and Java. It simplifies C++ and also provides many powerful functions. Besides, C# is a language developed for.NET Framework. 

# Power-Interest Grid
We have created a power vs interest grid to show the stakeholder based on the interest and power. This project is mostly built by the of Accord.NET framework. Their manager is "cesarsouza". So the team has the most power and interest. 
This project uses the visual studio and its expanding tool .Nuget. So they have the power but less interest.
This project is open source and many contributors on github can see it and help to develop it. Also they can only use it to develop.
And this project also have competitors who may have more interest on it but have less power.
![powerVSinterest](https://raw.githubusercontent.com/ZZAster/framework/development/A-软体-第七组/Picture-framework/powerVSinterest.png)<br>

---
# Context View
Next we will introduce the context view of Accord.NET Framework which defines the relationships, dependencies, and interactions between the system and its environment. 

This desribe what the system does and does not do; where the boundaries are between it and the outside world; and how the system interacts with other systems, orgnizations, add people across these boundaries.

## System Scope
According to the introduction of Accord.NET's official website, Accord.NET Framework defined as a ".NET machine learning framework combined with audio and image processing libraries completely written in C#." 

"Machine learning made in a minute.", Accord.NET describes the application direction and design concept of their system on the website, and briefly describes some functions and uses that the software system can provide on the initial interface of its official website.
> It is a complete framework for building production-grade computer vision, computer audition,     signal processing and statistics applications even for commercial use. 

And as you can see from the official website's instructions and introductions, Accord.NET provides many powerful and useful libraries for developers on the .NET platform for machine learning and numerical computing. These libraries can be roughly divided into three modules. Below we show some of the library files in each module:


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
![Accord.NET](https://github.com/ZZAster/framework/blob/development/A-%E8%BD%AF%E4%BD%93-%E7%AC%AC%E4%B8%83%E7%BB%84/Picture-framework/context_view.png)<br>
*Figure3 Context View*

As the picture showed, external entities can be divided in groups as follows:

### Competitors

As a machine learning framework developed specifically for the .NET platform, Accord.NET itself is used to make up for the development language on the .NET platform, especially for C#, which lacks the usable library files for numerical computing and machine learning.

So we can see that although there are already many frameworks for machine learning, such as AForge.NET and Emgu.CV, there are no competitors on the same platform Accord.NET. As a new framework, it inherits many of the advantages of the products described above and has more complete and powerful features.

But when we compare them across all the platform, we can see that there are many machine learning frameworks that are equally complete and simpler to use. These frameworks usually rely on languages that are more suitable for numerical calculations, such as Python. Tensorflow, developed by Google, is such a framework that most deep learning engineers are happy to develop using tensorflow and python. More importantly, Tensorflow has developed Tensorflowsharp, which is specifically applied to projects developed by C#.

### Developing languages & Software Platform
Accord.NET was developed as a C# package. Although it can be imported by other languages through the .NET platform, it is still a framework developed entirely by C#.

- Developing Languages: C#
- Platform : For the operating system, Accord.NET supports the three most popular operating systems, Windows, Linux and OS X. In the integrated development environment, it is mainly called by projects built using Visual Studio.

### Building & Dependencies
We can see from above that Accord.NET can be building with VS and Mono on three mainly Operation Systems(Windows, Linux and OS X). There we only shows the dependencies for building it on VS 2017, and on UNIX-like operating systems, such as Linux and OS X, Accord.NET needs to be installed by using Mono, a free and open source project that creates a series of .NET tools including C# compilers and common language architectures which can run on a system other than windows, Mono will automatically import the external dependencies required by the framework during the installation process:

**Building**

- With Visual Studio 2017
>Please download and install the following dependencies:<br>
[T4 Toolbox for Visual Studio 2017](https://github.com/hagronnestad/T4Toolbox/releases/tag/vs2017-b1)<br>
[Sandcastle Help File Builder (with VS2017 extension)](https://github.com/EWSoftware/SHFB/releases)<br>
[NUnit 3 Test Adapter](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.NUnit3TestAdapter)<br>
[Visual C++ Redistributable for Visual Studio 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48145&751be11f-ede8-5a0c-058c-2ee190a24fa6) (both x64 and x86)

- With Mono in Linux and OS X
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

**Dependencies**

In addition to the dependencies required for installation, most of the dependencies are external standard libraries such as GhostAPI, JSON, and NUint, as well as libraries for handling audio and image formats, such as ffmpeg and ZedGraph.

### Version Control & Community & Testing tools
In the process of Accord.NET development, there are many platforms that play a very important role. As an open source software, Github is used as a platform for version control and community communication. The core development team develops functions through this platform, and individual users can maintain the software by submitting revision comments.

Communities can also contribute to this project by other means, such as email and supplementing Wikipedia. Developers also offer electronic payments and OpenHub to get help from some individual users.

### Others
Follow the advice given by the teacher during the interim report，We studied which languages the Accord.NET framework can be called by, and then found out that for the reason of Accod.NET being developed completely by C#, it is mainly called by C# programming project, but it also support other programming languages compitable with .NET such as VB.NET and C++/CTL.


---
# Evolution	perspective  

Compared with the first release, Accord.NET has improved much more. And there are totally 15 releases in the Github. It starts from 07-09-2013 to 22-10-2017. As for the version is from 2.10 to 3.8.0. The earlier releases can only be found in the releases notes. The real initial release is on 20-05-2010.  
The first release is Accord.NET Framework 2.0.0. It's based on the AForge.NET. What it does is provide a series of fundamental libraries, determining the ooriginal form of the project. Between 2.0.0 and 3.0.0, there are several releases used to update the libraries by adding new features and fix bugs. But the developing team concentrates more attention on adding new features.  
Take 2.14 for an example, the release only fixes a bug, and add many new features like Taylor series functions and dissimilarity functions. But sometime it will also report some issue and fix them in the next release.  
On 16-8-2015 the Accord.NET 3.0.0 is released. The most important update is that Accord.NET merge with AForge.NET.This release marks a milestone in the Accord.NET Framework. Starting from this release, the AForge.NET Framework has been incorporated directly in the project. In addition, it provides most of the AForge.NET namespaces unchanged and help projects use the AForge.NET framework to make the transition to Accord.NET more easily. This means that this specific version of Accord.NET Framework can be used as drop-in replacement in any project currently using the AForge.NET Framework and that is willing to upgrade to Accord.NET sometime in the future. It's really a good news for the users of AForge.NET.  
According to the recent releases, we can see that the team focus on MachineLearning. These releases updates many algorithms like K-Medoids (PAM) and Voronoi Iteration clustering algorithms. In addition, they add support for OS X targetting NET Standard 1.4, fix target framework versions and add some new namespace.   
Furthermore, the project is near completion form the latest release. It adds many example for the classes. And The libsonly script is now in RAR4 format instead of RAR5 so they will not be listed as corrupted files by Linux/MacOSX decompressors

---

# Functional View

This part will show the functional view of the Accord.NET. 

The Functional view of a system defines the architectural elements that deliver the system’s functionality. The view documents the system’s functional structure-including the key functional elements, their responsibilities, the interfaces they expose, and the interactions between them. Taken together, this demonstrates how the system will perform the functions required of it.

##  Functional Capabilities

The Accord.NET Framework is a programming aid software. The Accord.NET Framework is a C# framework that extends the new  [AForge.NET Framework](https://en.wikipedia.org/wiki/AForge.NET) with new tools and libraries.  Accord.NET implements tools and features that are still not available in AForge.NET, such as Kernel Support Vector Machines, Discriminative and Projective Analysis, Hidden Markov Models, new Neural networks learning algorithms, new imaging filters, and other useful methods and tools. 

> *  [AForge.NET](https://en.wikipedia.org/wiki/AForge.NET) is a computer vision and artificial intelligence library. It implements a number of genetic, fuzzy logic and machine learning algorithms with several architectures of artificial neural networks with corresponding training algorithms. 
> * [Accord.NET](https://en.wikipedia.org/wiki/Accord.NET) is a collection of libraries for scientific computing, including numerical linear algebra, numerical optimization, statistics, artificial neural networks, machine learning, signal processing and computer vision and support libraries (such as graph plotting and visualization).

The framework comprises a set of libraries that are available in source code as well as via executable installers and [NuGet](https://en.wikipedia.org/wiki/NuGet) packages.

## External Interfaces Layer
Accord .NET uses a lot of auxiliary softwares to help implementing its functions, for example, when we want to access database, we can use the AccessDatabaseEngine of Microsoft, and when we need to do some operations on video, we can use FFmpeg and so on. The followings are external components which can be found in the fold "External" of the Accord.NET Framework.
> * **ace** - AccessDatabaseEngine, is Microsoft's access database access engine, and some software that calls access to the database requires this engine to run.
> * **ffmpeg** - FFmpeg is a free multimedia framework that can run video, conversion, and streaming functions in multiple formats of audio and video, giving users access to almost all video formats, including mkv, flv, and mov. VLC Media Player and Google Chrome browsers are already supported.has very powerful features including video capture, video format conversion, video capture, watermarking, etc.
> * **GhostAPI** - Ghost is built on top of a RESTful JSON API. This API is used for all data access inside of the Ghost software itself, meaning the API is the heart of the software, not an afterthought or additional layer. It is the API provided by Lego for communication with RCX brick.
> * **Json.NET** - Json.NET is a popular high-performance JSON framework for .NET. 
> * **libfreenect** - Driver for Kinect for Windows v2 (K4W2) devices (release and developer preview). And libfreenect2 does not do anything for either Kinect for Windows v1 or Kinect for Xbox 360 sensors. Use libfreenect1 for those sensors.
> * **msinttypes** -  this allows compiling C99 compliant projects in MSVC. The C99 standard defines "stdint.h", "inttypes.h" for uniform cross-platform data definitions. Unfortunately, VC, BCB and other compilers have poor compatibility with C99.
> * **Nunit** - NUnit is a unit testing framework specifically written for .NET. NUnit is the fourth major product of the xUnit family, written entirely in C# and is written to take advantage of many of the features of .NET. Such as reflection, customer attributes, etc. The most important point is that it works for all .NET languages.
> * **OpenKinect** - It is an open community of people interested in making use of the amazing Xbox Kinect hardware with our PCs and other devices. We are working on free, open source libraries that will enable the Kinect to be used with Windows, Linux, and Mac. Our primary focus is currently the **libfreenect** software.
> * **SharpDX** - SharpDX is an open-source **managed .NET wrapper** of the [DirectX API](https://msdn.microsoft.com/en-us/library/windows/desktop/ee663274%28v=vs.85%29.aspx).
> * **SharpZipLib** - SharpZipLib (#ziplib, formerly NZipLib) is a compression library for Zip, GZip, BZip2, and Tar written entirely in C# for .NET. It is implemented as an assembly (installable in the GAC), and thus can easily be incorporated into other projects (in any .NET language)
> * **TeRK** - The TeRK.dll is a .NET assembly, which contains built of TeRK C# types generated from TeRK ICE definition. The TeRK.dll requires Ice.dll and Glacier2.dll, which are part of ICE package.
> * **ZedGraph** - ZedGraph is an open source .NET charting library, all code is developed in C#. It can create 2D linear and column charts with arbitrary data sets.

## Dependency Layer 

The framework is comprised by the set of libraries and sample applications, which demonstrate their features, and the Accord.NET framework implement it's function dependent on these libraries.

![Structure](https://raw.githubusercontent.com/ZZAster/framework/development/A-%E8%BD%AF%E4%BD%93-%E7%AC%AC%E4%B8%83%E7%BB%84/Picture-framework/Structure.png)

> * **Accord.Math** - Contains a matrix extension library, along with a suite of numerical matrix decomposition methods, numerical optimization algorithms for constrained and unconstrained problems, special functions and other tools for scientific applications.
> * **Accord.Statistics** - Contains probability distributions, hypothesis testing, statistical models and methods such as Linear and Logistic regression, Hidden Markov Models, (Hidden) Conditional Random Fields, Principal Component Analysis, Partial Least Squares, Discriminant Analysis, Kernel methods and many other related techniques.
> * **Accord.MachineLearning** - Support Vector Machines, Decision Trees, Naive Bayesian models, K-means, Gaussian Mixture models and general algorithms such as Ransac, Cross-validation and Grid-Search for machine-learning applications.
> * **Accord.Neuro** - Neural learning algorithms such as Levenberg-Marquardt, Parallel Resilient Backpropagation, the Nguyen-Widrow initialization algorithm, Deep Belief Networks and Restrictured Boltzmann Machines, and many other neural network related items.

> * **Accord.Controls** - Histograms, scatterplots and tabular data viewers for scientific applications.
> * **Accord.Controls.Imaging** - Windows Forms controls to show and handle images. Contains a convenient ImageBox control which mimics the traditional MessageBox for quickly displaying or inspecting images.
> * **Accord.Controls.Audio** - Windows Forms controls to display waveforms and audio-related information.
> * **Accord.Controls.Vision** - Windows Forms components and controls to track head, face and hand movements and other computer vision related tasks.

> - **Accord.Controls** - Histograms, scatterplots and tabular data viewers for scientific applications.
> - **Accord.Controls.Imaging** - Windows Forms controls to show and handle images. Contains a convenient ImageBox control which mimics the traditional MessageBox for quickly displaying or inspecting images.
> - **Accord.Controls.Audio** - Windows Forms controls to display waveforms and audio-related information.
> - **Accord.Controls.Vision** - Windows Forms components and controls to track head, face and hand movements and other computer vision related tasks.

## Logical Layer

In order to realize the functions, Accord.NET has so many algorithms.The main functional algorithms included in the Accord.NET framework are described below by its category.

|     Category     | algorithms                                                   |
| :--------------: | ------------------------------------------------------------ |
|  Classification  | SVM、Logistic Regression、Decision Trees、 Neural Networks、Deep Learning、Deep Neural Networks、Levenberg-Marquardt with Bayesian Regularization、Restricted Boltzmann Machines、Sequence classification 、Hidden Markov Classifiers and Hidden Conditional Random Fields. |
|    Regression    | Multiple linear regression、Multivariate linear regression、polynomial regression 、logarithmic regression、Logistic regression、multinomial logistic regression(softmax) and generalized linear models、L2-regularized L2-loss logistic regression , L2-regularized logistic regression , L1-regularized logistic regression , L2-regularized logistic regression in the dual form and regression support vector machines |
|    Clustering    | K-Means、K-Modes、Mean-Shift、Gaussian Mixture Models、Binary Split、Deep Belief Networks、 Restricted Boltzmann Machines.  Clustering algorithms can be applied in arbitrary data, including images, data tables, videos and audio. |
|   Distribution   | Parametric and non-parametric estimation of more than 40 distributions. Univariate distributions such as Normal, Cauchy,  Hypergeometric , Poisson , Bernoulli , and specialized  distributions such as the Kolmogorov-Smirnov , Nakagami , Weibull, and the Von-Mises  distributions. Multivariate distributions such as the multivariate Normal, Multinomial, Independent , Joint and Mixture distributions. |
| Hypothesis Tests | More than 35 statistical hypothesis tests , including one way and two-way ANOVA tests , non-parametric tests such as the Kolmogorov-Smirnov test and the Sign Test for the Median , contingency table tests such as the Kappa test , with variations for multiple tables , as well as the Bhapkar and Bowker tests; and the more traditional Chi-Square , Z , F , T and Wald tests . |
|  Kernel Methods  | Kernel Support Vector Machines , Multi-class and Multi-label machines , Sequential Minimal Optimization , Least-Squares Learning , probabilistic learning , including special methods for linear machines such as LIBLINEAR's methods for Linear Coordinate Descent , Linear Newton Method , Probabilistic Coordinate Descent , Probabilistic Coordinate Descent in the Dual , Probabilistic Newton Method for L1 and L2 machines in both the dual and primal formulations. |
|     Imaging      | Interest and feature point detectors such as Harris, FREAK , SURF , and FAST . Grey-level Co-occurrence matrices , Border following , Bag-of-Visual-Words (BoW) , RANSAC-based homography estimation , integral images , haralick textural feature extraction , and dense descriptors such as histogram of oriented gradients (HOG) and Local Binary Pattern (LBP) . Several image filters for image processing applications such as difference of Gaussians , Gabor , Niblack and Sauvola thresholding . |
| Audio and Signal   | Load, parse, save, filter and transform audio signals, such as applying audio processing filters in both space and frequency domain . WAV files , audio capture , time-domain filters such as envelope , high-pass , low-pass , wave rectification filters. Frequency-domain operators such as differential rectification filter and comb filter with Dirac's delta functions . Signal generators for Cosine , Impulse , Square signals.  |
|      Vision      | Real-time face detection and tracking , as well as general methods for detecting, tracking and transforming objects in image streams. Contains cascade definitions, Camshift and Dynamic Template Matching trackers. Includes pre-created  classifiers for human  faces and some facial features such as noses. |

---
# References
1. Wikipedia - Accord.NET.<br>

2. Accord.NET Framework's Official Website.<br>
