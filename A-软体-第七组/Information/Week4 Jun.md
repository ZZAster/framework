# Week4'  Jun

## 1.1 What is Accord.NET

Accord.NET provides statistical analysis, machine learning, image processing and computer vision methods for .NET applications. It can be used on Microsoft Windows, Xamarin, Unity3D, Windows Store applications, Linux or mobile.  Once an extension to the former AForge.NET Framework, the framework grew to incorporate AForge.NET and complement it with new features, adding to a more complete environment for scientific computing in .NET. 
The framework is divided in libraries, available through an executable installer, standalone compressed archives and NuGet packages. 

### 1.1.1 How to install it

The easiest way to get started is through NuGet. Search for "Accord.NET" in the package manager, then chose to install the modules you are more likely interested. If you are on Visual Studio, right-click on the "References" item in your solution folder, and select "Manage NuGet Packages." Search for the modules you want, and then select install.

### 1.1.2 The content of Accord.NET framework 3.7

![](https://raw.githubusercontent.com/ZZAster/framework/development/A-%E8%BD%AF%E4%BD%93-%E7%AC%AC%E4%B8%83%E7%BB%84/Picture-framework/content.png)

Externals contain some auxiliary component, Samples is the source code of cases, Setup is the installed program, and Sources is the code of project. Source code, Unit Tests is the unit test code.

## 1.2  Three functional modules of Accord.NET

The Accord.NET framework has three main functional modules. For scientific computing, signal and image processing, support libraries. Some namespace and functions of the three models are briefly introduced below. 

### 1.2.1 Scientific computing

- **Accord.Math** -  Contains a matrix extension library, along with a suite of  numerical matrix decomposition methods, numerical optimization algorithms  for constrained and unconstrained problems, special functions and other  tools for scientific applications.
- **Accord.Statistics** -  Contains probability distributions, hypothesis testing, statistical models and methods such as Linear and Logistic regression, Hidden Markov Models, (Hidden) Conditional Random Fields, Principal Component Analysis, Partial Least Squares, Discriminant Analysis, Kernel methods and many other related techniques.
- **Accord.MachineLearning** -  Support Vector Machines, Decision Trees, Naive Bayesian models, K-means, Gaussian Mixture models and general algorithms such as Ransac, Cross-validation and Grid-Search for machine-learning applications. 
- **Accord.Neuro** -   Neural learning algorithms such as Levenberg-Marquardt, Parallel Resilient Backpropagation, the Nguyen-Widrow initialization algorithm, Deep Belief Networks and Restrictured Boltzmann Machines, and many other neural network related items. 

### 1.2.2 Signal and image processing

- **Accord.Imaging** -   Contains interest point detectors (such as Harris, SURF, FAST and FREAK), image filters, image matching and  image stitching methods, as well as feature extractors such as Histograms of Oriented Gradients and Haralick's textural feature descriptors. 
- **Accord.Audio** -   Contains methods to process, transforms, filters and handle audio signals for machine learning and statistical applications. 
- **Accord.Vision** -   Real-time face detection and tracking, as well as general methods for detecting, tracking and transforming objects in image streams. Contains cascade definitions, Camshift and Dynamic Template Matching trackers.

### 1.2.3 Support libraries

- **Accord.Controls** -   Histograms, scatterplots and tabular data viewers for scientific applications.
- **Accord.Controls.Imaging** -   Windows Forms controls to show and handle images. Contains a convenient ImageBox control which mimics the traditional MessageBox for quickly displaying or inspecting images.
- **Accord.Controls.Audio** -  Windows Forms controls to display waveforms and audio-related information. 
- **Accord.Controls.Vision** -  Windows Forms components and controls to track head, face and hand movements and other computer vision related tasks.
