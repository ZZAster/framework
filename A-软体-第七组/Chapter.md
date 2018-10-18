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

*Table	2:	Most	active	contributors	in	trems	of	number	of	commits. *

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
![Accord.NET](https://github.com/ZZAster/framework/blob/development/A-%E8%BD%AF%E4%BD%93-%E7%AC%AC%E4%B8%83%E7%BB%84/Picture-framework/context_view.png)<br>
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
# Functional View

This part will show the functional view of the Accord.NET. 

The Functional view of a system defines the architectural elements that deliver the system’s functionality. The view documents the system’s functional structure-including the key functional elements, their responsibilities, the interfaces they expose, and the interactions between them. Taken together, this demonstrates how the system will perform the functions required of it.

##  Functional Capabilities

The Accord.NET Framework is a programming aid software. The Accord.NET Framework is a C# framework that extends the new  [AForge.NET Framework](https://en.wikipedia.org/wiki/AForge.NET) with new tools and libraries.  Accord.NET implements tools and features that are still not available in AForge.NET, such as Kernel Support Vector Machines, Discriminative and Projective Analysis, Hidden Markov Models, new Neural networks learning algorithms, new imaging filters, and other useful methods and tools. 

> *  [AForge.NET](https://en.wikipedia.org/wiki/AForge.NET) is a computer vision and artificial intelligence library. It implements a number of genetic, fuzzy logic and machine learning algorithms with several architectures of artificial neural networks with corresponding training algorithms. 
> * [Accord.NET](https://en.wikipedia.org/wiki/Accord.NET) is a collection of libraries for scientific computing, including numerical linear algebra, numerical optimization, statistics, artificial neural networks, machine learning, signal processing and computer vision and support libraries (such as graph plotting and visualization).

The framework comprises a set of libraries that are available in source code as well as via executable installers and [NuGet](https://en.wikipedia.org/wiki/NuGet) packages.

## Main Architecture 

The framework is comprised by the set of libraries and sample applications, which demonstrate their features: 
![Structure](https://raw.githubusercontent.com/ZZAster/framework/development/A-%E8%BD%AF%E4%BD%93-%E7%AC%AC%E4%B8%83%E7%BB%84/Picture-framework/Structure.png)
*Figure structure*
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

## Internal Structure

In order to realize the functions, Accord.NET has so many algorithms.The main functional algorithms included in the Accord.NET framework are described below by its category.

> * **Classification** - [Support Vector Machines ](http://accord-framework.net/docs/html/N_Accord_MachineLearning_VectorMachines.htm), [Logistic Regression ](http://accord-framework.net/docs/html/T_Accord_Statistics_Models_Regression_LogisticRegression.htm), [Decision Trees ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_DecisionTrees_DecisionTree.htm), [Neural Networks ](http://accord-framework.net/docs/html/N_Accord_Neuro.htm), [Deep Learning (Deep Neural Networks) ](http://accord-framework.net/docs/html/T_Accord_Neuro_Networks_DeepBeliefNetwork.htm), [Levenberg-Marquardt with Bayesian Regularization ](http://accord-framework.net/docs/html/T_Accord_Neuro_Learning_LevenbergMarquardtLearning.htm), [Restricted Boltzmann Machines ](http://accord-framework.net/docs/html/T_Accord_Neuro_Networks_RestrictedBoltzmannMachine.htm), [Sequence classification ](http://accord-framework.net/docs/html/T_Accord_Statistics_Models_Markov_Learning_HiddenMarkovClassifierLearning.htm), [Hidden Markov Classifiers ](http://accord-framework.net/docs/html/T_Accord_Statistics_Models_Markov_HiddenMarkovClassifier.htm)and [Hidden Conditional Random Fields ](http://accord-framework.net/docs/html/T_Accord_Statistics_Models_Fields_HiddenConditionalRandomField_1.htm). 
> * **Regression** - [Multiple linear regression ](http://accord-framework.net/docs/html/T_Accord_Statistics_Models_Regression_Linear_MultipleLinearRegression.htm), [Multivariate linear regression ](http://accord-framework.net/docs/html/T_Accord_Statistics_Models_Regression_Linear_MultivariateLinearRegression.htm), [polynomial regression ](http://accord-framework.net/docs/html/T_Accord_Statistics_Models_Regression_Linear_PolynomialRegression.htm), logarithmic regression. [Logistic regression ](http://accord-framework.net/docs/html/T_Accord_Statistics_Models_Regression_LogisticRegression.htm), [multinomial logistic regression (softmax) ](http://accord-framework.net/docs/html/T_Accord_Statistics_Models_Regression_MultinomialLogisticRegression.htm)and [generalized linear models ](http://accord-framework.net/docs/html/T_Accord_Statistics_Models_Regression_GeneralizedLinearRegression.htm). [L2-regularized L2-loss logistic regression ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_VectorMachines_Learning_ProbabilisticNewtonMethod.htm), [L2-regularized logistic regression ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_VectorMachines_Learning_ProbabilisticDualCoordinateDescent.htm), [L1-regularized logistic regression ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_VectorMachines_Learning_ProbabilisticCoordinateDescent.htm), [L2-regularized logistic regression in the dual form ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_VectorMachines_Learning_ProbabilisticDualCoordinateDescent.htm)and [regression support vector machines ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_VectorMachines_Learning_SequentialMinimalOptimizationRegression.htm). 
> * **Clustering **- [K-Means ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_KMeans.htm), [K-Modes ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_KModes.htm), [Mean-Shift ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_MeanShift.htm), [Gaussian Mixture Models ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_GaussianMixtureModel.htm), [Binary Split ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_BinarySplit.htm), [Deep Belief Networks ](http://accord-framework.net/docs/html/T_Accord_Neuro_Networks_DeepBeliefNetwork.htm), [Restricted Boltzmann Machines ](http://accord-framework.net/docs/html/T_Accord_Neuro_Networks_RestrictedBoltzmannMachine.htm). Clustering algorithms can be applied in arbitrary data, [including images ](https://github.com/accord-net/framework/wiki/Sample-applications#color-clustering-kmeans-and-meanshift), data tables, videos and [audio ](https://github.com/accord-net/framework/wiki/Audio). 
> * **Distribution **- Parametric and [non-parametric estimation ](http://accord-framework.net/docs/html/T_Accord_Statistics_Distributions_Univariate_EmpiricalDistribution.htm)of more than 40 distributions. [Univariate ](http://accord-framework.net/docs/html/N_Accord_Statistics_Distributions_Univariate.htm)distributions such as [Normal ](http://accord-framework.net/docs/html/T_Accord_Statistics_Distributions_Univariate_NormalDistribution.htm), [Cauchy ](http://accord-framework.net/docs/html/T_Accord_Statistics_Distributions_Univariate_CauchyDistribution.htm), [Hypergeometric ](http://accord-framework.net/docs/html/T_Accord_Statistics_Distributions_Univariate_HypergeometricDistribution.htm), [Poisson ](http://accord-framework.net/docs/html/T_Accord_Statistics_Distributions_Univariate_PoissonDistribution.htm), [Bernoulli ](http://accord-framework.net/docs/html/T_Accord_Statistics_Distributions_Univariate_BernoulliDistribution.htm), and specialized distributions such as the [Kolmogorov-Smirnov ](http://accord-framework.net/docs/html/T_Accord_Statistics_Distributions_Univariate_KolmogorovSmirnovDistribution.htm), [Nakagami ](http://accord-framework.net/docs/html/T_Accord_Statistics_Distributions_Univariate_NakagamiDistribution.htm), [Weibull ](http://accord-framework.net/docs/html/T_Accord_Statistics_Distributions_Univariate_WeibullDistribution.htm), and [Von-Mises ](http://accord-framework.net/docs/html/T_Accord_Statistics_Distributions_Univariate_VonMisesDistribution.htm)distributions. [Multivariate ](http://accord-framework.net/docs/html/N_Accord_Statistics_Distributions_Multivariate.htm)distributions such as the [multivariate Normal ](http://accord-framework.net/docs/html/T_Accord_Statistics_Distributions_Multivariate_MultivariateNormalDistribution.htm), [Multinomial ](http://accord-framework.net/docs/html/T_Accord_Statistics_Distributions_Multivariate_MultinomialDistribution.htm), [Independent ](http://accord-framework.net/docs/html/T_Accord_Statistics_Distributions_Multivariate_Independent_1.htm), [Joint ](http://accord-framework.net/docs/html/T_Accord_Statistics_Distributions_Multivariate_JointDistribution.htm)and [Mixture distributions ](http://accord-framework.net/docs/html/T_Accord_Statistics_Distributions_Multivariate_MultivariateMixture_1.htm). 
> * **Hypothesis Tests** - More than [35 statistical hypothesis tests ](http://accord-framework.net/docs/html/N_Accord_Statistics_Testing.htm), including [one way ](http://accord-framework.net/docs/html/T_Accord_Statistics_Testing_OneWayAnova.htm)and [two-way ANOVA tests ](http://accord-framework.net/docs/html/T_Accord_Statistics_Testing_TwoWayAnova.htm), non-parametric tests such as the [Kolmogorov-Smirnov test ](http://accord-framework.net/docs/html/T_Accord_Statistics_Testing_KolmogorovSmirnovTest.htm)and the [Sign Test for the Median ](http://accord-framework.net/docs/html/T_Accord_Statistics_Testing_SignTest.htm), [contingency table ](http://accord-framework.net/docs/html/T_Accord_Statistics_Analysis_GeneralConfusionMatrix.htm)tests such as the [Kappa test ](http://accord-framework.net/docs/html/T_Accord_Statistics_Testing_KappaTest.htm), with variations for [multiple tables ](http://accord-framework.net/docs/html/T_Accord_Statistics_Testing_AverageKappaTest.htm), as well as the [Bhapkar ](http://accord-framework.net/docs/html/T_Accord_Statistics_Testing_BhapkarTest.htm)and [Bowker ](http://accord-framework.net/docs/html/T_Accord_Statistics_Testing_BowkerTest.htm)tests; and the more traditional [Chi-Square ](http://accord-framework.net/docs/html/T_Accord_Statistics_Testing_ChiSquareTest.htm), [Z ](http://accord-framework.net/docs/html/T_Accord_Statistics_Testing_ZTest.htm), [F ](http://accord-framework.net/docs/html/T_Accord_Statistics_Testing_FTest.htm), [T ](http://accord-framework.net/docs/html/T_Accord_Statistics_Testing_TTest.htm)and [Wald tests ](http://accord-framework.net/docs/html/T_Accord_Statistics_Testing_WaldTest.htm). 
> * **Kernel Methods** - [Kernel Support Vector Machines ](http://accord-framework.net/docs/html/N_Accord_MachineLearning_VectorMachines.htm), [Multi-class ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_VectorMachines_MulticlassSupportVectorMachine.htm)and [Multi-label machines ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_VectorMachines_MultilabelSupportVectorMachine.htm), [Sequential Minimal Optimization ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_VectorMachines_Learning_SequentialMinimalOptimization.htm), [Least-Squares Learning ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_VectorMachines_Learning_LeastSquaresLearning.htm), [probabilistic learning ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_VectorMachines_Learning_ProbabilisticOutputCalibration.htm), including special methods for [linear machines ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_VectorMachines_SupportVectorMachine.htm)such as LIBLINEAR's methods for [Linear Coordinate Descent ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_VectorMachines_Learning_LinearCoordinateDescent.htm), [Linear Newton Method ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_VectorMachines_Learning_LinearNewtonMethod.htm), [Probabilistic Coordinate Descent ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_VectorMachines_Learning_ProbabilisticCoordinateDescent.htm), [Probabilistic Coordinate Descent in the Dual ](http://accord-framework.net/docs/html/T_Accord_MachineLearning_VectorMachines_Learning_ProbabilisticDualCoordinateDescent.htm), [Probabilistic Newton Method for L1 and L2 machines in both the dual and primal formulations](http://accord-framework.net/docs/html/T_Accord_MachineLearning_VectorMachines_Learning_ProbabilisticNewtonMethod.htm). 
> * **Imaging** - Interest and feature point detectors such as [Harris](http://accord-framework.net/docs/html/T_Accord_Imaging_HarrisCornersDetector.htm), [FREAK ](http://accord-framework.net/docs/html/T_Accord_Imaging_FastRetinaKeypoint.htm), [SURF ](http://accord-framework.net/docs/html/T_Accord_Imaging_SpeededUpRobustFeaturesDetector.htm), and [FAST ](http://accord-framework.net/docs/html/T_Accord_Imaging_FastCornersDetector.htm). [Grey-level Co-occurrence matrices ](http://accord-framework.net/docs/html/T_Accord_Imaging_GrayLevelCooccurrenceMatrix.htm), [Border following ](http://accord-framework.net/docs/html/T_Accord_Imaging_BorderFollowing.htm), [Bag-of-Visual-Words (BoW) ](http://accord-framework.net/docs/html/T_Accord_Imaging_BagOfVisualWords.htm), [RANSAC-based homography estimation ](http://accord-framework.net/docs/html/T_Accord_Imaging_RansacHomographyEstimator.htm), [integral images ](http://accord-framework.net/docs/html/T_Accord_Imaging_IntegralImage2.htm), [haralick textural feature extraction ](http://accord-framework.net/docs/html/T_Accord_Imaging_Haralick.htm), and dense descriptors such as [histogram of oriented gradients (HOG) ](http://accord-framework.net/docs/html/T_Accord_Imaging_HistogramsOfOrientedGradients.htm)and [Local Binary Pattern (LBP) ](http://accord-framework.net/docs/html/T_Accord_Imaging_LocalBinaryPattern.htm). Several [image filters for image processing applications ](http://accord-framework.net/docs/html/N_Accord_Imaging_Filters.htm)such as [difference of Gaussians ](http://accord-framework.net/docs/html/T_Accord_Imaging_Filters_DifferenceOfGaussians.htm), [Gabor ](http://accord-framework.net/docs/html/T_Accord_Imaging_Filters_GaborFilter.htm), [Niblack ](http://accord-framework.net/docs/html/T_Accord_Imaging_Filters_NiblackThreshold.htm)and [Sauvola thresholding ](http://accord-framework.net/docs/html/T_Accord_Imaging_Filters_SauvolaThreshold.htm). 
> * **Audio and Signal** - Load, parse, save, filter and transform [audio signals](http://accord-framework.net/docs/html/T_Accord_Audio_Signal.htm), such as applying [audio processing filters ](http://accord-framework.net/docs/html/N_Accord_Audio_Filters.htm)in both space and [frequency domain ](http://accord-framework.net/docs/html/T_Accord_Audio_ComplexSignal.htm). [WAV files ](http://accord-framework.net/docs/html/T_Accord_Audio_Formats_WaveDecoder.htm), [audio capture ](http://accord-framework.net/docs/html/T_Accord_DirectSound_AudioCaptureDevice.htm), time-domain filters such as [envelope ](http://accord-framework.net/docs/html/T_Accord_Audio_Filters_EnvelopeFilter.htm), [high-pass ](http://accord-framework.net/docs/html/T_Accord_Audio_Filters_HighPassFilter.htm), [low-pass ](http://accord-framework.net/docs/html/T_Accord_Audio_Filters_LowPassFilter.htm), [wave rectification ](http://accord-framework.net/docs/html/T_Accord_Audio_Filters_WaveRectifier.htm)filters. Frequency-domain operators such as [differential rectification filter ](http://accord-framework.net/docs/html/T_Accord_Audio_ComplexFilters_DifferentialRectificationFilter.htm)and [comb filter with Dirac's delta functions ](http://accord-framework.net/docs/html/T_Accord_Audio_ComplexFilters_CombFilter.htm). Signal generators for [Cosine ](http://accord-framework.net/docs/html/T_Accord_Audio_Generators_CosineGenerator.htm), [Impulse ](http://accord-framework.net/docs/html/T_Accord_Audio_Generators_ImpulseGenerator.htm), [Square ](http://accord-framework.net/docs/html/T_Accord_Audio_Generators_SquareGenerator.htm)signals. 
> * **Vision** - [Real-time face detection ](http://accord-framework.net/docs/html/T_Accord_Vision_Detection_HaarObjectDetector.htm)and [tracking ](http://accord-framework.net/docs/html/T_Accord_Vision_Tracking_Camshift.htm), as well as general methods for [detecting ](http://accord-framework.net/docs/html/T_Accord_Vision_GroupMatching.htm), [tracking ](http://accord-framework.net/docs/html/N_Accord_Vision_Tracking.htm)and [transforming objects in image streams ](http://accord-framework.net/docs/html/N_Accord_Imaging.htm). Contains [cascade definitions ](http://accord-framework.net/docs/html/N_Accord_Vision_Detection_Cascades.htm), [Camshift ](http://accord-framework.net/docs/html/T_Accord_Vision_Tracking_Camshift.htm)and [Dynamic Template Matching trackers ](http://accord-framework.net/docs/html/T_Accord_Vision_Tracking_MatchingTracker.htm). Includes [pre-created classifiers for human faces ](http://accord-framework.net/docs/html/T_Accord_Vision_Detection_Cascades_FaceHaarCascade.htm)and some facial features such as [noses ](http://accord-framework.net/docs/html/T_Accord_Vision_Detection_Cascades_NoseHaarCascade.htm). 
---
# References
1. Wikipedia - Accord.NET.<br>

2. Accord.NET Framework's Official Website.<br>
