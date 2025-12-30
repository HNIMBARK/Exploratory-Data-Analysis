# Exploratory-Data-Analysis

### the following topics:
#### •  What is the goal of EDA?
#### •  EDA with Python and R
#### •  EDA in Power BI

## Technical requirements

#### •  EWorking internet connection and Power BI Desktop
#### •  R and Python engines and IDEs
#### •  Configuring R with Power BI



## What is the goal of EDA?
The primary goal of EDA is to ensure that the dataset used for complex processes is clean and reliable. This involves addressing two critical aspects: eliminating missing values and outliers that have the potential to skew subsequent analyses, and selecting relevant variables that contribute substantive information while discarding those that are primarily noise.

By thoroughly cleaning the dataset, we eliminate potential sources of inaccuracy in the conclusions derived from subsequent processes. Missing values and outliers can disrupt the integrity of statistical analyses and lead to inaccurate results. Therefore, one of the first focuses of EDA is to identify and handle missing values appropriately, either by imputing appropriate estimates or by removing them  altogether. Similarly, outliers, extreme observations that deviate significantly from the overall pattern, are identified and treated to avoid undue influence on subsequent analyses.

In addition to ensuring data cleanliness, EDA involves a comprehensive exploration of the relationships between variables within the dataset. This exploration helps uncover insights that can justify and guide any subsequent complex processing. Identifying relationships, dependencies, and patterns between variables allows us to understand the underlying relationships and draw meaningful conclusions. Such insights gained during the EDA phase can justify the use of specific data preprocessing techniques or guide the selection of appropriate machine learning algorithms for later stages.

Ultimately, by conducting thorough EDA, we enhance the quality and reliability of the dataset, mitigate potential sources of error or bias, and lay the foundation for more accurate and effective analyses to be performed in subsequent stages. The main phases of EDA are as follows:

### 1.  Understanding your data
### 2.  Cleaning your data
### 3.  Discovering associations between variables



## Understanding your data

In this first phase, it is important to understand the meaning of each variable in the context of the problem that the dataset represents. Once the measurable business entities with which the variables are associated are clear, it is easier to infer how they interact with each other.

Having an idea of the size of the dataset, understood as the number of variables and the number of observations (rows), will help you get a first idea of the size of the data you will be dealing with. Next, it is crucial to identify and immediately define the type of variables involved (which can be numerical 
or categorical) in order to visualize them in the most appropriate way.

Then, knowing the descriptive statistics of the numerical variables in the dataset helps to gain greater sensitivity to their values. In addition, when you’re looking at them and trying to figure out how they’re distributed, there are a few different types of graphs that can help you get a clearer picture:


## Cleaning your data

As you learned in Chapter 16, Adding Statistical Insights: Outliers and Missing Values, these are the two most important activities for obtaining a statistically robust dataset that is as close as possible to the real case it represents:

### •  Identifying and managing outliers
### •  Imputation of missing values




## Discovering associations between variables

As you learned in Chapter 15, Adding Statistical Insights: Associations, knowing the degree of association  between variables in the dataset will certainly help you understand which ones carry the most information and which ones are mostly just noise. Selecting the most informative variables and using them to train a machine learning model will certainly help you to get more stable and performant results.




## EDA with Python and R

If you need to do data exploration using only Python or R, there are tools that automatically generate a number of visualizations to make your life easier. We have two lists below, one for Python tools and the other for R tools, in case you need them. It is easier to find tools for interactive data analysis in Python than in R. Packages available in R often provide wrappers that greatly simplify EDA via coding.

The Python libraries for EDA are as follows:
#### •  Sweetviz (https://pypi.org/project/sweetviz/): An open-source Python library that generates beautiful, high-density visualizations to kickstart EDA with just two lines of code

#### •  Lux (https://lux-api.readthedocs.io/): A Python library that facilitates fast and easy data exploration by automating the visualization and data analysis process
#### • pandas Prowling (https://pandas-profiling.github.io/pandas-profiling/): Generates profile reports from a pandas DataFrame for data analysis
#### • pandasGUI (https://github.com/adamerose/pandasgui): A GUI for viewing, plotting, and analyzing pandas DataFrames
#### •  D-Tale (https://github.com/man-group/dtale): The combination of a Flask backend and a React frontend to bring you an easy way to view and analyze pandas data structures

### The R packages for EDA are the following:

#### • ExPanDaR (https://github.com/joachim-gassen/ExPanDaR): ExPanDaR is a Shiny-based app supporting interactive exploratory data analysis. The repository is a bit outdated, but it’s still a valid application.
#### • Explore (https://github.com/rolkra/explore): An R package that simplifies exploratory data analysis. It allows users to interactively explore data using a few easy-to-remember functions. It also enables users to generate automated reports with one line of code.
#### • ggquickeda (https://github.com/smouksassi/ggquickeda): An R Shiny app/package that enables you to quickly explore your data and to detect trends on the y thanks to scatterplots, dot plots, boxplots, bar plots, and so on.
#### •  summarytools (https://github.com/dcomtois/summarytools): An R package for data clean-ing, exploring, and simple reporting. It integrates well with commonly used soware and tools for reporting in R (such as RStudio).
#### • DataExplorer (https://boxuancui.github.io/DataExplorer/): Aims to automate most data handling and visualization so that users can focus on studying the data and extracting insights.





