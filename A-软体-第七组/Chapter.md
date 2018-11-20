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
# Functional View

This part will show the functional view of the Accord.NET. 

The Functional view of a system defines the architectural elements that deliver the system’s functionality. The view documents the system’s functional structure-including the key functional elements, their responsibilities, the interfaces they expose, and the interactions between them. Taken together, this demonstrates how the system will perform the functions required of it. The Following is an introduction to the functional capabilities, external interfaces, dependency layer and logical layer of the framework, among which functional capabilities show the functions of Accord.NET, external interfaces layer shows the auxiliary external software, and the dependency layer shows the library it used to implement its functions, and the logical layer shows the algorithms.

##  Functional Capabilities

The Accord.NET Framework is a programming aid software. And it is a C# framework that extends the  AForge.NET Framework with new tools and libraries.  Accord.NET implements tools and features that are still not available in AForge.NET, such as Kernel Support Vector Machines, Discriminative and Projective Analysis, Hidden Markov Models, new Neural networks learning algorithms, new imaging filters, and other useful methods and tools. 

> *  [AForge.NET](https://en.wikipedia.org/wiki/AForge.NET) is a computer vision and artificial intelligence library. It implements a number of genetic, fuzzy logic and machine learning algorithms with several architectures of artificial neural networks with corresponding training algorithms. 
> * [Accord.NET](https://en.wikipedia.org/wiki/Accord.NET) is a collection of libraries for scientific computing, including numerical linear algebra, numerical optimization, statistics, artificial neural networks, machine learning, signal processing and computer vision and support libraries (such as graph plotting and visualization).

The framework comprises a set of libraries that are available in source code as well as via executable installers and [NuGet](https://en.wikipedia.org/wiki/NuGet) packages.

## External Interfaces Layer

Accord.NET uses a lot of auxiliary software to help implementing its functions, for example, when we want to access database, we can use the AccessDatabaseEngine of Microsoft, and when we need to do some operations on video, we can use FFmpeg and so on.  The following is the external software we may need when using the Accord.NET framework.

> * **ace** - AccessDatabaseEngine, is Microsoft's access database access engine, and some software that calls access to the database requires this engine to run.
> * **ffmpeg** -  A complete, cross-platform solution to record, convert and stream audio and video. Convertng video and audio is very easy with FFmpeg.
> * **GhostAPI** - Ghost is built on top of a RESTful JSON API. This API is used for all data access inside of the Ghost software itself, meaning the API is the heart of the software, not an afterthought or additional layer. It is the API provided by Lego for communication with RCX brick.
> * **Json.NET** - Json.NET is a popular high-performance JSON framework for .NET. 
> * **libfreenect** - Driver for Kinect for Windows v2 (K4W2) devices (release and developer preview). And libfreenect2 does not do anything for either Kinect for Windows v1 or Kinect for Xbox 360 sensors. Use libfreenect1 for those sensors.
> * **msinttypes** -  This allows compiling projects which meet the criteria of C99 in MSVC. (The C99 standard defines "stdint.h", "inttypes.h" for uniform cross-platform data definitions. Unfortunately, VC, BCB and other compilers have poor compatibility with C99.)
> * **Nunit** - NUnit is a unit testing framework specifically written for .NET.  NUnit is the fourth major product of the xUnit family, written entirely in C#. And it is written to take advantage of many features of .NET, such as reflection, customer attributes, etc. The most important point is that it works for all .NET languages.
> * **OpenKinect** - It is an open community of people interested in making use of the amazing Xbox Kinect hardware with our PCs and other devices. We are working on free, open source libraries that will enable the Kinect to be used with Windows, Linux, and Mac. Our primary focus is currently the **libfreenect** software.
> * **SharpDX** - SharpDX is an open-source managed .NET wrapper of the [DirectX API](https://msdn.microsoft.com/en-us/library/windows/desktop/ee663274%28v=vs.85%29.aspx).
> * **SharpZipLib** - SharpZipLib (#ziplib, formerly NZipLib) is a compression library for Zip, GZip, BZip2, and Tar, written entirely in C# for .NET. It is implemented as an assembly (installable in the GAC), and thus can easily be incorporated into other projects (in any .NET language)
> * **TeRK** - The TeRK.dll is a .NET assembly. The TeRK.dll requires Ice.dll and Glacier2.dll, which are part of ICE package.
> * **ZedGraph** - ZedGraph is an open-source .NET charting library, of which all code is developed in C#. It can create 2D linear and cylindrical graphs with arbitrary data sets.

## Dependency Layer 

The framework is comprised by the set of libraries and sample applications, which demonstrate their features, and the Accord.NET framework implement it's function dependent on these libraries.

![Structure](https://raw.githubusercontent.com/ZZAster/framework/development/A-%E8%BD%AF%E4%BD%93-%E7%AC%AC%E4%B8%83%E7%BB%84/Picture-framework/Structure.png)

*Graph: the internal structure of Accord.NET.*

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
The algorithms can be divided into three types:

* Supervised learning：Classification, Regression, Kernel Methods

* Unsupervised learning：Clustering

* Semi-Supervised Learning: Imaging, Audio and Signal, Vision

*The following is the specific algorithms each type contains:*

|     Category     | algorithms                                                   |
| :--------------: | ------------------------------------------------------------ |
|  Classification  | SVM, Logistic Regression, Decision Trees,  Neural Networks, Deep Learning, Deep Neural Networks, Levenberg-Marquardt with Bayesian Regularization, Restricted Boltzmann Machines, Sequence classification, Hidden Markov Classifiers and Hidden Conditional Random Fields. |
|    Regression    | Multiple linear regression, Multivariate linear regression, polynomial regression, logarithmic regression, logistic regression, multinomial logistic regression(softmax) and generalized linear models, L2-regularized L2-loss logistic regression, L2-regularized logistic regression, L1-regularized logistic regression, L2-regularized logistic regression in the dual form and regression support vector machines. |
|    Clustering    | K-Means, K-Modes, Mean-Shift, Gaussian Mixture Models, Binary Split, Deep Belief Networks, Restricted Boltzmann Machines. Clustering algorithms can be applied in arbitrary data, including images, data tables, videos and audio. |
|   Distribution   | Parametric and non-parametric estimation of more than 40 distributions. Univariate distributions such as Normal, Cauchy,  Hypergeometric , Poisson , Bernoulli , and specialized  distributions such as the Kolmogorov-Smirnov , Nakagami , Weibull, and the Von-Mises  distributions. Multivariate distributions such as the multivariate Normal, Multinomial, Independent , Joint and Mixture distributions. |
| Hypothesis Tests | More than 35 statistical hypothesis tests , including one way and two-way ANOVA tests, non-parametric tests such as the Kolmogorov-Smirnov test and the Sign Test for the Median , contingency table tests such as the Kappa test , with variations for multiple tables, as well as the Bhapkar and Bowker tests; and the more traditional Chi-Square, Z , F , T and Wald tests. |
|  Kernel Methods  | Kernel Support Vector Machines , Multi-class and Multi-label machines , Sequential Minimal Optimization , Least-Squares Learning , probabilistic learning , including special methods for linear machines such as LIBLINEAR's methods for Linear Coordinate Descent , Linear Newton Method , Probabilistic Coordinate Descent, Probabilistic Coordinate Descent in the Dual , Probabilistic Newton Method for L1 and L2 machines in both the dual and primal formulations. |
|     Imaging      | Interest and feature point detectors such as Harris, FREAK , SURF , and FAST . Grey-level Co-occurrence matrices , Border following , Bag-of-Visual-Words (BoW) , RANSAC-based homography estimation , integral images , haralick textural feature extraction , and dense descriptors such as histogram of oriented gradients (HOG) and Local Binary Pattern (LBP) . Several image filters for image processing applications such as difference of Gaussians , Gabor , Niblack and Sauvola thresholding . |
| Audio and Signal   | Load, parse, save, filter and transform audio signals, such as applying audio processing filters in both space and frequency domain . WAV files , audio capture , time-domain filters such as envelope , high-pass , low-pass , wave rectification filters. Frequency-domain operators such as differential rectification filter and comb filter with Dirac's delta functions . Signal generators for Cosine , Impulse , Square signals. g |
|      Vision      | Real-time face detection and tracking , as well as general methods for detecting, tracking and transforming objects in image streams. Contains cascade definitions, Camshift and Dynamic Template Matching trackers. Includes pre-created  classifiers for human  faces and some facial features such as noses. |
## Effect of using the Accord.NET
Let's see some application effects of using Accord.NET:

1.Spectrum analyzer (Fourier)

The Fourier sample application shows how to capture sounds from a capture device (such as a microphone jack) using the Accord.NET Framework. The signal can be analyzed, processed and transformed using the framework's Fourier and Hilbert transform functions. 

![](https://raw.githubusercontent.com/ZZAster/framework/development/A-%E8%BD%AF%E4%BD%93-%E7%AC%AC%E4%B8%83%E7%BB%84/Picture-framework/case1.png)

2Clustering (Gaussian Mixture Models)

This sample application shows how to use  to Gaussian Mixture Models perform clustering and classification using soft-decision margins.

![](https://raw.githubusercontent.com/ZZAster/framework/development/A-%E8%BD%AF%E4%BD%93-%E7%AC%AC%E4%B8%83%E7%BB%84/Picture-framework/case2.png)

3.Face Detection (Haar object detector)

Face detection using the Face detection based in Haar-like rectangular features method often known as the Viola-Jones method .

![](https://raw.githubusercontent.com/ZZAster/framework/development/A-%E8%BD%AF%E4%BD%93-%E7%AC%AC%E4%B8%83%E7%BB%84/Picture-framework/case3.png)


---
# Development View

We will now take a closer look to the architecture that support the Accord.NET framework's development progress. At first, we will describe the common design principle of this framework. Then we will analyze the code organization and module structure model.

## Common Design Models
This section describe the standlarize and common design that are used in the development of Accord.NET framework.

### Contributing
Developers should send pull requests against the development branch instead of master. The master branch is reserved to contain only the latest official public release of the framework.

### Please stick to C# 4.0
If possible, when contributing code to the framework, please avoid using C# language features from above C# 4.0. There are at least two reasons for this restriction:

 1. **Mono:** To keep compatibility with the most widespread versions of Mono (4.x). If you take a look at our Travis-CI builds, you might see that the builds are actually done and run using Mono, so using any language feature that is not supported there will cause a failing build;
 1. **Unity:** Some language features might not be accessible when targeting .NET 3.5, which for a long time has been the only .NET Framework version that could be run from inside [Unity](https://unity3d.com).
 
 ### Code formatting
Please use the same code formatting style as the default format offered by Visual Studio. This is the style that Visual Studio will format your code with when pressing Ctrl+E, D while in the editor.

### Contributor Covenant Code of Conduct
Accord.NET framework's Code of Conduct is adapted from the Contributor Covenant, version 1.4, which is available at contributor-covenant's official site.

## Codeline Organization
The project's code functionality can be divided into four larfe section by their rules which are showed in Figure 9.

![Codeline Organization](picture-framework/code-organization.png)  
_**Figure 9.** Codeline Organization of Accord.NET Framework_

### Funcitonality
The functionality section contains the various components that implement the project's functionality. The External folder contains the third-party software interfaces that are used for supporting the code of project functions. And the Source folder contains the code implementation of the algorithm library provided by the Accord.NET Framework, which is the source code for the project.

### Development & Development
The development and deployment section contains the code to supplement, develop, and test the entire project. These codes are primarily used to help improve and maintain Accord.NET without affecting the functionality of the project. The Set Up folder contains the packages that help developers use when installing the project, and the Samples file contains the use cases that testers have written for the various features of Accord.NET. The Tools folder contains code and tools for performance testing and debugging of the project. The Unit Tests folder contains code for the unit testing portion of the project.

### Documents
The documents section contains information about the project. For example, all version updates for the project are documented in the relase note document. CONTRIBUTING and CODE_OF_CONDUCT describe the standard specifications that developers must follow when adding code.

### Miscellanenous
This section contains other files that are not related to the project structure on github.

## Module Structure Model


---
# Deployment View

The deployment view describes the environment into which the system will be deployed. 
## Environment: 
Accord.NET can be used on Windows, Linux and OS X. It is developed by C#, but that not means it can be only used in a C# project. Accord.NET supports all .NET compatible languages such as VB.NET or C++/CLI. It needs a .NET development environment such as Microsoft Visual Studio. And you can use it after downloading and installing the package. Different functions have different package. You can choose what you need. After that, you can use the package in your project.

## Third-party dependencies:

**ACE(AccessDatabaseEngine):** It is Microsoft provided which is used to access the database.

**ffmpeg:** A complete, cross-platform solution to record, convert and stream audio and video.

**GhostAPI:** Ghost is a professional publishing platform. This API is used for all data access inside of the Ghost software itself.

**Json.NET:** Json.NET is a popular high-performance JSON framework for .NET.

**libfreenect:** libfreenect is a library for accessing the Microsoft Kinect USB camera.

**msinttypes:** Msinttypes contains two header files. In some Api such as ffmpeg, the using header file is different from what visual studio provides. So it should used these two files.

**SharpDX:** SharpDX is an open-source managed .NET wrapper of the DirectX API.

**SharpZipLib:** Ziplib is a Zip, GZip, Tar and BZip2 library written for the .NET platform.

**NUnit:** NUnit is a unit-testing framework for all .Net languages.

**TeRK:** The TeRK.dll is a .NET assembly, which contains built of TeRK C# types generated from TeRK ICE definition.

**ZedGraph:** ZedGraph is a class library for creating two-dimensional linear, bar and pie charts of arbitrary data.

## Specialist Knowledge
To use Accord.NET some specialist knowledge is required.
* knowledge of programming in at least one .NET compatible languages.
* knowledge of how to use the IDE of that language and how to import the package.

---
# Evolution	perspective  

Compared with the first release, Accord.NET has improved much more. And there are totally 15 releases in the Github. It starts from 07-09-2013 to 22-10-2017. As for the version is from 2.10 to 3.8.0. The earlier releases can only be found in the releases notes. The real initial release is on 20-05-2010.  

### The initial releases of Accord.NET Framework
The first release is Accord.NET Framework 2.0.0. It's based on the AForge.NET. What it does is provide a series of fundamental libraries, determining the ooriginal form of the project. Between 2.0.0 and 3.0.0, there are several releases used to update the libraries by adding new features and fix bugs. But the developing team concentrates more attention on adding new features.  
Take 2.14.0 for an example, the release only fixes a bug, and add many new features like Taylor series functions and dissimilarity functions. But sometime it will also provide improvements to the documentation and standrad bug-fixing.  

### The important releases of Accord.NET Framework
One of the most important releases is on 30-8-2014. 2.13.1  
replaces SlimDX libraries with SharpDX. That means that the framework can be run into more platforms. That's really a big change. In addition, Two new assemblies have also been created to further accommodate future framework extensions, such as a dedicate matrix format library, and an additional library for math algorithms that are not available under the LGPL.  

### The milestone of Accord.NET Framework  
On 16-8-2015 the Accord.NET 3.0.0 is released. The most important update is that Accord.NET merge with AForge.NET.This release marks a milestone in the Accord.NET Framework. Starting from this release, the AForge.NET Framework has been incorporated directly in the project. In addition, it provides most of the AForge.NET namespaces unchanged and help projects use the AForge.NET framework to make the transition to Accord.NET more easily. This means that this specific version of Accord.NET Framework can be used as drop-in replacement in any project currently using the AForge.NET Framework and that is willing to upgrade to Accord.NET sometime in the future. It's really a good news for the users of AForge.NET.  

### The completion of Accord.NET Framework 
According to the recent releases, we can see that the team focus on MachineLearning. These releases updates many algorithms like K-Medoids (PAM) and Voronoi Iteration clustering algorithms. In addition, they add support for OS X targetting NET Standard 1.4, fix target framework versions and add some new namespace.   
Furthermore, the project is near completion form the latest release. Because they begin making last improvements to documentations, adding supprot for VS2017 and targetting several version of .NET Framework. And they fix some important bugs. At the same time the libsonly script is now in RAR4 format instead of RAR5 so they will not be listed as corrupted files by Linux/MacOSX decompressors.  
![Structure](https://raw.githubusercontent.com/ZZAster/framework/development/A-%E8%BD%AF%E4%BD%93-%E7%AC%AC%E4%B8%83%E7%BB%84/Picture-framework/evolutionPerspective.jpg)
*Figure: The Time Axis of releases*

---
# Performance

As the article mentioned above, **Accord.NET Framework** is a .NET machine learning framework combined with audio and image processing libraries. Therefore we will evaluate its performance from the following aspects: AI, and Imaging. And we will show its strengths and weaknesses compared to his competitors.

## When dealing with AI

At first, lets see some mainstream frameworks and libraries of learning AI.

### 1.TensorFlow -"Computation using data flow graphs for scalable machine learning." 

Language:  C++ or Python

TensorFlow is an open-source software for carrying out numerical computations using data flow graphs. This framework is known for having an architecture that allows computation on any CPU or GPU, be it a desktop, a server, or even a mobile device. This framework is available in the Python programming language. 

**Pros**:

- Uses an easy-to-learn a language (Python).
- Uses computational graph abstraction.
- Availability of TensorBoard for visualization.

**Cons**:

- It's slow, as Python is not the fastest of languages.
- Lack of many pre-trained models.
- Not completely open-source.

### 2.Microsoft CNTK - "An open source-deep learning toolkit." 

Language: C++

We could call this Microsoft's response to Google's TensorFlow.

Microsoft's Computational Network ToolKit is a library that enhances the modularization and the maintenance of separating computation networks, providing learning algorithms and model descriptions. CNTK can take advantage of many servers at the same time in a case where lots of servers are needed for operations. It is said to be close in functionality to Google's TensorFlow; however, it is a bit speedier. 

**Pros**:

- It is very flexible.
- Allows for distributed training.
- Supports C++, C#, Java, and Python.

**Cons**:

- It is implemented in a new language, Network Description Language (NDL).
- Lack of visualizations.

Now lets see the protagonist of our article: Accord.NET

### 3.Accord.NET - Machine learning, computer vision, statistics, and general scientific computing for .NET." Language: C#.

Here is one for the C# programmers.

The Accord.NET framework is a.NET machine learning framework that makes audio and image processing easy.

This framework can efficiently handle numerical optimization, artificial neural networks, and even visualization. Aside from this, Accord.NET is powerful for computer vision and signal processing and also makes for an easy implementation of algorithms. 

**Pros**:

- It has a large and active development team.
- Very well-documented framework.
- Quality visualization.

**Cons**:

- Not a very popular framework.
- Slow compared to TensorFlow.

These libraries discussed above are very efficient and have proven over time to be of high quality. Big companies like Facebook, Google, Yahoo, Apple, and Microsoft make use of some of these libraries for their deep learning and machine learning projects 

## When dealing with imaging

Currently, more well-known and fully functional image processing libraries are OpenCv, EmguCv, AForge.NET/Accord.NET, etc. So the following will compare the performance of these framework.

From the point of view of whether it is easy to use: (it's pure personal opinion)

| Libraries  | easy to use or not | comments                                                     |
| ---------- | ------------------ | ------------------------------------------------------------ |
| OpenCv     | not very good      | Most of OpenCv's features are provided as C-style functions, and a few of them are provided in C++ classes. Note: Version 2.0 packs more features into classes. |
| EmguCv     | ordinary           | EmguCv wraps most of OpenCv's functionality into .net classes, structures, or enumerations. However, the documentation is not complete, you still have to look at the OpenCv documentation.( EmguCv is built on OpenCv). |
| Accord.NET | good               | The pure .net class library is very convenient to use.       |

In order to know the real performance of the Accord.NET, we try to do some experiments but we don't get very effective outcome. Luckily we found an IT freelancer who did the test and get accurate answer. The following is the test and it's result.

These libraries can do a lot of things. We chose the most basic part for performance testing, which is to convert a color image into a grayscale image and then convert the grayscale image into a binary image. Because image processing is used for memory reading and writing and operations (especially matrix operations) most of the time, these two operations are somewhat representative. 

We realized the grayscale and binarization of the image in the following ways: (1) C language calls OpenCv library; (2) C# calls Accord.net library; (3) C# calls EmguCv library; (4) C# The form of P/INVOKE calls the OpenCv function.(The specific code is not displayed here.).

The above four forms were respectively processed 10 times, and the running time was recorded and the maximum and minimum data of each type were removed, and the average value was calculated. 

*The result is as follows (in milliseconds):*

| language | library          | Grayscale | Binarization | rank |
| -------- | ---------------- | --------- | ------------ | ---- |
| C        | OpenCv           | 16.89721  | 7.807766     | 1    |
| C#       | Accord.NET       | 48.9403   | 25.32473     | 4    |
| C#       | EmguCv           | 18.86898  | 13.74628     | 3    |
| C#       | OpenCv(P/Invoke) | 18.68938  | 10.014       | 2    |

We can see that it does not have such a big advantage compared to a specialized image processing library(OpenCv and EmguCv). Accord is applicable and very nice, but still slow in speedy applications than OpenCv. (in some cases e.g. acquiring Image Data, image processing like perform filters is very slow.) This test was done years ago, and the outcome was affected by many factors such as hardware. Maybe it will be better after improving these years.

## Why we choose Accord.NET

So after these days learning about this framework, a fundamental question busies my mind for a long time: Why we choose Accord.NET, until existing wrappers for powerful OpenCv in .NET and deep learning libraries like TensorFlow, CNTK (support C#)? We googled about Accord.NET performance comparison (e.g. image processing), key advantages and I've got nothing a satisfy answer. So We ask the the development team about this question. And the originator César Souza answers us:

"Hi, I would say the main point is that Accord.NET has a higher level of abstraction than the libraries you mentioned, and unlike them it is a unified framework where you can treat images, text, audio, under similar interfaces. And those interfaces also happen to depend on very fundamental .NET types such as jagged and multidimensional matrices, so even if you need to interop with other libraries such as OpenCV or CNTK you do not have to rewrite your application from scratch to use them. You can select things to use from Accord.NET and from OpenCV for example (that's part of the reason for the "accord" name).

Also, since the main goal is to offer an unified experience, Accord.NET can eventually be extended to use those libraries. For example, the .Neuro project will soon be updated to use TensorFlow/CNTK under the hood, but hopefully with a simpler API.

If I had to pick an example I would say that Accord.NET is like scikit-learn for Python, except that it also includes more fundamental libraries such as for mathematics and image processing if you need."

---
# References
1. Wikipedia - Accord.NET.<br>

2. Accord.NET Framework's Official Website.<br>

3.[10 Best Frameworks and Libraries for AI](https://dzone.com/articles/progressive-tools10-best-frameworks-and-libraries)

4.[Gitter:Where communities thrive](https://gitter.im/accord-net/framework)

5.[Accord.NET Framework for Windows Store, Windows Phone and WPF](https://groups.google.com/forum/#!topic/accord-net/XSJE_NJxKuU)

6.[The Comparison of Image Processing Libraries)](https://www.cnblogs.com/janghe/p/9759066.html)

