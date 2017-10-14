# IRIS
The purpose of this repository is to get familiar with the IRIS dataset that is on [kaggle.com](http://www.kaggle.com/). This particular dataset is located [here](https://www.kaggle.com/uciml/iris). We will be using this dataset for Project 1 for DATA 550 at Mercyhurst University, in Erie, PA.

## File and Folder Structure

All data files are contained in the folder called ```input```. I have also created two Jupyter notebooks that connect to these data files, which are located in the ```notebooks``` folder.

The reasoning behind this structure is to match how things are on Kaggle, which makes switching between my local copy and the copy in Kaggle easier.

## Notebooks

The first notebook to look at is ```iris-experiments.ipynb```. This is the notebook that also located on my [Kaggle account](https://www.kaggle.com/rer145/iris-experiments/).  In this notebook, the goal was to follow along with an existing kernel to gain a better understanding of the data set.

The second notebook to look at is ```iris-pygal.ipynb```. This notebook is a smaller example of accessing the Iris data set, uses pygal for the visualizations.  This notebook is NOT on Kaggle, since Kaggle does not support the use of pygal on its site. This notebook is primarily used for my own experiments with using pygal against the data set.

The third notebook to look at is ```iris-data.ipynb```.  This notebook is a scratch file I used to explore the data in the Iris.csv data set. This notebook is where the data in the next section comes from.

## Data Familiarization

Pandas contains a very useful method called ```describe()```.  This method generates several statistics that summarize the data. In my opinion, this is a very quick and dirty way of finding out what sort of data you are using.  

I created two additional columns of data for each record that represents the area of the sepal and petal. This was accomplished by multiplying the length and width of the sepal and the petal and concatenating that to the iris data set. 

```python
sepalArea = iris["SepalLengthCm"] * iris["SepalWidthCm"]  #calculates the area of the sepals
petalArea = iris["PetalLengthCm"] * iris["PetalWidthCm"]  #calculates the area of the petals

# convert each calcuation into series, and then concatenate them to the original data
iris = pd.concat([iris, pd.Series(sepalArea, name='SepalAreaCm'), pd.Series(petalArea, name='PetalAreaCm')], axis=1)
```

#### Iris-setosa

Stat | Sepal Length (cm) | Sepal Width (cm) | Sepal Area (cm) | Petal Length (cm) | Petal Width (cm) | Petal Area (cm)
--- | ---: | ---: | ---: | ---: | ---: | ---:
count | 50.0 | 50.0 | 50.0 | 50.0 | 50.0 | 50.0
mean | 5.006 | 3.418 | 17.2088 | 1.464 | 0.244 | 0.3628
std | 0.352490 | 0.381024 | 2.947688 | 0.173511 | 0.107210 | 0.183248
min | 4.3 | 2.3 | 10.35 | 1.0 | 0.1 | 0.11
max | 5.8 | 4.4 | 25.08 | 1.9 | 0.6 | 0.96

#### Iris-versicolor

Stat | Sepal Length (cm) | Sepal Width (cm) | Sepal Area (cm) | Petal Length (cm) | Petal Width (cm) | Petal Area (cm)
--- | ---: | ---: | ---: | ---: | ---: | ---:
count | 50.0 | 50.0 | 50.0 | 50.0 | 50.0 | 50.0
mean | 5.936 | 2.770 | 16.5262 | 4.260 | 1.326 | 5.7204
std | 0.516171 | 0.313798 | 2.866882 | 0.469911 | 0.197753 | 1.368403
min | 4.9 | 2.0 | 10.00 | 3.0 | 1.0 | 3.30
max | 7.0 | 3.4 | 22.40 | 5.1 | 1.8 | 8.64

#### Iris-virginica

Stat | Sepal Length (cm) | Sepal Width (cm) | Sepal Area (cm) | Petal Length (cm) | Petal Width (cm) | Petal Area (cm)
--- | ---: | ---: | ---: | ---: | ---: | ---:
count | 50.0 | 50.0 | 50.0 | 50.0 | 50.0 | 50.0
mean | 6.588 | 2.974 | 19.6846 | 5.552 | 2.026 | 11.2962
std | 0.635880 | 0.322497 | 3.458783 | 0.551895 | 0.274650 | 2.157412
min | 4.9 | 2.2 | 12.25 | 4.5 | 1.4 | 7.50
max | 7.9 | 3.8 | 30.02 | 6.9 | 2.5 | 15.87




## Useful Links

* [My Kaggle Profile](https://www.kaggle.com/rer145)
* [Iris data set](https://www.kaggle.com/uciml/iris)
* [iris-experiments.ipynb on Kaggle](https://www.kaggle.com/rer145/iris-experiments/)