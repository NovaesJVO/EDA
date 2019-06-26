# The EDA Project #

**Attention**: EDA is **not** clinical or commercial software. It is designed for educational and demonstration purposes.

EDA, is an environment that allows the user to analyze the results generated by different search approaches for similarity with diversity. The system uses RF techniques to include the user in the retrieval process, so that he can iteratively evaluate the results generated and adjust the process to his intention, without the need to reformulate the search.

It has been implemented in [Java](https://www.oracle.com/technetwork/pt/java/javase/downloads/index.html), with the help of the [OpenCV 4](https://opencv.org/opencv-4-0/) and [JFreeChart](http://www.jfree.org/jfreechart/index.html) libraries.   

Despite the authors' efforts to release the prototypes without errors, there may be some problems. If you encounter any problems or wish to add new features, please contact us.

**Quote**: If you download or use EDA for technical tests or anilis, we ask that you include the following reference:

* Novaes, J.V.O; Santos, L. F. D; Traina, A.; Traina Jr., C; Bedo, M. V. N. SBBD 2019 Proceedings Satellite Events of the 34th Brazilian Symposium on Databases (SBBD) 2019: Pagina_Inicio-Pagina_Fim. Ceará, Brazil, October 7-10, 2019.

### 1. Minimum requirements ###

* Screen resolution: 1280×800 (or higher)
* 200 MB free disk space (For installation!).
* 2 GB RAM.
* Intel Core™2 Duo P8600 core processor.
* Java JDK 8 (or higher)

### 2. Using EDA ###

EDA was developed for Linux-based systems. The installation process described below has been tested on a [Ubuntu 18.04](http://releases.ubuntu.com/18.04/), For other distributions based on Ubuntu the operation may be similar, but it may be necessary to install some packages manually and, to date, other Linux distributions have not been tested.

  ![Main](./Main.png)

  The following [video](http://youtube.com)  generically presents the system features.

**2.1 Download**

* Clone or download this project.
* If necessary unzip the downloaded file.
* The following files must be in the directory:

```
  EDA
    ├── Corel1000
    │   ├── 0.jpg
    │   ├── ...
    │   └── 999.jpg
    ├── Corel_class.txt
    ├── Corel_Colorhist.txt
    ├── dist
    │   ├── lib
    │   │   ├── jcommon-1.0.23.jar
    │   │   ├── jfreechart-1.0.19.jar
    │   │   └── opencv-400.jar
    │   ├── Projeto.jar
    │   └── Tests
    │       └── Script
    │           └── Script.txt
    ├── lib
    │   └── libopencv_java400.so
    ├── Main.png
    ├── README.md
    ├── run.sh
    └── Self_Features.txt

6 directories, 1012 files 
```


**2.2 Run**
  The run file is run.sh. Initially it is necessary to make this file an execult, for this use the command: chmod + x run.sh and to execute use: ./run.sh.

  In the first run it may be necessary to install some packages, in this case, the root password can be requested.

  List of packages used by EDA:
  * libjasper1 
  * libjasper-dev 
  * libavcodec-dev 
  * libavformat-dev 
  * libswscale-dev 
  * libdc1394-22-dev 
  * execstack

**2.3 Resources**

The following literature resources have been implemented, tested, and are available in the EDA:

* Seven features extractors: Color Layout, Color Structure, Dominant Color, Edge Histogram, Haralick, Local Binary Pattern, and Scalable Color.
<br/>

* Five distance functions: Bray-Curtis, Canberra, Chebyshev, Euclidean and Manhatan.
<br/>

* Seven query algorithms (with or without diversity): Better Result with Influence Diversification (BRIDk), First Match (FM), Greedy Marginal Contribution (GMC), k-Nearest Neighbors Query (kNNq), Maximal Marginal Relevance (MMR), Relative Grouping based on Influence (ReGi) and Range Query (Rq).
<br/>

* Three Relevance Feedback (RF) techniques: Query Point Movement, Vector Support Machine and Similarity Refinement Evaluator.
<br/>
* Six Evaluation Metrics: Precision and Revocation, Average Average Precision - mAP, Average Recall - AR, Number of Relevant and Irrelevant Images by Iteration and Search Execution Time and RF Technique.


**2.4 Query Parameters**

Query parameters may differ depending on the query algorithm. To facilitate the configuration process, it follows a list of the parameters expected by each algorithm:

* Better Result with Influence Diversification (BRIDk), k-Nearest Neighbors Query (kNNq) and Relative Grouping based on Influence (ReGi): Expect an integer (k) that indicates the number of images that should be returned.

* First Match (FM): It waits for an integer (k) that indicates the number of images that must be returned and a number >= 0 that indicates the minimum separation distance between the elements.

* Greedy Marginal Contribution (GMC) and Maximal Marginal Relevance (MMR): It expects an integer (k) that indicates the number of images to be returned, a value in the interval [0; 1] that indicates the diversity preference of the user, and an integer that indicates the proportion of images that should be used during the optimization phase.

* Range Query (Rq): It waits for a number > 0 that indicates the maximum distance threshold.

**2.5 Datasets Settings**
When starting EDA for the first time, it will be necessary to configure at least one of the datasets that will be used. EDA allows this to be done in two ways:

  
  1. The system is in charge of generating the features of the images of the dataset, being the responsibility of the user to inform the name of the dataset and the directory where the images are.
<br/>

  2. You can use features generated externally to the system. In this case, it is necessary to inform the name of the dataset, the name of the feature extractor used, the directory of the images and a file (.txt) that contains the extracted features. This file must be in this [format](./Corel_Colorhist.txt):

      * Number of images.
      * Number of features.
      * The other lines must contain the features separated by; and end up as the name of the image to which the features belong.

When you complete the settings, the user must save the changes made. At this point, a loading screen will appear, wait until the process is finished. When this happens, a button to go to the main EDA interface will appear.

**2.6 Explorer Module:**

The Explorer Module, the first to appear on the main interface, was designed to allow some system functionality to be tested before and to perform some kind of experiment.

Initially, it is necessary to load a query image, select a dataset, a distance function, a feature extractor, a query algorithm, set the query parameters, and then execute the query. After executing the query, the system displays the result set on the preview screen and shows a selection screen of the RF technique. From this, the user can:
<br/>

* Clicking on one of the recovered images with the right mouse button while holding down the Shift key opens a display screen containing the image. If the search algorithm used is ReGi, the Group Viewer functionality (2.6) will be used, this functionality displays all the images grouped together with one of the representative images retrieved.
<br/>

* Clicking on the right-click images, while holding down the Ctrl key, selects the images, which can be displayed on the preview screen by clicking "Show Selected Images".
<br/>

* Double click on an image, right click the image as relevant and with the left button labels the image as irrelevant.
<br/>

* After labeling images as relevant and / or irrelevant, the user can select an RF technique and click on "Relevance Feedback" to feed the system. A new search will be performed and its result will be displayed.

**2.7 Experment Module - Supervised Feedback:**
The Experiment Module - Feedback Supervised allows the user to evaluate the quality of the retrieval process by performing multiple searches with the same RF configuration and technique but with different query images. The configuration of this module is similar to that of the exploratory module, the main difference is that it allows loading more than one query image. In addition, this is a module of experiments, so for each iteration information such as the execution time of the search algorithm, RF technique and the amount of relevant and irrelevant images retrieved, are saved and can be used in later analyzes.

Before starting the experiment, it is necessary to load the query image, select a dataset, a distance function, a characteristic extractor, a search algorithm, define the search parameters and then start the experiment. At this point, the result of a search using the first query image is displayed, the user can then label the images and re-feed the system or execute a new search using if it exists, the next query image. During the experiment the user can:

* At any time the user can finish the experiment and, in this case, all the information obtained so far, are saved.
<br/>

* Clicking on one of the recovered images with the right mouse button while holding down the Shift key opens a display screen containing the image. If the search algorithm used is ReGi, the Group Viewer functionality (2.6) will be used, this functionality displays all the images grouped together with one of the representative images retrieved.
<br/>

* Clicking on the right-click images, while holding down the Ctrl key, selects the images, which can be displayed on the preview screen by clicking "Show Selected Images".
<br/>

* Double click on an image, right click the image as relevant and with the left button labels the image as irrelevant.
<br/>

* After labeling the images, the user can click on "Relevance Feedback" to feedback the system. A new search will be performed and its result will be displayed.

**2.8 Group Viewer:**

This feature allows you to see how the grouping generated by ReGi is being generated.

When using the ReGi search algorithm and clicking on one of the representative images retrieved with the right button, while pressing the Shift key, it triggers the interface of this functionality. The grouped images are displayed in a list and clicking on one of the images in that list causes it to appear in the center of the interface in a larger size. If the user wishes to view the image in real size, just double-click the image in the center of the interface. To facilitate user interaction with this result, the images in the list are loaded 10 out of 10, if it is necessary to load more images just click on "Load More" and, if there are, 10 new images will be added to the list.

**2.9 Experment Module - Unsurpervised Feedback:**

The purpose of this module is similar to that of Supervised Feedback, the main difference is that the image evaluation process is done automatically. Analogously, this module allows you to configure the search and select the feedback technique, but allows the user to select the images that will be used during the tests in three ways: random, via script or manual selection:

* Random Selection: The user must inform the directory of the images that will be used in the experiment and the number of images that must be selected. From this, the system randomly chooses the images in the amount of informed. To allow the results generated by the random selection to be replicated, the system generates a script, which allows you to re-run the experiment.
<br/>

* Selection via script: It is necessary to select select a file containing the search configuration, the RF technique and a list with the directory paths of each of the images.
<br/>

* Manual selection: the user has to manually select each of the images that will be used (similar to the Supervised Feedback module).

The automatic evaluation process considers that a retrieved image is relevant if it is of the same class as the search image, otherwise the image is irrelevant, so the user must inform the system what class of images are provided (search and dataset). EDA, allows the class of the images to be provided in two ways: via the class file or via the image label.

* Class file: it is expected a file that contains the name of all the images, such that each line has the name of an image and the identifier of the class to which the image belongs, [for example](./Corel_class.txt).
<br/>  

* Image label: it is expected that each image has in its file name expected that each image has in its filename the class it belongs to, for example: "01_img2.jpg", in this case, we have to image img2.jpg belongs to class 01.

Because of the automatic evaluation, the system requires a parameter that indicates the maximum number of iterations (query and feedback) that can be performed in each of the searches, because without this parameter, the system could execute infinite iterations and never finalize the test. Therefore, before starting an experiment, the system prompts the user to enter the maximum number of iterations.

The automatic experiment process works as follows:

  1. The first query image listed is used to perform a search, the result of that search is converted into a list with the name of the retrieved images.
<br/>  
  
  2. From this list, the evaluation of the images is done, being verified if the class of recovered images is the same as the image of the query. If yes, the image is marked as relevant, otherwise, the image is marked as irrelevant.
<br/>  
  
  3. Then the RF technique is applied and a new search is performed.
<br/>  

  4. The second and third steps are repeated until the maximum number of iterations has been reached. When this occurs, a new query image is used and the process is repeated from the beginning. If there are no more query images, the process terminates and the system saves the test results.

**2.10 Result Analysis:**

This interface allows, through quantitative metrics, to visualize the results obtained in the experiments. As the image evaluation process can be supervised or not, this interface was divided into two sub-interfaces, one to analyze the experiments with supervised feedback and another to the unsupervised feedback experiments. Both have the same functionalities, but allow to evaluate separately the results generated by each type of evaluation.

The operation of this interface is quite simple, initially, it is necessary to select which type of evaluation you wish to analyze, then you need to select the evaluation metrics and the test files that will be used. From there, the system is in charge of analyzing the results and generating the graphs.

* To perform the analysis you can select all the test files or select only those that you want manually.
<br/>  

* After generating the graphics, the system allows all of them to be exported. To do this simply click on the "Save Analysis" button and inform the location where the images should be exported. All graphics will be saved in PNG format.
<br/>  

* The system allows all test files and scripts to be copied and provides a copy functionality. To access it, simply go to **options -> copy test file** and inform the location where the files should be copied.

**2.11 Using External Features:**

All the externally generated features that are available to the system will appear with the word "Self" before the character extractor name, for example: "Self - Color_Histogram". As these characteristics were generated externally, to use query images that are not part of the dataset, it is necessary to inform the system, manually, the characteristics of that query image. Whenever this occurs, the Exploratory and Experiments: Supervised Feedback modules will display a window requesting the characteristics of the current query image. A single line is expected, containing the characteristics separated by ";". The Experiments: Unsupervised Feedback module allows these features to be informed during manual selection. In this case, it is necessary to select a file, which contains the path for each of the query images, and the characteristics of that image, again, separated by ";". [Here is an example](./Self_Features) of the format of this file.


### 3. Additional Information and Legal Note ####

The demonstration binary file is under GPLv2 restrictions due to free use of [JAVA](http://openjdk.java.net/legal/) requirements.

This repository contains a demonstration, any express or implied warranties, including without limitation the implied warranties of merchantability and fitness for a particular purpose are waived. Under no circumstances will the authors of this software or its contributors be liable for any direct, indirect, incidental, special, exemplary or consequential damages (including, but not limited to, acquiring substitute goods or services, loss of use, data or profits, or business interruption), but caused and in any theory of liability in the contract, objective liability or unlawful act (including negligence or otherwise) arising in any way in the use of this statement, even if advised of the possibility of such damage.