## EDA in Power BI

In this section, we will make extensive use of the ggplot2 package, an advanced R library designed for creating plots based on the Grammar of Graphics. It is not our intention to go into detail about every feature exposed by the package, even though it is used quite extensively in the code that accompanies the chapter. Our goal, as always, is to provide code that can be easily adapted for use in other projects and, above all, to provide a starting point for a more detailed look at the functions used. For more details, see the References section in this chapter.

**library(readr)
library(dplyr)
dataset_url <- 'http://bit.ly/titanic-dataset-csv'
src_tbl <- read_csv(dataset_url)
vars_to_drop <- c('PassengerId')
categorical_vars <- c('Sex', 'Ticket', 'Cabin', 'Embarked')
integer_vars <- c('Survived', 'Pclass', 'SibSp', 'Parch')**


The script then defines the **tbl** tibble by applying the appropriate transformations:

**tbl <- src_tbl %>%
  mutate(
    across(categorical_vars, as.factor),
    across(integer_vars, as.integer)
  ) %>%
  select( -all_of(vars_to_drop) )**
  
This script will be preloaded into any other R script you develop for the EDA report, so you can be sure to have the dataset with the exact data types specified in memory.
So, let’s start developing the report from the basic statistics of the dataset.


## Dataset summary page

The first page of the EDA report is responsible for providing the analyst with an overview of the data contained in the dataset. Some basic information is exposed that enriches the output of the DataEx-plorer package’s **introduce()** function. This information is as follows:

### •  Number of rows and columns
### •  Number of discrete (categorical) and continuous (numerical) columns
### •  Number of columns having all missing values
### •  Total number of missing values in the dataset
### •  Number of complete rows, that is, not having missing values
### •  Total number of observations in the dataset, given by the number of rows multiplied by the number of columns
### •  Memory used in KB
### •  Number of duplicated rows

Then, a summary statistics table for the entire dataset is computed from the output of the **dfSummary()** function of the summarytools package. It contains the following information for each variable:

### •  Variable name and data type
### •  Basic statistics according to the data type
### •  Number of unique valid values (not null)



## Frequencies of valid values

### •  Number of valid values and their percentage
### •  Number of missing values and their percentage

Finally, more extensive descriptive statistics are available for numerical variables thanks to the **descr()** function of the summary tools package. In addition to the most common ones, the following statistics are added:

### • Median absolute deviation (mad): Unlike variance and standard deviation, this is a robust measure of how widely distributed outliers are in a dataset. It is typically used for non-normal distributions.
### •  Interquartile range (IQR): As you saw with the box plots, this is a measure of where the bulk of the distribution values lie.
### • Coefficient of variation (cv): This is a measure of relative variability as it is the ratio of the standard deviation to the mean.
### •  Coefficient of skewness (skewness): A measure of the lack of symmetry in a distribution.
### •  Kurtosis: It is a measure of whether the data is heavy-tailed or light-tailed relative to a normal istribution.

With this information, the analyst can get a complete picture of the shape of the data contained in the dataset






## Installing CRAN R is very simple:

### 1.  Go to https://cran.r-project.org/ and click on the Download R for Windows link in the middle of the page.
### 2.  Then, click on the base link on the le, under the Subdirectories label.
### 3. Finally, click on the Download R xxx for Windows link (where xxx corresponds to the actual, available version) on the top le of the next page.

IMPORTANT NOTE
If you need to use multiple R engines installed on the machine for your Power Query trans-formations, you must also install Power BI Desktop. It allows you to switch the routing of the data gateway to the selected engine through its options by updating the C:\Users\<your-username>\AppData\Local\PowerBIScripting\RSettings.xml conguration file. This file allows the override of the R engine referenced by the data gateway by default.
## TIP
We recommend installing the latest available version of CRAN R. Unfortunately, with the default installation, CRAN R will not benet from the performance advantages of the 
MKL library, as it did with MRO, but in the next sections, you’ll be shown how to link it to a classic CRAN R installation.


### 4.  Once the R-x.x.x-win.exe le is downloaded, double-click on it and select the language to be used during the installation.
### 5.  The next screen, Information, shows you the license of the soware. Click on “Next”.
### 6.  In the next window, you can select the destination location of the soware. Keep the default one and click on “Next”.
### 7.  In the “Select Components” window, you can choose which components to install. By default, all are selected, and “User installation” is chosen. Click on “Next”.
### 8.  In the “Startup options” window, keep the default (No) and click on “Next”.
### 9.  In the “Select Start Menu Folder” window, keep the default and click on “Next”.
### 10.  In the “Select Additional Tasks” window, you can choose to add additional shortcuts for your convenience. Keep the default selected and click on “Next”.
### 11.  The installation will start. Click “Finish” at the end of it.





ggplot2
