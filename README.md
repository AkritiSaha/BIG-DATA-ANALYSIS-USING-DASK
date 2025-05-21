I showcased the implementation of scalable data analysis on Dask, a parallel computing library in Python which facilitates working with datasets that surpass available memory. I performed all the analysis in a Jupyter Notebook which is an interactive environment that offers easy and convenient execution, making it simpler to develop, visualize, and interpret results step by step.

Objective-

As discussed earlier, this project aimed to demonstrate the effectiveness of Dask in big data applications and its performance relative to other libraries such as Pandas, which is perhaps the most common in big data frameworks. While Pandas does well with a reasonable amount of data, it tends to be inefficient as the dataset scales up. Dask, on the other hand, effortlessly makes use of parallelism and out-of-core computation to scale out seamlessly.

Dataset Overview-

For the analysis, I used the Titanic dataset, one of the most famous datasets in machine learning. It consists of a passenger’s age, sex, class, fare, and whether they survived or not. While the Titanic dataset isn't the biggest dataset available, it was useful to illustrate Dask's capabilities performing identical operations to those performed with Pandas while preparing us for real world scenarios.

Tools and Libraries-

Dask: Supports data loading, transformation, and computation for distributed and scalable systems.
Jupyter Notebook: Supports constructing the analysis incrementally along with superb visualization of intermediate work which is results.

Python: The primary programming language where the code and logic will be written.

Key Steps and Insights-

Installation and Setup:

This notebook starts off with Dask installation, running pip install dask[complete] in their command line interface. Afterwards, the notebook imports dask.dataframe as dd to work with large tabular data sets in the same way one does with Pandas data frames.

Data Loading and Initial Exploration:

This step involved importing the Titanic dataset via Dask’s dd.read_csv() function, which is specifically designed for lazy evaluation and is efficient in reading data. Basic operations such as head() and shape were executed to check if the dataset was properly loaded.

Descriptive Analysis:

The count of survivors and non-survivors was derived by looking up the column labeled “Survived” alongside the function value_counts().compute().

Passenger's average age was calculated with .mean().compute().

Female passengers were counted by using a boolean array through a mask and sum().compute().

Categorical Insights:

Counts of passengers for various embarkation points (e.g., S, C, Q) were summed.

The maximum fare paid was retrieved via extraction using .max().compute().

The total fare averaged in all classes was computed with groupby and with regard to Pclass. 

Dealing with Missing Values:

An important step in pre-processing data was marking and imputing gaps:

Gaps in Age were filling using isnull().mean().compute().

The Age column further were replaced using fillna to the mean age.

Feature Engineering and Transformations:

Aged passengers over sixty years old specifically were subsetted to study the subset.

To evaluate the effect of family on survival and comfort, a new feature FamilySize was created by aggregating siblings/spouses (SibSp) and parents/children (Parch) who were onboard.

Scalability Testing:

The Titanic data set may be small, but this mimics how the same codebase would scale to a much larger dataset without changing the logic. Each calculation was carried out using Dask's compute() method which executes in a parallel, distributed manner.

Final Thoughts-

In this task, I demonstrated Dask's ability to perform scalable data analysis by highlighting it as it is more efficient than Pandas when working with large datasets.
