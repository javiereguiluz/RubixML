# Rubix ML for PHP
[![PHP from Packagist](https://img.shields.io/packagist/php-v/rubix/ml.svg?style=for-the-badge)](https://www.php.net/) [![Latest Stable Version](https://img.shields.io/packagist/v/rubix/ml.svg?style=for-the-badge)](https://packagist.org/packages/rubix/ml) [![Travis](https://img.shields.io/travis/andrewdalpino/Rubix-ML.svg?style=for-the-badge)](https://travis-ci.org/andrewdalpino/Rubix-ML) [![GitHub license](https://img.shields.io/github/license/andrewdalpino/Rubix.svg?style=for-the-badge)](https://github.com/andrewdalpino/Rubix/blob/master/LICENSE.md)

Rubix ML is a library that lets you build intelligent programs that learn from data in [PHP](https://php.net).

## Our Mission
The goal of Rubix is to bring easy to use machine learning (ML) capabilities to the PHP language. We aspire to provide the framework to facilitate rapid prototyping, small to medium sized projects, and education. If you're eager to get started you can follow along with the [basic introduction](#basic-introduction) or browse the [API reference](#api-reference).

## Installation
Install Rubix using composer:
```sh
$ composer require rubix/ml
```

## Requirements
- [PHP](https://php.net) 7.1.3 or above
- [GD extension](https://php.net/manual/en/book.image.php) for Image Vectorization

## License
MIT

## Documentation

### Table of Contents

 - [Basic Introduction](#basic-introduction)
	 - [Obtaining Data](#obtaining-data)
	 - [Choosing an Estimator](#choosing-an-estimator)
	 - [Training and Prediction](#training-and-prediction)
	 - [Evaluation](#evaluating-model-performance)
	 - [Visualization](#visualization)
     - [Next Steps](#next-steps)
- [Environments](#environments)
    - [Command Line](#command-line)
    - [Web Server](#web-server)
- [API Reference](#api-reference)
	- [Datasets](#datasets)
		- [Dataset Objects](#dataset-objects)
			- [Labeled](#labeled)
			- [Unlabeled](#unlabeled)
	- [Feature Extractors](#feature-extractors)
		- [Image Patch Descriptor](#image-patch-descriptor)
    	- [Word Count Vectorizer](#word-count-vectorizer)
		- [Raw Pixel Encoder](#raw-pixel-encoder)
	- [Estimators](#estimators)
		- [Anomaly Detectors](#anomaly-detectors)
			- [Isolation Forest](#isolation-forest)
			- [Isolation Tree](#isolation-tree)
			- [Local Outlier Factor](#local-outlier-factor)
			- [Robust Z Score](#robust-z-score)
		- [Classifiers](#classifiers)
			- [AdaBoost](#adaboost)
			- [Classification Tree](#classification-tree)
			- [Committee Machine](#committee-machine)
			- [Dummy Classifier](#dummy-classifier)
			- [Extra Tree Classifier](#extra-tree-classifier)
			- [Gaussian Naive Bayes](#gaussian-naive-bayes)
			- [K-d Neighbors](#k-d-neighbors)
			- [K Nearest Neighbors](#k-nearest-neighbors)
			- [Logistic Regression](#logistic-regression)
			- [Multi Layer Perceptron](#multi-layer-perceptron)
			- [Naive Bayes](#naive-bayes)
			- [Random Forest](#random-forest)
			- [Softmax Classifier](#softmax-classifier)
		- [Clusterers](#clusterers)
			- [DBSCAN](#dbscan)
			- [Fuzzy C Means](#fuzzy-c-means)
			- [Gaussian Mixture](#gaussian-mixture)
			- [K Means](#k-means)
			- [Mean Shift](#mean-shift)
		- [Regressors](#regressors)
			- [Adaline](#adaline)
			- [Dummy Regressor](#dummy-regressor)
			- [Extra Tree Regressor](#extra-tree-regressor)
			- [K-d Neighbors Regressor](#k-d-neighbors-regressor)
			- [KNN Regressor](#knn-regressor)
			- [MLP Regressor](#mlp-regressor)
			- [Regression Tree](#regression-tree)
			- [Ridge](#ridge)
	- [Meta-Estimators](#meta-estimators)
		- [Data Preprocessing](#data-preprocessing)
			- [Pipeline](#pipeline)
		- [Ensemble](#ensemble)
			- [Bootstrap Aggregator](#bootstrap-aggregator)
		- [Model Persistence](#model-persistence)
			- [Persistent Model](#persistent-model)
		- [Model Selection](#model-selection)
			- [Grid Search](#grid-search)
	- [Estimator Interfaces](#estimator-interfaces)
		- [Online](#online)
		- [Probabilistic](#probabilistic)
		- [Persistable](#persistable)
	- [Transformers](#transformers)
		- [Dense Random Projector](#dense-random-projector)
		- [Gaussian Random Projector](#gaussian-random-projector)
		- [L1 Normalizer](#l1-normalizer)
		- [L2 Normalizer](#l2-normalizer)
		- [Lambda Function](#lambda-function)
		- [Min Max Normalizer](#min-max-normalizer)
		- [Missing Data Imputer](#missing-data-imputer)
		- [Numeric String Converter](#numeric-string-converter)
		- [One Hot Encoder](#one-hot-encoder)
	    - [Polynomial Expander](#polynomial-expander)
	    - [Quartile Standardizer](#quartile-standardizer)
	    - [Robust Standardizer](#robust-standardizer)
	    - [Sparse Random Projector](#sparse-random-projector)
		- [TF-IDF Transformer](#tf---idf-transformer)
		- [Variance Threshold Filter](#variance-threshold-filter)
		- [Z Scale Standardizer](#z-scale-standardizer)
	- [Neural Network](#neural-network)
		- [Activation Functions](#activation-functions)
			- [ELU](#elu)
			- [Gaussian](#gaussian)
			- [Hyperbolic Tangent](#hyperbolic-tangent)
			- [ISRU](#isru)
			- [Leaky ReLU](#leaky-relu)
			- [ReLU](#relu)
			- [SELU](#selu)
			- [Sigmoid](#sigmoid)
			- [Softmax](#softmax)
			- [Soft Plus](#soft-plus)
			- [Softsign](#softsign)
			- [Thresholded ReLU](#thresholded-relu)
		- [Cost Functions](#cost-functions)
			- [Cross Entropy](#cross-entropy)
			- [Exponential](#exponential)
			- [Least Squares](#least-squares)
			- [Relative Entropy](#relative-entropy)
        - [Initializers](#initializers)
            - [He](#he)
            - [Le Cun](#le-cun)
            - [Normal](#normal)
            - [Xavier 1](#xavier-1)
            - [Xavier 2](#xavier-2)
		- [Layers](#layers)
			- [Input Layers](#input-layers)
				- [Placeholder](#placeholder)
			- [Hidden Layers](#hidden-layers)
                - [Activation](#activation)
				- [Alpha Dropout](#alpha-dropout)
				- [Batch Norm](#batch-norm)
				- [Dense](#dense)
				- [Dropout](#dropout)
				- [Noise](#noise)
                - [PReLU](#prelu)
			- [Output Layers](#output-layers)
				- [Binary](#Binary)
				- [Continuous](#continuous)
				- [Multiclass](#multiclass)
		- [Optimizers](#optimizers)
			- [AdaGrad](#adagrad)
			- [Adam](#adam)
			- [Momentum](#momentum)
			- [RMS Prop](#rms-prop)
			- [Step Decay](#step-decay)
			- [Stochastic](#stochastic)
		- [Snapshots](#snapshots)
	- [Kernels](#kernels)
		- [Distance](#distance)
			- [Canberra](#canberra)
			- [Cosine](#cosine)
			- [Diagonal](#diagonal)
			- [Euclidean](#euclidean)
			- [Hamming](#hamming)
			- [Jaccard](#jaccard)
			- [Manhattan](#manhattan)
			- [Minkowski](#minkowski)
	- [Cross Validation](#cross-validation)
		- [Validators](#validators)
			- [Hold Out](#hold-out)
			- [K Fold](#k-fold)
			- [Leave P Out](#leave-p-out)
			- [Monte Carlo](#monte-carlo)
		- [Metrics](#validation-metrics)
			- [Anomaly Detection](#anomaly-detection)
			- [Classification](#classification)
			- [Clustering](#clustering)
			- [Regression](#regression)
	- [Reports](#reports)
		- [Aggregate Report](#aggregate-report)
		- [Confusion Matrix](#confusion-matrix)
		- [Contingency Table](#contingency-table)
		- [Multiclass Breakdown](#multiclass-breakdown)
		- [Outlier Ratio](#outlier-ratio)
		- [Prediction Speed](#prediction-speed)
		- [Residual Breakdown](#residual-breakdown)
	- [Other](#other)
		- [Generators](#generators)
			- [Agglomerate](#agglomerate)
			- [Blob](#blob)
			- [Circle](#circle)
			- [Half Moon](#half-moon)
		- [Guessing Strategies](#guessing-strategies)
			- [Blurry Mean](#blurry-mean)
			- [Blurry Median](#blurry-median)
			- [K Most Frequent](#k-most-frequent)
			- [Lottery](#lottery)
			- [Popularity Contest](#popularity-contest)
			- [Wild Guess](#wild-guess)
		- [Helpers](#helpers)
			- [Params](#params)
		- [Tokenizers](#tokenizers)
			- [Whitespace](#whitespace)
			- [Word](#word-tokenizer)

---
### Basic Introduction
Machine learning is the process by which a computer program is able to progressively improve performance on a certain task through training and data without explicitly being programmed. There are two types of machine learning that Rubix supports out of the box, *Supervised* and *Unsupervised*.

 - **Supervised** learning is a technique to train computer models with a dataset in which the outcome of each sample data point has been *labeled* either by a human expert or another ML model prior to training. There are two types of supervised learning to consider in Rubix:
	 - **Classification** is the problem of identifying which *class* a particular sample belongs to. For example, one task may be in determining a particular species of Iris flower or predicting someone's MBTI personality type.
	 - **Regression** aims at predicting continuous *values* such as the sale price of a house in a particular city or the average life expectancy of an individual. A major difference between classification and regression is that while there are a finite number of classes that a sample can belong to, there are infinitely many real values that a regression model can predict.
- **Unsupervised** learning, by contrast, uses an *unlabeled* dataset and works by finding patterns within the training samples to learn new insights.
	- **Clustering** is the process of grouping data points in such a way that members of the same group are more similar (homogeneous) than the rest of the samples. You can think of clustering as assigning a class label to an otherwise unlabeled sample. An example where clustering is used is in differentiating tissues in PET scan images.
	- **Anomaly Detection** is the flagging of samples that do not conform to an expected pattern that is learned during training. Anomalous samples can often indicate adversarial activity, bad data, or exceptional performance.

When first starting out, it sometimes helps to make the distinction between *traditional* programming and machine learning. In traditional programming, you are given an input and output specification and it is your job to write the logic that maps inputs to the desired outputs. With machine learning, it is the algorithm that writes the function that does the input/output mapping and instead it is your job to design the model such that, when you feed it data, it can learn the mapping. For this reason, you can think of machine learning as "programming with data."

### Obtaining Data
Machine learning projects typically begin with a question. For example, you might want to answer the question "who of my friends are most likely to stay married to their spouse?" One way to go about answering this question with machine learning would be to go out and ask a bunch of happily married and divorced couples the same set of questions about their partner and then use that data to build a model of what a successful (or not) marriage looks like. Later, you can use that model to make predictions based on the answers you get from your friends. Specifically, the answers you collect are called *features* and they constitute measurements of some phenomena being observed. The number of features in a sample is called the dimensionality of the sample. For example, a sample with 20 features is said to be *20 dimensional*. The idea is to engineer enough of the right features for the model to be able to recognize patterns in the data.

An alternative to collecting data yourself is to access one of the many datasets that are free to use from a public repository. The advantage of using a public dataset is that, chances are, it has already been cleaned and therefore ready to use right out of the box. We recommend the University of California Irvine [Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets.html) as a great place to get started.

Note that there are a number of PHP libraries that make extracting data from CSV, databases, and cloud services a lot easier, and we recommend checking them out as well.

Here are a few libraries that we recommend that will help you get started extracting data:

- [PHP League CSV](https://csv.thephpleague.com/) - Generator-based CSV extractor
- [Doctrine DBAL](https://www.doctrine-project.org/projects/dbal.html) - SQL database abstraction layer
- [Google BigQuery](https://cloud.google.com/bigquery/docs/reference/libraries) - Cloud-based data warehouse via SQL

#### The Dataset Object
Data is passed around in Rubix via specialized data containers called Datasets. [Dataset objects](#dataset-objects) extend the PHP array structure with methods that properly handle selecting, splitting, folding, transforming, and randomizing the samples and labels contained within. In general, there are two types of Datasets, *Labeled* and *Unlabeled*. Labeled datasets are used for *supervised* learning and Unlabeled datasets are used for *unsupervised* learning and for making predictions. Dataset objects have a mutability policy of *generally* immutable except for performance reasons such as applying a [Transformer](#transformers).

For the following example, suppose that you went out and asked 100 couples (50 married and 50 divorced) about their partner's communication skills (between 1 and 5), attractiveness (between 1 and 5), and time spent together per week (hours per week). You could construct a [Labeled Dataset](#labeled) from this data like so:

```php
use \Rubix\ML\Datasets\Labeled;

$samples = [
    [3, 4, 50.5], [1, 5, 24.7], [4, 4, 62.], [3, 2, 31.1], ...
];

$labels = ['married', 'divorced', 'married', 'divorced', ...];

$dataset = new Labeled($samples, $labels);
```

### Choosing an Estimator

Estimators make up the core of the Rubix library as they are responsible for making predictions. There are many different algorithms to choose from and each one is designed to handle a specific (sometimes overlapping) task. Choosing the right [Estimator](#estimators) for the job is crucial to creating a system that is both accurate and performant.

In practice, one will try a number of different ways to model a problem including choosing a handful of Estimators to test out to get a better sense of what works. For our example problem we will start with a simple classifier called K Nearest Neighbors. Since the label of each training sample we collect will be a class (*married couples* or *divorced couples*), we need an Estimator that is designed to output class predictions. K Nearest Neighbors works by locating the closest training samples to an unknown sample and choosing the class label that appears most often.

#### Creating the Estimator Instance

Like most Estimators, the [K Nearest Neighbors](#k-nearest-neighbors) classifier requires a set of parameters (called *hyper-parameters*) to be chosen up front. These parameters can be selected based on some prior knowledge of the problem space, or at random. Fortunately, the defaults provided in Rubix are a good place to start for most machine learning problems. In addition, Rubix provides a meta-Estimator called [Grid Search](#grid-search) that optimizes the hyper-parameter space by searching for the most effective combination. For the purposes of our example we will just go with our intuition and choose the parameters outright.

You can find a full description of all of the K Nearest Neighbors parameters in the [API reference](#api-reference) guide which we highly recommend reading over a few times to get a good grasp for how each parameter effects the training.

The K Nearest Neighbors algorithm works by comparing the *distance* between a sample and each of samples from the training set. It will use the K *closest* points to base its prediction. For example, if the 5 closest neighbors to a given unknown sample have 4 married labels and 1 divorced label, then the algorithm will output a prediction of married with a probability of 0.8.

To instantiate a K Nearest Neighbors Classifier:
```php
use Rubix\ML\Classifiers\KNearestNeighbors;
use Rubix\ML\Kernels\Distance\Euclidean;

// Using the default parameters
$estimator = new KNearestNeighbors();

// Specifying the parameters
$estimator = new KNearestNeighbors(3, new Euclidean());
```

The first hyper-parameter that K Nearest Neighbors accepts is the number of nearest neighbors (*k*) to consider when making a prediction. The second parameter is the distance kernel that determines how distance is measured within the model.

Now that we've chosen and instantiated an Estimator and our Dataset object is ready to go, we are ready to train the model and use it to make some predictions.

### Training and Prediction
Training is the process of feeding the Estimator data so that it can learn the parameters of the model that best minimize some cost function. A *cost function* is a function that measures the performance of a model during training. The lower the cost, the better the model fits the training data. The overall way in which each Estimator *learns* is based on the underlying algorithm which has been implemented under the hood.

Passing the Labeled Dataset object we created earlier, we can train our K Nearest Neighbors classifier like so:
```php
...
$estimator->train($dataset);
```

For our 100 sample example training set, this should only take a matter of microseconds, but larger datasets with higher dimensionality and more sophisticated Estimators can take much longer. Once the Estimator has been fully trained, we can feed in some unknown samples to see what the model predicts. Turning back to out example problem, suppose that we went out and collected 5 new data points from our friends using the same questions we asked the couples we interviewed for our training set. We could make predictions on whether they will stay married or get divorced by taking their answers as features and running them in an Unlabeled dataset through the trained Estimator's `predict()` method.
```php
use Rubix\ML\Dataset\Unlabeled;

$unknown = [
    [4, 3, 44.2], [2, 2, 16.7], [2, 4, 19.5], [1, 5, 8.6], [3, 3, 55.],
];

$dataset = new Unlabeled($unknown);

$predictions = $estimator->predict($dataset);

var_dump($predictions);
```

##### Output:

```sh
array(5) {
	[0] => 'married'
	[1] => 'divorced'
	[2] => 'divorced'
	[3] => 'divorced'
	[4] => 'married'
}
```

From these results, we can deduce that, based on the data that the model has been trained with, it is important for couples to communicate and spend time together if they are going to stay happily married. We didn't need a machine learning model to tell us that, but imagine scaling this example to use a whole self-report inventory with 100 or more questions instead. With more features to work with, our model gains flexibility. But how do we when our model is any good at making accurate predictions in the real world? We'll address a technique called Cross Validation in the next section that aims at testing the generalization performance of a trained model.

### Evaluating Model Performance
Making predictions is not very useful unless the Estimator can correctly generalize what it has learned during training to the real world. [Cross Validation](#cross-validation) is a process by which we can test the model for its generalization ability. For the purposes of this introduction, we will use a simple form of cross validation called *Hold Out*. The [Hold Out](#hold-out) validator will take care of randomizing and splitting the dataset into training and testing sets for us, such that a portion of the data is *held out* to be used to test (or *validate*) the model. The reason we do not use *all* of the data for training is because we want to test the Estimator on samples that it has never seen before.

The Hold Out validator requires you to set the ratio of testing to training samples as a constructor parameter. In this case, let's choose to use a factor of 0.2 (20%) of the dataset for testing leaving the rest (80%) for training. Typically, 0.2 is a good default choice however your mileage may vary. The important thing to note here is the trade off between more data for training and more data to produce precise testing results. Once you get the hang of Hold Out, the next step is to consider more advanced cross validation techniques such as [K Fold](#k-fold), [Leave P Out](#leave-p-out), and [Monte Carlo](#monte-carlo) simulations.

To return a score from the Hold Out validator using the Accuracy metric just pass it the untrained Estimator instance and a dataset:

```php
use Rubix\ML\CrossValidation\HoldOut;
use Rubix\ML\CrossValidation\Metrics\Accuracy;

...
$validator = new HoldOut(0.2);

$score = $validator->test($estimator, $dataset, new Accuracy());

var_dump($score);
```

##### Output:

```sh
float(0.945)
```

### Visualization
Visualization is how you communicate the findings of your experiment to the end-user and is key to deriving value from your hard work. Although visualization is important (important enough for us to mention it), we consider it to be beyond the scope of what Rubix has to offer. Therefore, we leave you with the choice of using any of the many great plotting and visualization frameworks out there to communicate your predictions.

If you are looking for a place to start, we highly recommend [D3.js](https://d3js.org/), since it is an amazing data-driven framework written in Javascript and tends to play well with PHP.

### Next Steps
After you've gone through this basic introduction to machine learning in Rubix, we highly recommend reading over the [API Reference](#api-reference) to get an idea of what the library can do. The API Reference is the place you'll go to get detailed information and examples about the classes that make up the library. If you have a question or need help, feel free to post on our Github page.

---
### Environments
Typically, there are two different types of *environments* that a PHP program can run in - on the command line in a terminal window or on a web server such as Nginx via the FPM module. Most of the time you will only be working with the command line in Rubix unless you are building a system to work live in production. For more information regarding the environments in which PHP can run in you can refer to the [general installation considerations](http://php.net/manual/en/install.general.php) on the PHP website.

### Command Line
The most common use cases for Rubix only require the PHP command line interface (CLI) to run since we don't need to handle any web requests. The CLI runs directly in a terminal and does not have a maximum execution time set by default. Note that you may need to adjust your memory limit in php.ini to a suitable value (or -1 for no limit).

To run a program on the command line, make sure the PHP binary is in your default PATH and enter:
```sh
$ php Model.php
```

### Web Server
It is possible to run a model trained with Rubix in a live system on a web server either during a request or in the background in a queue but many considerations need to be taken into account to ensure a smooth system. The primary consideration is one of resource allocation as machine learning models tend to be highly resource (CPU and memory) intensive. It is generally discouraged to run an ML model within a web request cycle, but if you must, you will need to consider the execution time of the script as it can be used as a denial of service (DOS) attack if not handled properly.

---
### API Reference

### Datasets
Data is what powers machine learning programs so naturally we treat it as a first-class citizen. Rubix provides a number of classes that help you wrangle and even generate data.

### Dataset Objects
In Rubix, data is passed around using specialized data structures called Dataset objects. Dataset objects can hold a heterogeneous mix of categorical and continuous data and gracefully handles *null* values with a user-defined placeholder. Dataset objects make it easy to handle data in a canonical way.

There are two *types* of data that Estimators can process i.e *categorical* and *continuous*. Any numerical (integer or float) datum is considered continuous and any string datum is considered categorical by convention throughout Rubix. For example, the number 5 could be represented as a continuous variable by casting it to an integer or it can be interpreted as the index of a category by using a string type (*'5'*). It is important to note the distinction between the two types as they are handled differently in Rubix.

##### Example:
```php
use Rubix\ML\Datasets\Unlabeled;

$samples = [
	['rough', 8, 6.55], ['furry', 10, 9.89], ...
];

$dataset = new Unlabeled($samples);
```

The Dataset interface has a robust API designed to make handling datasets fast and easy. Below you'll find a description of the various methods available.

#### Selecting

Return the sample matrix:
```php
public samples() : array
```

Select the *sample* at row offset:
```php
public row(int $index) : array
```

Select the *values* of a feature column at offset:
```php
public column(int $index) : array
```

Return the *first* **n** rows of data in a new Dataset object:
```php
public head(int $n = 10) : self
```

Return the *last* **n** rows of data in a new Dataset object:
```php
public tail(int $n = 10) : self
```

##### Example:
```php
// Return the sample matrix
$samples = $dataset->samples();

// Return just the first 5 rows in a new dataset
$subset = $dataset->head(5);
```

#### Properties

Return the number of rows in the Dataset:
```php
public numRows() : int
```

Return the number of columns in the Dataset:
```php
public numColumns() : int
```

#### Splitting, Folding, and Batching

Remove **n** rows from the Dataset and return them in a new Dataset:
```php
public take(int $n = 1) : self
```

Leave **n** samples on the Dataset and return the rest in a new Dataset:
```php
public leave(int $n = 1) : self
```

Split the Dataset into *left* and *right* subsets given by a **ratio**:
```php
public split(float $ratio = 0.5) : array
```

Partition the Dataset into *left* and *right* subsets based on the value of a feature in a specified column:
```php
public partition(int $index, mixed $value) : array
```

Fold the Dataset **k** - 1 times to form **k** equal size Datasets:
```php
public fold(int $k = 10) : array
```

Batch the Dataset into subsets of **n** rows per batch:
```php
public batch(int $n = 50) : array
```

##### Example:
```php
// Remove the first 5 rows and return them in a new dataset
$subset = $dataset->take(5);

// Split the dataset into left and right subsets
list($left, $right) = $dataset->split(0.5);

// Partition the dataset by the feature column at index 4
list($left, $right) = $dataset->partition(4, 1532485673);

// Fold the dataset into 8 equal size datasets
$folds = $dataset->fold(8);
```

#### Randomizing

Randomize the order of the Dataset and return it:
```php
public randomize() : self
```

Generate a random subset with replacement of size **n**:
```php
public randomSubsetWithReplacement($n) : self
```

Generate a random *weighted* subset with replacement of size **n**:
```php
public randomWeightedSubsetWithReplacement($n, array $weights) : self
```

##### Example:
```php
// Randomize and split the dataset into two subsets
list($left, $right) = $dataset->randomize()->split(0.8);

// Generate a bootstrap dataset of 500 random samples
$subset = $dataset->randomSubsetWithReplacement(500);
```

#### Filtering

To filter a Dataset by a feature column:
```php
public filterByColumn(int $index, callable $fn) : self
```

##### example:
```php
$tallPeople = $dataset->filterByColumn(2, function ($value) {
	return $value > 178.5;
});
```

#### Sorting

To sort a Dataset by a specific feature column:
```php
public sortByColumn(int $index, bool $descending = false) : self
```

##### Example:
```php
...
var_dump($dataset->samples());

$dataset->sortByColumn(2, false);

var_dump($dataset->samples());
```

##### Output:
```sh
array(3) {
    [0]=> array(3) {
	    [0]=> string(4) "mean"
	    [1]=> string(4) "furry"
	    [2]=> int(8)
    }
    [1]=> array(3) {
	    [0]=> string(4) "nice"
	    [1]=> string(4) "rough"
	    [2]=> int(1)
    }
    [2]=> array(3) {
	    [0]=> string(4) "nice"
	    [1]=> string(4) "rough"
	    [2]=> int(6)
    }
}

array(3) {
    [0]=> array(3) {
	    [0]=> string(4) "nice"
	    [1]=> string(4) "rough"
	    [2]=> int(1)
    }
    [1]=> array(3) {
	    [0]=> string(4) "nice"
	    [1]=> string(4) "rough"
	    [2]=> int(6)
    }
    [2]=> array(3) {
	    [0]=> string(4) "mean"
	    [1]=> string(4) "furry"
	    [2]=> int(8)
    }
}
```

#### Prepending and Appending

To prepend a given Dataset onto the beginning of another Dataset:
```php
public prepend(Dataset $dataset) : self
```

To append a given Dataset onto the end of another Dataset:
```php
public append(Dataset $dataset) : self
```

#### Applying a Transformation

You can apply a fitted [Transformer](#transformers) to a Dataset directly passing it to the apply method on the Dataset.

```php
public apply(Transformer $transformer) : void
```

##### Example:
```php
use Rubix\ML\Transformers\OneHotEncoder;

...
$transformer = new OneHotEncoder();

$transformer->fit($dataset);

$dataset->apply($transformer);
```

#### Saving and Restoring
Dataset objects can be saved and restored from a serialized object file which makes them easy to work with. Saving will capture the current state of the dataset including any transformations that have been applied.

Save the Dataset to a file:
```php
public save(?string $path = null) : void
```

Restore the Dataset from a file:
```php
public static restore(string $path) : self
```

##### Example:
```php
// Save the dataset to a file
$dataset->save('path/to/dataset');

// Assign a filename (ex. 1531772454.dataset)
$dataset->save();

$dataset = Labeled::restore('path/to/dataset');
```

There are two types of Dataset objects in Rubix, *labeled* and *unlabeled*.

### Labeled
For *supervised* Estimators you will need to train it with a Labeled dataset consisting of a sample matrix with the addition of an array of labels that correspond to the observed outcome of each sample. Splitting, folding, randomizing, sorting, and subsampling are all done while keeping the indices of samples and labels aligned.

In addition to the basic Dataset interface, the Labeled class can sort and *stratify* the data by label.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | samples | None | array | A 2-dimensional array consisting of rows of samples and columns of features. |
| 2 | labels | None | array | A 1-dimensional array of labels that correspond to the samples in the dataset. |
| 3 | validate | true | bool | Should we validate the input? |

##### Additional Methods:
Return a 1-dimensional array of labels:
```php
public labels() : array
```

Return the label at the given row offset:
```php
public label(int $index) : mixed
```

Return all of the possible outcomes i.e. the unique labels:
```php
public possibleOutcomes() : array
```

Filter the Dataset by label:
```php
public filterByLabel(callable $fn) : self
```

Sort the Dataset by label:
```php
public sortByLabel(bool $descending = false) : self
```

Group the samples by label and return them in their own Dataset:
```php
public stratify() : array
```
Split the Dataset into left and right stratified subsets with a given **ratio** of samples in each:
```php
public stratifiedSplit($ratio = 0.5) : array
```

Fold the Dataset **k** - 1 times to form **k** equal size stratified Datasets
```php
public stratifiedFold($k = 10) : array
```

##### Example:
```php
use Rubix\ML\Datasets\Labeled;

...
$dataset = new Labeled($samples, $labels);

// Return all the labels in the dataset
$labels = $dataset->labels();

// Return the label at offset 3
$label = $dataset->label(3);

// Return all possible unique labels
$outcomes = $dataset->possibleOutcomes();

var_dump($labels);
var_dump($label);
var_dump($outcomes);
```

##### Output:
```sh
array(4) {
    [0]=> string(5) "female"
    [1]=> string(4) "male"
    [2]=> string(5) "female"
    [3]=> string(4) "male"
}

string(4) "male"

array(2) {
	[0]=> string(5) "female"
	[1]=> string(4) "male"
}
```

##### Example:
```php
...
// Fold the dataset into 5 equal size stratified subsets
$folds = $dataset->stratifiedFold(5);

// Split the dataset into two stratified subsets
list($left, $right) = $dataset->stratifiedSplit(0.8);

// Put each sample with label x into its own dataset
$strata = $dataset->stratify();
```

### Unlabeled
Unlabeled datasets can be used to train *unsupervised* Estimators and for feeding data into an Estimator to make predictions.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | samples | None | array | A 2-dimensional feature matrix consisting of rows of samples and columns of feature values. |
| 3 | validate | true | bool | Should we validate the input? |


##### Additional Methods:
This Dataset does not have any additional methods.

##### Example:
```php
use Rubix\ML\Datasets\Unlabeled;

$dataset = new Unlabeled($samples);
```

---
### Feature Extractors
Feature Extractors are objects that help you encode raw data into feature vectors so they can be used by an Estimator.

Extractors have an API similar to [Transformers](#transformers), however, they are designed to be used on the raw data *before* it is inserted into a Dataset Object. The output of the `extract()` method is a sample matrix that can be used to build a [Dataset Object](#dataset-objects).

Fit the Extractor to the raw samples before extracting:
```php
public fit(array $samples) : void
```

Return a sample matrix:
```php
public extract(array $samples) : array
```

##### Example:
```php
use Rubix\ML\Extractors\WordCountVectorizer;
use Rubix\ML\Datasets\Unlabeled;
use Rubix\ML\Datasets\Labeled;

...
$estractor = new WordCountVectorizer(5000);

$extractor->fit($data);

$samples = $extractor->extract($data);

$dataset = new Unlabeled($samples);

$dataset = new Labeled($samples, $labels);
```

### Image Patch Descriptor
This image extractor encodes various user-defined features called descriptors using subsamples of the original image called *patches*.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | descriptors | None | array | The descriptor middleware. Each descriptor encodes a set of features from a patch of the image. |
| 2 | size | [32, 32] | array | A tuple of width and height values denoting the resolution of the encoding. |
| 3 | patch size | [4, 4] | array | The width and height of the patch area. |
| 3 | driver | 'gd' | string | The PHP extension to use for image processing ('gd' *or* 'imagick'). |


##### Additional Methods:

Return the dimensionality of the vector that gets encoded:
```php
public numPatches() : int
```



### Word Count Vectorizer
In machine learning, word *counts* are often used to represent natural language as numerical vectors. The Word Count Vectorizer builds a vocabulary using hash tables from the training samples during fitting and transforms an array of strings (text *blobs*) into sparse feature vectors. Each feature column represents a word from the vocabulary and the value denotes the number of times that word appears in a given sample.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | max vocabulary | PHP_INT_MAX | int | The maximum number of words to encode into each word vector. |
| 2 | stop words | [ ] | array | An array of stop words i.e. words to filter out of the original text. |
| 3 | normalize | true | bool | Should we remove extra whitespace and lowercase? |
| 4 | tokenizer | Word | object | The object responsible for turning samples of text into individual tokens. |

##### Additional Methods:

Return the fitted vocabulary i.e. the words that will be vectorized:
```php
public vocabulary() : array
```

Return the size of the vocabulary:
```php
public size() : int
```

##### Example:
```php
use Rubix\ML\Extractors\ImagePatchDescriptor;
use Rubix\ML\Extractors\Descriptors\TextureHistogram;

$extractor = new ImagePatchDescriptor([
	new TextureHistorgram(),
], [32, 32], [4, 4], 'gd');
```

### Raw Pixel Encoder
The Raw Pixel Encoder takes an array of images (as [PHP Resources](http://php.net/manual/en/language.types.resource.php)) and converts them to a flat vector of raw color channel data. Scaling and cropping is handled automatically by [Intervention Image](http://image.intervention.io/) for PHP. Note that the GD extension is required to use this feature.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | size | [32, 32] | array | A tuple of width and height values denoting the resolution of the encoding. |
| 2 | rgb | true | bool | True to use RGB color channel data and False to use Greyscale. |
| 3 | driver | 'gd' | string | The PHP extension to use for image processing ('gd' *or* 'imagick'). |

##### Additional Methods:

Return the dimensionality of the vector that gets encoded:
```php
public dimensions() : int
```

##### Example:
```php
use Rubix\ML\Extractors\PixelEncoder;

$extractor = new PixelEncoder([28, 28], true, 'gd');
```

---
### Estimators
Estimators are the core of the Rubix library and consist of various [Classifiers](#classifiers), [Regressors](#regressors), [Clusterers](#clusterers), and [Anomaly Detectors](#anomaly-detectors) that make *predictions* based on their training. Estimators can be supervised or unsupervised depending on the task and can employ methods on top of the basic Estimator API by implementing a number of interfaces such as [Online](#online), [Probabilistic](#probabilistic), and [Persistable](#persistable). They can even be wrapped by a Meta-Estimator to provide additional functionality such as data [preprocessing](#pipeline) and [hyperparameter optimization](#grid-search).

To train an Estimator pass it a training Dataset:
```php
public train(Dataset $training) : void
```

To make predictions, pass it a new dataset:
```php
public predict(Dataset $dataset) : array
```

The return value of `predict()` is an array indexed in the order in which the samples were fed in.

##### Example:
```php
use Rubix\ML\Classifiers\RandomForest;
use Rubix\ML\Datasets\Labeled;

...
$dataset = new Labeled($samples, $labels);

$estimator = new RandomForest(200, 0.5, 5, 3);

// Take 3 samples out of the dataset to use later
$testing = $dataset->take(3);

// Train the estimator with the labeled dataset
$estimator->train($dataset);

// Make some predictions on the holdout set
$result = $estimator->predict($testing);

var_dump($result);
```

##### Output:
```sh
array(3) {
	[0] => 'married'
	[1] => 'divorced'
	[2] => 'married'
}
```

---
### Anomaly Detectors

[Anomaly detection](https://en.wikipedia.org/wiki/Anomaly_detection) is the process of identifying samples that do not conform to an expected pattern. They can be used in fraud prevention, intrusion detection, sciences, and many other areas. The output of a Detector is either *0* for a normal sample or *1* for a detected anomaly.

### Isolation Forest
An [Ensemble](#ensemble) Anomaly Detector comprised of [Isolation Trees](#isolation-tree) each trained on a different subset of the training set. The Isolation Forest works by averaging the isolation score of a sample across a user-specified number of trees.

##### Unsupervised | Probabilistic | Persistable | Nonlinear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | trees | 100 | int | The number of Isolation Trees to train in the ensemble. |
| 2 | ratio | 0.1 | float | The ratio of random samples to train each Isolation Tree with. |
| 3 | threshold | 0.5 | float | The threshold isolation score. i.e. the probability that a sample is an outlier. |

##### Additional Methods:
This Estimator does not have any additional methods.

##### Example:
```php
use Rubix\ML\AnomalyDetection\IsolationForest;

$estimator = new IsolationForest(500, 0.1, 0.7);
```
### Isolation Tree
Isolation Trees separate anomalous samples from dense clusters using an extremely randomized splitting process that isolates outliers into their own nodes. *Note* that this Estimator is considered a *weak* learner and is typically used within the context of an ensemble (such as [Isolation Forest](#isolation-forest)).

##### Unsupervised | Probabilistic | Persistable | Nonlinear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | max depth | PHP_INT_MAX | int | The maximum depth of a branch that is allowed. |
| 2 | threshold | 0.5 | float | The minimum isolation score. i.e. the probability that a sample is an outlier. |

##### Additional Methods:
This Estimator does not have any additional methods.

##### Example:
```php
use Rubix\ML\AnomalyDetection\IsolationTree;

$estimator = new IsolationTree(1000, 0.65);
```

### Local Outlier Factor
The Local Outlier Factor (LOF) algorithm considers the local region of a sample, set by the k parameter, when determining an outlier. A density estimate for each neighbor is computed by measuring the radius of the cluster centroid that the point and its neighbors form. The LOF is the ratio of the sample over the median radius of the local region.

##### Unsupervised | Probabilistic | Online | Persistable | Nonlinear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | k | 10 | int | The k nearest neighbors that form a local region. |
| 2 | neighbors | 20 | int | The number of neighbors considered when computing the radius of a centroid. |
| 3 | threshold | 0.5 | float | The minimum density score. i.e. the probability that a sample is an outlier. |
| 4 | kernel | Euclidean | object | The distance metric used to measure the distance between two sample points. |

##### Additional Methods:
This Estimator does not have any additional methods.

##### Example:
```php
use Rubix\ML\AnomalyDetection\LocalOutlierFactor;
use Rubix\ML\Kernels\Distance\Minkowski;

$estimator = new LocalOutlierFactor(10, 20, 0.2, new Minkowski(3.5));
```

### Robust Z Score
A quick *global* anomaly detector, Robust Z Score uses a modified Z score to detect outliers within a Dataset. The modified Z score consists of taking the median and median absolute deviation (MAD) instead of the mean and standard deviation thus making the statistic more robust to training sets that may already contain outliers. Outlier can be flagged in one of two ways. First, their average Z score can be above the user-defined tolerance level or an individual feature's score could be above the threshold (*hard* limit).

##### Unsupervised | Persistable

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | tolerance | 3.0 | float | The average z score to tolerate before a sample is considered an outlier. |
| 2 | threshold | 3.5 | float | The threshold z score of a individual feature to consider the entire sample an outlier. |

##### Additional Methods:

Return the median of each feature column in the training set:
```php
public medians() : array
```

Return the median absolute deviation (MAD) of each feature column in the training set:
```php
public mads() : array
```

##### Example:
```php
use Rubix\ML\AnomalyDetection\RobustZScore;

$estimator = new RobustZScore(1.5, 3.0);
```

---
### Classifiers
Classifiers are a type of Estimator that predict discrete outcomes such as class labels. There are two types of Classifiers in Rubix - *Binary* and *Multiclass*. Binary Classifiers can only distinguish between two classes (ex. *Male*/*Female*, *Yes*/*No*, etc.) whereas a Multiclass Classifier is able to handle two or more unique class outcomes.

### AdaBoost
Short for Adaptive Boosting, this ensemble classifier can improve the performance of an otherwise *weak* classifier by focusing more attention on samples that are harder to classify.

##### Supervised | Binary | Persistable

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | base | None | string | The fully qualified class name of the base *weak* classifier. |
| 2 | params | [ ] | array | The parameters of the base classifier. |
| 3 | estimators | 100 | int | The number of estimators to train in the ensemble. |
| 4 | ratio | 0.1 | float | The ratio of samples to subsample from the training dataset per epoch. |
| 5 | tolerance | 1e-3 | float | The amount of validation error to tolerate before an early stop is considered. |

##### Additional Methods:

Return the calculated weight values of the last trained dataset:
```php
public weights() : array
```

Return the influence scores for each boosted classifier:
```php
public influence() : array
```

##### Example:
```php
use Rubix\ML\Classifiers\AdaBoost;
use Rubix\ML\Classifiers\ExtraTreeClassifier;

$estimator = new AdaBoost(ExtraTreeClassifier::class, [10, 3, 5], 200, 0.1, 1e-2);
```

### Classification Tree
A tree-based classifier that minimizes [gini impurity](https://en.wikipedia.org/wiki/Gini_coefficient) to greedily search for the best splits in a training set.

##### Supervised | Multiclass | Probabilistic | Persistable | Nonlinear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | max depth | PHP_INT_MAX | int | The maximum depth of a branch that is allowed. Setting this to 1 is equivalent to training a Decision Stump. |
| 2 | max leaf size | 5 | int | The maximum number of samples that a leaf node can contain. |
| 3 | max features | PHP_INT_MAX | int | The maximum number of features to consider when determining a split point. |
| 4 | tolerance | 1e-3 | float | A small amount of impurity to tolerate when choosing a split. |

##### Additional Methods:
This Estimator does not have any additional methods.

##### Example:
```php
use Rubix\ML\Classifiers\ClassificationTree;

$estimator = new ClassificationTree(100, 7, 4, 1e-4);
```

### Committee Machine
A voting ensemble that aggregates the predictions of a committee of heterogeneous classifiers (called *experts*). The committee uses a user-specified influence-based scheme to make final predictions. Influence values can be arbitrary as they are normalized anyways upon object creation.

##### Supervised | Ensemble | Probabilistic | Persistable

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | experts | None | array | An array of classifiers instances that will comprise the committee. |
| 2 | influence | None | array | The influence values of each expert in the committee. |


##### Additional Methods:
This Meta Estimator does not have any additional methods.

##### Example:
```php
use Rubix\ML\Classifiers\CommitteeMachine;
use Rubix\ML\Classifiers\RandomForest;
use Rubix\ML\Classifiers\SoftmaxClassifier;
use Rubix\ML\NeuralNet\Optimizers\Adam;
use Rubix\ML\Classifiers\KNearestNeighbors;

$estimator = new CommitteeMachine([
	new RandomForest(100, 0.3, 30, 3, 4, 1e-3),
	new SoftmaxClassifier(50, new Adam(0.001), 0.1),
	new KNearestNeighbors(3),
], [
	4, 6, 5, // Arbitrary influence values for each expert
]);
```

### Dummy Classifier
A classifier that uses a user-defined [Guessing Strategy](#guessing-strategies) to make predictions. Dummy Classifier is useful to provide a sanity check and to compare performance with an actual classifier.

##### Supervised | Multiclass | Persistable

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | strategy | PopularityContest | object | The guessing strategy to employ when guessing the outcome of a sample. |

##### Additional Methods:
This Estimator does not have any additional methods.

##### Example:
```php
use Rubix\ML\Classifiers\DummyClassifier;
use Rubix\ML\Other\Strategies\PopularityContest;

$estimator = new DummyClassifier(new PopularityContest());
```

### Extra Tree Classifier
An Extremely Randomized Classification Tree that splits the training set at a random point chosen among the maximum features. Extra Trees work great in Ensembles such as [Random Forest](#random-forest) or [AdaBoost](#adaboost) as the "weak" classifier or they can be used on their own. The strength of Extra Trees are computational efficiency as well as increasing variance of the prediction (if that is desired).

##### Supervised | Multiclass | Probabilistic | Persistable | Nonlinear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | max depth | PHP_INT_MAX | int | The maximum depth of a branch that is allowed. |
| 2 | max leaf size | 5 | int | The maximum number of samples that a leaf node can contain. |
| 3 | max features | PHP_INT_MAX | int | The number of features to consider when determining a split. |
| 4 | tolerance | 1e-3 | float | A small amount of impurity to tolerate when choosing a split. |

##### Additional Methods:
This Estimator does not have any additional methods.

##### Example:
```php
use Rubix\ML\Classifiers\ExtraTreeClassifier;

$estimator = new ExtraTreeClassifier(50, 3, 4);
```

### Gaussian Naive Bayes
A variate of the [Naive Bayes](#naive-bayes) classifier that uses a probability density function (*PDF*) over continuous features. The distribution of values is assumed to be Gaussian therefore your data might need to be transformed beforehand if it is not normally distributed.

##### Supervised | Multiclass | Online | Probabilistic | Persistable | Nonlinear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | priors | true | bool | Should we compute the empirical prior probabilities of the class outcomes? |
| 2 | epsilon | 1e-8 | float | A small amount of smoothing to apply to the variance of each Gaussian for numerical stability. |

##### Additional Methods:

Return the class prior log probabilities based on their weight over all training samples:
```php
public priors() : array
```

Return the running mean of each feature column for each class:
```php
public means() : array
```

Return the running variance of each feature column for each class:
```php
public variances() : array
```

##### Example:
```php
use Rubix\ML\Classifiers\GaussianNB;

$estimator = new GaussianNB(true, 1e-2);
```

### K-d Neighbors
A fast [K Nearest Neighbors](#k-nearest-neighbors) approximating Estimator that uses a K-d tree to divide the training set into neighborhoods whose max size are constrained by the *neighborhood* hyperparameter. K-d Neighbors does a binary search to locate the nearest neighborhood and then searches  only the points in the neighborhood for the nearest k to make a prediction. Since there may be points in other neighborhoods that may be closer, the nearest neighbor search is said to be *approximation*. The main advantage K-d Neighbors has over regular KNN is that it is much faster.

##### Supervised | Multiclass | Probabilistic | Persistable | Nonlinear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | k | 3 | int | The number of neighboring training samples to consider when making a prediction. |
| 2 | neighborhood | 10 | int | The max size of a neighborhood. |
| 3 | kernel | Euclidean | object | The distance kernel used to measure the distance between two sample points. |

##### Additional Methods:
This Estimator does not have any additional methods.

##### Example:
```php
use Rubix\ML\Classifiers\KDNeighbors;
use Rubix\ML\Kernels\Distance\Euclidean;

$estimator = new KDNeighbors(3, 10, new Euclidean());
```

### K Nearest Neighbors
A distance-based algorithm that locates the K nearest neighbors from the training set and uses a majority vote to classify the unknown sample. K Nearest Neighbors is considered a *lazy* learning Estimator because it does the majority of its computation at prediction time. The advantage KNN has over [KD Neighbors](#k-d-neighbors)  is that it is more precise and capable of online learning.

##### Supervised | Multiclass | Probabilistic | Online | Persistable | Nonlinear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | k | 5 | int | The number of neighboring training samples to consider when making a prediction. |
| 2 | kernel | Euclidean | object | The distance kernel used to measure the distance between two sample points. |

##### Additional Methods:
This Estimator does not have any additional methods.

##### Example:
```php
use Rubix\ML\Classifiers\KNearestNeighbors;
use Rubix\ML\Kernels\Distance\Euclidean;

$estimator = new KNearestNeighbors(3, new Euclidean());
```

### Logistic Regression
A type of linear classifier that uses the logistic (sigmoid) function to distinguish between two possible outcomes. Logistic Regression measures the relationship between the class label and one or more independent variables by estimating probabilities.

##### Supervised | Binary | Online | Probabilistic | Persistable | Linear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | epochs | 100 | int | The maximum number of training epochs to execute. |
| 2 | batch size | 10 | int | The number of training samples to process at a time. |
| 3 | optimizer | Adam | object | The gradient descent optimizer used to train the underlying network. |
| 4 | alpha | 1e-4 | float | The amount of L2 regularization to apply to the weights of the network. |
| 5 | cost fn | Cross Entropy | object | The function that computes the cost of an erroneous activation during training. |
| 6 | min change | 1e-4 | float | The minimum change in the cost function necessary to continue training. |

##### Additional Methods:

Return the average cost of a sample at each epoch of training:
```php
public steps() : array
```

Return the underlying neural network instance or *null* if untrained:
```php
public network() : Network|null
```

##### Example:
```php
use Rubix\ML\Classifers\LogisticRegression;
use Rubix\ML\NeuralNet\Optimizers\Adam;
use Rubix\ML\NeuralNet\CostFunctions\Exponential;

$estimator = new LogisticRegression(200, 10, new Adam(0.001), 1e-4, new Exponential(), 1e-4);
```

### Multi Layer Perceptron
A multiclass feedforward [Neural Network](#neural-network) classifier that uses a series of user-defined [Hidden Layers](#hidden) as intermediate computational units. Multiple layers and non-linear activation functions allow the Multi Layer Perceptron to handle complex non-linear problems. MLP also features progress monitoring which stops training when it can no longer make progress. It also utilizes [snapshotting](#snapshots) to make sure that it always uses the best parameters even if progress may have declined during training.

##### Supervised | Multiclass | Online | Probabilistic | Persistable | Nonlinear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | hidden | [ ] | array | An array of hidden layers of the neural network. |
| 2 | batch size | 50 | int | The number of training samples to process at a time. |
| 3 | optimizer | Adam | object | The gradient descent optimizer used to train the underlying network. |
| 4 | alpha | 1e-4 | float | The amount of L2 regularization to apply to the weights of the network. |
| 5 | cost fn | Cross Entropy | object | The function that computes the cost of an erroneous activation during training. |
| 6 | min change | 1e-4 | float | The minimum change in the cost function necessary to continue training. |
| 7 | metric | Accuracy | object | The validation metric used to monitor the training progress of the network. |
| 8 | holdout | 0.1 | float | The ratio of samples to hold out for progress monitoring. |
| 9 | window | 3 | int | The number of epochs to consider when determining if the algorithm should terminate or keep training. |
| 10 | epochs | PHP_INT_MAX | int | The maximum number of training epochs to execute. |

##### Additional Methods:

Return the average cost of a sample at each epoch of training:
```php
public steps() : array
```

Return the validation scores at each epoch of training:
```php
public scores() : array
```

Returns the underlying neural network instance or *null* if untrained:
```php
public network() : Network|null
```

##### Example:
```php
use Rubix\ML\Classifiers\MultiLayerPerceptron;
use Rubix\ML\NeuralNet\Layers\Dense;
use Rubix\ML\NeuralNet\ActivationFunctions\ELU;
use Rubix\ML\NeuralNet\Optimizers\Adam;
use Rubix\ML\NeuralNet\CostFunctions\CrossEntropy;
use Rubix\ML\CrossValidation\Metrics\MCC;

$estimator = new MultiLayerPerceptron([
	new Dense(30, new ELU()),
	new Dense(30, new ELU()),
	new Dense(30, new ELU()),
], 100, new Adam(0.001), 1e-4, new CrossEntropy(), 1e-3, new MCC(), 0.1, 3, PHP_INT_MAX);
```

### Naive Bayes
Probability-based classifier that uses probabilistic inference to derive the predicted class. The posterior probabilities are calculated using [Bayes' Theorem](https://en.wikipedia.org/wiki/Bayes%27_theorem). and the naive part relates to the fact that it assumes that all features are independent. In practice, the independent assumption tends to work out most of the time despite most features being correlated in the real world.

##### Supervised | Multiclass | Online | Probabilistic | Persistable | Nonlinear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | alpha | 1.0 | float | The amount of additive (Laplace/Lidstone) smoothing to apply to the probabilities. |
| 2 | priors | true | bool | Should we compute the empirical prior probabilities of the class outcomes? |

##### Additional Methods:

Returns the class prior log probabilities based on their weight over all training samples:
```php
public priors() : array
```

Return the log probabilities of each feature given each class label:
```php
public probabilities() : array
```

##### Example:
```php
use Rubix\ML\Classifiers\NaiveBayes;

$estimator = new NaiveBayes(0.5, true);
```

### Random Forest
[Ensemble](#ensemble) classifier that trains Decision Trees ([Classification Trees](#classification-tree) or [Extra Trees](#extra-tree)) on a random subset (*bootstrap*) of the training data. A prediction is made based on the probability scores returned from each tree in the forest weighted equally.

##### Supervised | Multiclass | Probabilistic | Persistable | Nonlinear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | trees | 100 | int | The number of Decision Trees to train in the ensemble. |
| 2 | ratio | 0.1 | float | The ratio of random samples to train each Decision Tree with. |
| 3 | max depth | 10 | int | The maximum depth of a branch that is allowed. Setting this to 1 is equivalent to training a Decision Stump. |
| 4 | min samples | 5 | int | The minimum number of data points needed to split a decision node. |
| 5 | max features | PHP_INT_MAX | int | The number of features to consider when determining a split. |
| 6 | tolerance | 1e-3 | float | A small amount of Gini impurity to tolerate when choosing a split. |
| 7 | base | ClassificationTree::class | string | The base tree class name. |

##### Additional Methods:
This Estimator does not have any additional methods.

##### Example:
```php
use Rubix\ML\Classifiers\RandomForest;
use Rubix\ML\Classifiers\ClassificationTree;

$estimator = new RandomForest(400, 0.1, 10, 3, 5, 1e-2, ClassificationTree::class);
```

### Softmax Classifier
A generalization of [Logistic Regression](#logistic-regression) for multiclass problems using a single layer [neural network](#neural-network) with a Softmax output layer.

##### Supervised | Multiclass | Online | Probabilistic | Persistable | Linear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | epochs | 100 | int | The maximum number of training epochs to execute. |
| 2 | batch size | 10 | int | The number of training samples to process at a time. |
| 3 | optimizer | Adam | object | The gradient descent optimizer used to train the underlying network. |
| 4 | alpha | 1e-4 | float | The amount of L2 regularization to apply to the weights of the network. |
| 5 | cost fn | Cross Entropy | object | The function that computes the cost of an erroneous activation during training. |
| 6 | min change | 1e-4 | float | The minimum change in the cost function necessary to continue training. |

##### Additional Methods:

Return the average cost of a sample at each epoch of training:
```php
public steps() : array
```

Return the underlying neural network instance or *null* if untrained:
```php
public network() : Network|null
```

##### Example:
```php
use Rubix\ML\Classifiers\SoftmaxClassifier;
use Rubix\ML\NeuralNet\Optimizers\Momentum;
use Rubix\ML\NeuralNet\CostFunctions\CrossEntropy;

$estimator = new SoftmaxClassifier(300, 100, new Momentum(0.001), 1e-4, new CrossEntropy(), 1e-5);
```

---
### Clusterers
Clustering is a common technique in machine learning that focuses on grouping samples in such a way that the groups are similar. Clusterers take unlabeled data points and assign them a label (cluster). The return value of each prediction is the cluster number each sample was assigned to.

### DBSCAN
Density-Based Spatial Clustering of Applications with Noise is a clustering algorithm able to find non-linearly separable and arbitrarily-shaped clusters. In addition, DBSCAN also has the ability to mark outliers as *noise* and thus can be used as a quasi [Anomaly Detector](#anomaly-detectors) as well.

##### Unsupervised | Persistable | Nonlinear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | radius | 0.5 | float | The maximum radius between two points for them to be considered in the same cluster. |
| 2 | min density | 5 | int | The minimum number of points within radius of each other to form a cluster. |
| 3 | kernel | Euclidean | object | The distance metric used to measure the distance between two sample points.

##### Additional Methods:
This Estimator does not have any additional methods.

##### Example:
```php
use Rubix\ML\Clusterers\DBSCAN;
use Rubix\ML\Kernels\Distance\Diagonal;

$estimator = new DBSCAN(4.0, 5, new Diagonal());
```
### Fuzzy C Means
Distance-based clusterer that allows samples to belong to multiple clusters if they fall within a fuzzy region defined by the fuzz parameter. Fuzzy C Means is similar to both K Means and Gaussian Mixture Models in that they require a priori knowledge of the number (parameter *c*) of clusters.

##### Unsupervised | Probabilistic | Persistable

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | c | None | int | The number of target clusters. |
| 2 | fuzz | 2.0 | float | Determines the bandwidth of the fuzzy area. |
| 3 | kernel | Euclidean | object | The distance metric used to measure the distance between two sample points. |
| 4 | min change | 1e-4 | float | The minimum change in inter cluster distance necessary for the algorithm to continue training. |
| 5 | epochs | PHP_INT_MAX | int | The maximum number of training rounds to execute. |

##### Additional Methods:

Return the *c* computed centroids of the training data:
```php
public centroids() : array
```

Returns the inter-cluster distances at each epoch of training:
```php
public steps() : array
```

##### Example:
```php
use Rubix\ML\Clusterers\FuzzyCMeans;
use Rubix\ML\Kernels\Distance\Euclidean;

$estimator = new FuzzyCMeans(5, 1.2, new Euclidean(), 1e-3, 1000);
```

### Gaussian Mixture
A Gaussian Mixture model is a probabilistic model for representing the presence of clusters within an overall population without requiring a sample to know which sub-population it belongs to a priori. GMMs are similar to centroid-based clusterers like [K Means](#k-means) but allow not just the centers (*means*) to be learned but the radii (*variances*) as well.

##### Unsupervised | Probabilistic | Persistable

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | k | None | int | The number of target clusters. |
| 2 | min change | 1e-3 | float | The minimum change in the Gaussians necessary for the algorithm to continue training. |
| 3 | epochs | 100 | int | The maximum number of training rounds to execute. |

##### Additional Methods:

Return the cluster prior probabilities based on their representation over all training samples:
```php
public priors() : array
```

Return the running means of each feature column for each cluster:
```php
public means() : array
```

Return the variance of each feature column for each cluster:
```php
public variances() : array
```

##### Example:
```php
use Rubix\ML\Clusterers\FuzzyCMeans;
use Rubix\ML\Kernels\Distance\Euclidean;

$estimator = new FuzzyCMeans(5, 1.2, new Euclidean(), 1e-3, 1000);
```

### K Means
A fast centroid-based hard clustering algorithm capable of clustering linearly separable data points given a number of target clusters set by the parameter K.

##### Unsupervised | Online | Persistable | Linear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | k | None | int | The number of target clusters. |
| 2 | kernel | Euclidean | object | The distance metric used to measure the distance between two sample points. |
| 3 | epochs | PHP_INT_MAX | int | The maximum number of training rounds to execute. |

##### Additional Methods:

Return the *c* computed centroids of the training data:
```php
public centroids() : array
```

##### Example:
```php
use Rubix\ML\Clusterers\KMeans;
use Rubix\ML\Kernels\Distance\Euclidean;

$estimator = new KMeans(3, new Euclidean());
```

### Mean Shift
A hierarchical clustering algorithm that uses peak finding to locate the local maxima (centroids) of a training set given by a radius constraint.

##### Unsupervised | Persistable | Linear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | radius | None | float | The radius of each cluster centroid. |
| 2 | kernel | Euclidean | object | The distance metric used to measure the distance between two sample points. |
| 3 | threshold | 1e-8 | float | The minimum change in centroid means necessary for the algorithm to continue training. |
| 4 | epochs | 100 | int | The maximum number of training rounds to execute. |


##### Additional Methods:

Return the *c* computed centroids of the training data:
```php
public centroids() : array
```

Returns the amount of centroid shift during each epoch of training:
```php
public steps() : array
```

##### Example:
```php
use Rubix\ML\Clusterers\MeanShift;
use Rubix\ML\Kernels\Distance\Diagonal;

$estimator = new MeanShift(3.0, new Diagonal(), 1e-6, 2000);
```

---
### Regressors
Regression analysis is used to predict the outcome of an event where the value is continuous.

### Adaline
Adaptive Linear Neuron is a type of single layer [neural network](#neural-network) with a [linear output layer](#linear).

##### Supervised | Online | Persistable | Linear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | epochs | 100 | int | The maximum number of training epochs to execute. |
| 2 | batch size | 10 | int | The number of training samples to process at a time. |
| 3 | optimizer | Adam | object | The gradient descent optimizer used to train the underlying network. |
| 4 | alpha | 1e-4 | float | The amount of L2 regularization to apply to the weights of the network. |
| 5 | cost fn | Least Squares | object | The function that computes the cost of an erroneous activation during training. |
| 6 | min change | 1e-4 | float | The minimum change in the cost function necessary to continue training. |

##### Additional Methods:

Return the average cost of a sample at each epoch of training:
```php
public steps() : array
```

Return the underlying neural network instance or *null* if untrained:
```php
public network() : Network|null
```

##### Example:
```php
use Rubix\ML\Classifers\Adaline;
use Rubix\ML\NeuralNet\Optimizers\Adam;
use Rubix\ML\NeuralNet\CostFunctions\LeastSquares;

$estimator = new Adaline(300, 10, new Adam(0.001), 1e-6, new LeastSquares(), 1e-4);
```

### Dummy Regressor
Regressor that guesses the output values based on a [Guessing Strategy](#guessing-strategies). Dummy Regressor is useful to provide a sanity check and to compare performance against actual Regressors.

##### Supervised | Persistable

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | strategy | Blurry Mean | object | The guessing strategy to employ when guessing the outcome of a sample. |

##### Additional Methods:
This Estimator does not have any additional methods.

##### Example:
```php
use Rubix\ML\Regressors\DummyRegressor;
use Rubix\ML\Other\Strategies\BlurryMedian;

$estimator = new DummyRegressor(new BlurryMedian(0.2));
```

### Extra Tree Regressor
An Extremely Randomized Regression Tree. Extra Trees differ from standard Regression Trees in that they choose a random split drawn from max features. When max features is set to 1 this amounts to building a totally random tree. Extra Tree can be used in an Ensemble, such as [Bootstrap Aggregator](#bootstrap-aggregator), or by itself, however, it is generally considered a weak learner by itself.

##### Supervised | Persistable | Nonlinear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | max depth | PHP_INT_MAX | int | The maximum depth of a branch that is allowed. |
| 2 | max leaf size | 5 | int | The maximum number of samples that a leaf node can contain. |
| 3 | max features | PHP_INT_MAX | int | The number of features to consider when determining a split. |
| 4 | tolerance | 1e-4 | float | A small amount of impurity to tolerate when choosing a split. |

##### Additional Methods:
This Estimator does not have any additional methods.

##### Example:
```php
use Rubix\ML\Classifiers\ExtraTreeRegressor;

$estimator = new ExtraTreeRegressor(100, 3, 20, 1e-4);
```

### K-d Neighbors Regressor
A fast implementation of [KNN Regressor](#knn-regressor) using a K-d tree. The KDN Regressor works by locating the neighborhood of a sample via binary search and then does a brute force search only on the samples in the neighborhood. The advantage of K-d Neighbors over KNN is speed and added variance to the predictions (if that is desired).

##### Supervised  | Persistable | Nonlinear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | k | 3 | int | The number of neighboring training samples to consider when making a prediction. |
| 2 | neighborhood | 10 | int | The max size of a neighborhood. |
| 3 | kernel | Euclidean | object | The distance kernel used to measure the distance between two sample points. |

##### Additional Methods:
This Estimator does not have any additional methods.

##### Example:
```php
use Rubix\ML\Regressors\KDNRegressor;
use Rubix\ML\Kernels\Distance\Euclidean;

$estimator = new KDNRegressor(5, 20, new Euclidean());
```

### KNN Regressor
A version of [K Nearest Neighbors](#k-nearest-neighbors) that uses the mean outcome of K nearest data points to make continuous valued predictions suitable for regression problems. The advantage of KNN Regressor over [KDN Regressor](#k-d-neighbors-regressor) is that it is more precise and capable of online learning.

##### Supervised | Online | Persistable | Nonlinear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | k | 5 | int | The number of neighboring training samples to consider when making a prediction. |
| 2 | kernel | Euclidean | object | The distance kernel used to measure the distance between two sample points. |

##### Additional Methods:
This Estimator does not have any additional methods.

##### Example:
```php
use Rubix\ML\Regressors\KNNRegressor;
use Rubix\ML\Kernels\Distance\Minkowski;

$estimator = new KNNRegressor(2, new Minkowski(3.0));
```

### MLP Regressor
A [Neural Network](#neural-network) with a linear output layer suitable for regression problems. The MLP also features progress monitoring which stops training when it can no longer make progress. It also utilizes [snapshotting](#snapshots) to make sure that it always uses the best parameters even if progress declined during training.

##### Supervised | Persistable | Nonlinear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | hidden | [ ] | array | An array of hidden layers of the neural network. |
| 2 | batch size | 50 | int | The number of training samples to process at a time. |
| 3 | optimizer | Adam | object | The gradient descent optimizer used to train the underlying network. |
| 4 | alpha | 1e-4 | float | The amount of L2 regularization to apply to the weights of the network. |
| 5 | cost fn | Least Squares | object | The function that computes the cost of an erroneous activation during training. |
| 6 | min change | 1e-4 | float | The minimum change in the cost function necessary to continue training. |
| 7 | metric | Accuracy | object | The validation metric used to monitor the training progress of the network. |
| 8 | holdout | 0.1 | float | The ratio of samples to hold out for progress monitoring. |
| 9 | window | 3 | int | The number of epochs to consider when determining if the algorithm should terminate or keep training. |
| 10 | epochs | PHP_INT_MAX | int | The maximum number of training epochs to execute. |


##### Additional Methods:

Return the average cost of a sample at each epoch of training:
```php
public steps() : array
```

Return the validation scores at each epoch of training:
```php
public scores() : array
```

Returns the underlying neural network instance or *null* if untrained:
```php
public network() : Network|null
```

##### Example:
```php
use Rubix\ML\Regressors\MLPRegressor;
use Rubix\ML\NeuralNet\Layers\Dense;
use Rubix\ML\NeuralNet\ActivationFunctions\SELU;
use Rubix\ML\NeuralNet\Optimizers\RMSProp;
use Rubix\ML\CrossValidation\Metrics\MeanSquaredError;

$estimator = new MLPRegressor([
	new Dense(50, new SELU()),
	new Dense(50, new SELU()),
	new Dense(50, new SELU()),
], 50, new RMSProp(0.001), 1e-2, new LeastSquares(), 1e-5, new MeanSquaredError(), 0.1, 3, 100);
```

### Regression Tree
A Decision Tree learning algorithm that performs greedy splitting by minimizing the sum of squared errors between decision node splits.

##### Supervised | Persistable | Nonlinear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | max depth | PHP_INT_MAX | int | The maximum depth of a branch that is allowed. |
| 2 | max leaf size | 5 | int | The maximum number of samples that a leaf node can contain. |
| 3 | max features | PHP_INT_MAX | int | The maximum number of features to consider when determining a split point. |
| 4 | tolerance | 1e-4 | float | A small amount of impurity to tolerate when choosing a split. |

##### Additional Methods:
This Estimator does not have any additional methods.

##### Example:
```php
use Rubix\ML\Regressors\RegressionTree;

$estimator = new RegressionTree(80, 1, 10, 0.0);
```

### Ridge
L2 penalized least squares linear regression. Can be used for simple regression problems that can be fit to a straight line.

##### Supervised | Persistable | Linear

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | alpha | 1.0 | float | The L2 regularization parameter. |

##### Additional Methods:

Return the y intercept of the computed regression line:
```php
public intercept() : float|null
```

Return the computed coefficients of the regression line:
```php
public coefficients() : array
```

##### Example:
```php
use Rubix\ML\Regressors\Ridge;

$estimator = new Ridge(2.0);
```

---
### Meta-Estimators
Meta-Estimators allow you to progressively enhance your models by adding additional functionality such as [data preprocessing](#data-preprocessing) and [persistence](#model-persistence) or by orchestrating an [Ensemble](#ensemble) of base Estimators. Each Meta-Estimator wraps a base Estimator and you can even wrap certain Meta-Estimators with other Meta-Estimators. Some examples of Meta-Estimators in Rubix are [Pipeline](#pipeline), [Grid Search](#grid-search), and [Bootstrap Aggregator](#bootstrap-aggregator).

##### Example:
```php
use Rubix\ML\Pipeline;
use Rubix\ML\GridSearch;
use Rubix\ML\Classifiers\ClassificationTree;
use Rubix\ML\CrossValidation\Metrics\MCC;
use Rubix\ML\CrossValidation\KFold;
use Rubix\ML\Transformers\NumericStringConverter;

...
$params = [[10, 30, 50], [1, 3, 5], [2, 3, 4];

$estimator = new Pipeline(new GridSearch(ClassificationTree::class, $params, new MCC(), new KFold(10)));

$estimator->train($dataset); // Train a classification tree with preprocessing and grid search

$estimator->complexity(); // Call complexity() method on Decision Tree from Pipeline
```

### Data Preprocessing
Often, additional processing of input data is required to deliver correct predictions and/or accelerate the training process. In this section, we'll introduce the Pipeline meta-Estimator and the various [Transformers](#transformers) that it employs to fit the input data to suit the requirements and preferences of the [Estimator](#estimator) that it feeds.

### Pipeline
Pipeline is responsible for transforming the input sample matrix of a Dataset in such a way that can be processed by the base Estimator. Pipeline accepts a base Estimator and a list of Transformers to apply to the input data before it is fed to the learning algorithm. Under the hood, Pipeline will automatically fit the training set upon training and transform any [Dataset object](#dataset-objects) supplied as an argument to one of the base Estimator's methods, including `predict()`.

##### Classifiers, Regressors, Clusterers, Anomaly Detectors

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | estimator | None | object | An instance of a base estimator. |
| 2 | transformers | [ ] | array | The transformer middleware to be applied to each dataset. |

##### Additional Methods:
This Meta Estimator does not have any additional methods.

##### Example:
```php
use Rubix\ML\Pipeline;
use Rubix\ML\Classifiers\SoftmaxClassifier;
use Rubix\ML\NeuralNet\Optimizer\RMSProp;
use Rubix\ML\Transformers\MissingDataImputer;
use Rubix\ML\Transformers\OneHotEncoder;
use Rubix\ML\Transformers\SparseRandomProjector;

$estimator = new Pipeline(new SoftmaxClassifier(100, new RMSProp(0.01), 1e-2), [
	new MissingDataImputer(),
	new OneHotEncoder(),
	new SparseRandomProjector(30),
]);

$estimator->train($dataset); // Datasets are fit and ...

$estimator->predict($samples); // transformed automatically.
```

Transformer *middleware* will process in the order given when the Pipeline was built and cannot be reordered without instantiating a new one. Since Transformers run sequentially, the order in which they run *matters*. For example, a Transformer near the end of the stack may depend on a previous Transformer to convert all categorical features into continuous ones before it can run.

In practice, applying transformations can drastically improve the performance of your model by cleaning, scaling, expanding, compressing, and normalizing the input data.

### Ensemble
Ensemble Meta Estimators train and orchestrate a number of base Estimators in order to make their predictions. Certain Estimators (like [AdaBoost](#adaboost) and [Random Forest](#random-forest)) are implemented as Ensembles under the hood, however these *Meta* Estimators are able to work across Estimator types which makes them very useful.

### Bootstrap Aggregator
Bootstrap Aggregating (or *bagging*) is a model averaging technique designed to improve the stability and performance of a user-specified base Estimator by training a number of them on a unique bootstrapped training set. Bootstrap Aggregator then collects all of their predictions and makes a final prediction based on the results.

##### Classifiers, Regressors, Anomaly Detectors

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | base | None | string | The fully qualified class name of the base Estimator. |
| 2 | params | [ ] | array | The parameters of the base estimator. |
| 3 | estimators | 10 | int | The number of base estimators to train in the ensemble. |
| 4 | ratio | 0.5 | float | The ratio of random samples to train each estimator with. |

##### Additional Methods:
This Meta Estimator does not have any additional methods.

##### Example:
```php
use Rubix\ML\BootstrapAggregator;
use Rubix\ML\Regressors\RegressionTree;

...
$estimator = new BootstrapAggregator(RegressionTree::class, [10, 5, 3], 100, 0.2);

$estimator->traing($training); // Trains 100 regression trees

$estimator->predict($testing); // Aggregates their predictions
```

### Model Selection
Model selection is the task of selecting a version of a model with a hyperparameter combination that maximizes performance on a specific validation metric. Rubix provides the *Grid Search* meta-Estimator that performs an exhaustive search over all combinations of parameters given as possible arguments.

### Grid Search
Grid Search is an algorithm that optimizes hyperparameter selection. From the user's perspective, the process of training and predicting is the same, however, under the hood, Grid Search trains one [Estimator](#estimators) per combination of parameters and predictions are made using the best Estimator. You can access the scores for each parameter combination by calling the `results()` method on the trained Grid Search meta-Estimator or you can get the best parameters by calling `best()`.

You can chose which parameters to search manually or you can generate parameters  to be used with Grid Search using the [Params](#params) helper.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | base | None | string | The fully qualified class name of the base Estimator. |
| 2 | params | [ ] | array | An array containing n-tuples of parameters where each tuple (array) represents a possible parameter for a given parameter location (ordinal). |
| 3 | metric | None | object | The validation metric used to score each set of parameters. |
| 4 | validator | None | object | An instance of a Validator object (HoldOut, KFold, etc.) that will be used to test each parameter combination. |

##### Additional Methods:

Return the results (scores and parameters) of the last search:
```php
public results() : array
```

Return the he parameters with the highest validation score:
```php
public best() : array
```

Return the underlying estimator trained with the best parameters:
```php
public estimator() : Estimator
```

##### Example:
```php
use Rubix\ML\GridSearch;
use Rubix\ML\Classifiers\KNearestNeighbors;
use Rubix\ML\Kernels\Distance\Euclidean;
use Rubix\ML\Kernels\Distance\Manhattan;
use Rubix\ML\CrossValidation\Metrics\Accuracy;
use Rubix\ML\CrossValidation\KFold;

...
$params = [
	[1, 3, 5, 10], [new Euclidean(), new Manhattan()], // Tuples containing possible params at that constructor position
];

$estimator = new GridSearch(KNearestNeightbors::class, $params, new Accuracy(), new KFold(10));

$estimator->train($dataset); // Train one estimator per parameter combination

var_dump($estimator->best()); // Return the best hyper-parmeters
```

##### Output:
```sh
array(2) {
  [0]=> int(5)
  [1]=> object(Rubix\ML\Kernels\Distance\Euclidean)#15 (0) {
  }
}
```

### Model Persistence
Model persistence is the practice of saving a trained model to disk so that it can be restored later, on a different machine, or used in an online system. Rubix persists your models using built in PHP object serialization (similar to pickling in Python). Most Estimators are persistable, but some are not allowed due to their poor storage complexity.

### Persistent Model
It is possible to persist a model to disk by wrapping the Estimator instance in a Persistent Model meta-Estimator. The Persistent Model class gives the Estimator two additional methods `save()` and `restore()` that serialize and unserialize to and from disk. In order to be persisted the Estimator must implement the Persistable interface.

```php
public save(string $path) : bool
```
Where path is the location of the directory where you want the model saved. `save()` will return true if the model was successfully persisted and false if it failed.

```php
public static restore(string $path) : self
```
The restore method will return an instantiated model from the save path.

##### Example:
```php
use Rubix\ML\PersistentModel;
use Rubix\ML\Classifiers\RandomForest;

$estimator = new PersistentModel(new RandomForest(100, 0.2, 10, 3));

$estimator->save('path/to/models/folder/random_forest.model');

$estimator->save(); // Saves to current working directory under unique filename

$estimator = PersistentModel::restore('path/to/models/folder/random_forest.model');
```

---
### Estimator Interfaces

### Online

Certain [Estimators](#estimators) that implement the *Online* interface can be trained in batches. Estimators of this type are great for when you either have a continuous stream of data or a dataset that is too large to fit into memory. Partial training allows the model to grow as new data is acquired.

You can partially train an Online Estimator with:
```php
public partial(Dataset $dataset) : void
```

##### Example:
```php
...
$datasets = $dataset->fold(3);

$estimator->partial($dataset[0]);

$estimator->partial($dataset[1]);

$estimator->partial($dataset[2]);
```

It is *important* to note that an Estimator will continue to train as long as you are using the `partial()` method, however, calling `train()` on a trained or partially trained Estimator will reset it back to baseline first.

---
### Probabilistic

Some [Estimators](#estimators) may implement the *Probabilistic* interface, in which case, they will have an additional method that returns an array of probability scores of each possible class, cluster, etc. Probabilities are useful for ascertaining the degree to which the Estimator is certain about a particular outcome.

Calculate probability estimates:
```php
public proba(Dataset $dataset) : array
```

##### Example:
```php
...
$probabilities = $estimator->proba($dataset->head(2));  

var_dump($probabilities);
```

##### Output:
```sh
array(2) {
	[0] => array(2) {
		['married'] => 0.975,
		['divorced'] => 0.025,
	}
	[1] => array(2) {
		['married'] => 0.200,
		['divorced'] => 0.800,
	}
}
```

---
### Transformers
Transformers take a sample matrices and transform them in various ways. A common transformation is scaling and centering the values using one of the Standardizers ([Z Scale](#z-scale-standardizer), [Robust](#robust-standardizer), [Quartile](#quartile-standardizer)). Transformers can be used with the [Pipeline](#pipeline) meta-Estimator or they can be used separately.

The fit method will allow the transformer to compute any necessary information from the training set in order to carry out its transformations. You can think of *fitting* a Transformer like *training* an Estimator. Not all Transformers need to be fit to the training set, when in doubt, call `fit()` anyways.

```php
public fit(Dataset $dataset) : void
```

The Transformer directly modifies a sample matrix via the `transform()` method.

```php
public transform(array $samples) : void
```

To transform a Dataset without having to pass the raw sample matrix you can call `apply()` on any Dataset object and it will apply the transformation to the underlying sample matrix automatically.

##### Example:
```php
use Rubix\ML\Transformers\MinMaxNormalizer;

...
$transformer = new MinMaxNormalizer();

$dataset->apply($transformer);
```

### Dense Random Projector
The Dense Random Projector uses a random matrix sampled from a dense uniform distribution [-1, 1] to project a sample matrix onto a target dimensionality.

##### Continuous *Only*

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | dimensions | None | int | The number of target dimensions to project onto. |

##### Additional Methods:

Estimate the minimum dimensionality needed given total sample size and max distortion using the Johnson-Lindenstrauss lemma:
```php
public static estimate(int $n, float $maxDistortion = 0.1) : int
```

##### Example:
```php
use Rubix\ML\Transformers\DenseRandomProjector;

$transformer = new DenseRandomProjector(50);

$dimensions = DenseRandomProjector::minDimensions(1e6, 0.1);

var_dump($dimensions);
```

##### Output:
```sh
int(11841)
```

### Gaussian Random Projector
A Random Projector is a dimensionality reducer based on the Johnson-Lindenstrauss lemma that uses a random matrix to project a feature vector onto a user-specified number of dimensions. It is faster than most non-randomized dimensionality reduction techniques and offers similar performance. This version uses a random matrix sampled from a Gaussian distribution.

##### Continuous *Only*

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | dimensions | None | int | The number of target dimensions to project onto. |

##### Additional Methods:

Estimate the minimum dimensionality needed given total sample size and max distortion using the Johnson-Lindenstrauss lemma:
```php
public static estimate(int $n, float $maxDistortion = 0.1) : int
```

##### Example:
```php
use Rubix\ML\Transformers\GaussianRandomProjector;

$transformer = new GaussianRandomProjector(100);

$dimensions = GaussianRandomProjector::minDimensions(1e4, 0.1);

var_dump($dimensions);
```

##### Output:
```sh
int(7894)
```

### L1 Normalizer
Transform each sample vector in the sample matrix such that each feature is divided by the L1 norm (or *magnitude*) of that vector.

##### Continuous *Only*

##### Parameters:
This Transformer does not have any parameters.

##### Additional Methods:
This Transformer does not have any additional methods.

##### Example:
```php
use Rubix\ML\Transformers\L1Normalizer;

$transformer = new L1Normalizer();
```

### L2 Normalizer
Transform each sample vector in the sample matrix such that each feature is divided by the L2 norm (or *magnitude*) of that vector.

##### Continuous *Only*

##### Parameters:
This Transformer does not have any parameters.

##### Additional Methods:
This Transformer does not have any additional methods.

##### Example:
```php
use Rubix\ML\Transformers\L2Normalizer;

$transformer = new L2Normalizer();
```

### Lambda Function
Run a stateless lambda function (*anonymous* function) over the sample matrix. The lambda function receives the sample matrix as an argument and should return the transformed sample matrix.

##### Categorical or Continuous

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | lambda | None | callable | The lambda function to run over the sample matrix. |

##### Additional Methods:
This Transformer does not have any additional methods.

##### Example:
```php
use Rubix\ML\Transformers\LambdaFunction;

// Instantiate a lambda function that will sum up all the features for each sample
$transformer = new LambdaFunction(function ($samples) {
	return array_map(function ($sample) {
		return [array_sum($sample)];
	}, $samples);
});
```

### Min Max Normalizer
Often used as an alternative to [Standard Scaling](#z-scale-standardizer), the Min Max Normalization scales the input features to a range of between 0 and 1 by dividing the feature value over the maximum value for that feature column.

##### Continuous

##### Parameters:
This Transformer does not have any parameters.

##### Additional Methods:
This Transformer does not have any additional methods.

##### Example:
```php
use Rubix\ML\Transformers\MinMaxNormalizer;

$transformer = new MinMaxNormalizer();
```

### Missing Data Imputer
In the real world, it is common to have data with missing values here and there. The Missing Data Imputer replaces missing value placeholders with a guess based on a given guessing [Strategy](#guessing-strategies).

##### Categorical or Continuous

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | placeholder | '?' | string or numeric | The placeholder that denotes a missing value. |
| 2 | continuous strategy | Blurry Mean | object | The guessing strategy to employ for continuous feature columns. |
| 3 | categorical strategy | Popularity Contest | object | The guessing strategy to employ for categorical feature columns. |

##### Additional Methods:
This Transformer does not have any additional methods.

##### Example:
```php
use Rubix\ML\Transformers\MissingDataImputer;
use Rubix\ML\Transformers\Strategies\BlurryMean;
use Rubix\ML\Transformers\Strategies\PopularityContest;

$transformer = new MissingDataImputer('?', new BlurryMean(0.2), new PopularityContest());
```

### Numeric String Converter
This handy Transformer will convert all numeric strings into their floating point counterparts. Useful for when extracting from a source that only recognizes data as string types.

##### Categorical

##### Parameters:
This Transformer does not have any parameters.

##### Additional Methods:
This Transformer does not have any additional methods.

##### Example:
```php
use Rubix\ML\Transformers\NumericStringConverter;

$transformer = new NumericStringConverter();
```

### One Hot Encoder
The One Hot Encoder takes a column of categorical features and produces a n-d one-hot (numerical) representation where n is equal to the number of unique categories in that column. A 0 indicates that a category is not present in the sample whereas a 1 indicates that a category is present.

##### Categorical

##### Parameters:
This Transformer does not have any parameters.

##### Additional Methods:
This Transformer does not have any additional methods.

##### Example:
```php
use Rubix\ML\Transformers\OneHotEncoder;

$transformer = new OneHotEncoder();
```

### Polynomial Expander
This transformer will generate polynomial features up to and including the specified degree. Polynomial expansion is often used to fit data that is non-linear using a linear Estimator such as [Ridge](#ridge).

##### Continuous *Only*

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | degree | 2 | int | The highest degree polynomial to generate from each feature vector. |

##### Additional Methods:
This Transformer does not have any additional methods.

##### Example:
```php
use Rubix\ML\Transformers\PolynomialExpander;

$transformer = new PolynomialExpander(3);
```

### Quartile Standardizer

This standardizer centers the sample matrix around the median and scales each feature according to the interquartile range (*IQR*) for each column. The IQR is the range between the 1st quartile (25th *quantile*) and the 3rd quartile (75th *quantile*).

##### Continuous

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | center | true | bool | Should we center the sample matrix? |
| 2 | scale | true | bool | Should we scale the sample matrix? |

##### Additional Methods:

Return the medians calculated by fitting the training set:
```php
public medians() : array
```

Return the interquartile ranges calculated during fitting:
```php
public iqrs() : array
```

##### Example:
```php
use Rubix\ML\Transformers\QuartileStandardizer;

$transformer = new QuartileStandardizer();
```

### Robust Standardizer
This transformer standardizes continuous features by centering around the median and scaling by the median absolute deviation (MAD), a value referred to as robust Z Score. The use of robust statistics makes this standardizer more immune to outliers than the [Z Scale Standardizer](#z-scale-standardizer).

##### Continuous

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | center | true | bool | Should we center the sample matrix? |
| 2 | scale | true | bool | Should we scale the sample matrix? |

##### Additional Methods:

Return the medians calculated by fitting the training set:
```php
public medians() : array
```

Return the median absolute deviations calculated during fitting:
```php
public mads() : array
```

##### Example:
```php
use Rubix\ML\Transformers\RobustStandardizer;

$transformer = new RobustStandardizer();
```

### Sparse Random Projector
The Sparse Random Projector uses a random matrix sampled from a sparse uniform distribution (mostly 0s) to project a sample matrix onto a target dimensionality.

##### Continuous *Only*

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | dimensions | None | int | The number of target dimensions to project onto. |

##### Additional Methods:

Calculate the minimum dimensionality needed given total sample size and max distortion using the Johnson-Lindenstrauss lemma:
```php
public static minDimensions(int $n, float $maxDistortion = 0.1) : int
```

##### Example:
```php
use Rubix\ML\Transformers\SparseRandomProjector;

$transformer = new SparseRandomProjector(30);

$dimensions = SparseRandomProjector::minDimensions(1e6, 0.5);

var_dump($dimensions);
```

##### Output:
```sh
int(663)
```

### TF-IDF Transformer
Term Frequency - Inverse Document Frequency is a measure of how important a word is to a document. The TF-IDF value increases proportionally with the number of times a word appears in a document and is offset by the frequency of the word in the corpus. This transformer makes the assumption that the input is made up of word frequency vectors such as those created by the [Word Count Vectorizer](#word-count-vectorizer).

##### Continuous *Only*

##### Parameters:
This Transformer does not have any parameters.

##### Additional Methods:
This Transformer does not have any additional methods.

##### Example:
```php
$transformer = new TfIdfTransformer();
```

### Variance Threshold Filter
A type of feature selector that removes all columns that have a lower variance than the threshold. Variance is computed as the population variance of all the values in the feature column.

##### Continuous

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | threshold | 0.0 | float | The threshold at which feature columns will be dropped from the dataset. |

##### Additional Methods:

Return the columns that were selected during fitting:
```php
public selected() : array
```

##### Example:
```php
use Rubix\ML\Transformers\VarianceThresholdFilter;

$transformer = new VarianceThresholdFilter(50);
```

### Z Scale Standardizer
A way of centering and scaling a sample matrix by computing the Z Score for each continuous feature. Z Scores have a mean of 0 and *unit* variance.

##### Continuous

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | center | true | bool | Should we center the sample matrix? |
| 2 | scale | true | bool | Should we scale the sample matrix? |

##### Additional Methods:

Return the means calculated by fitting the training set:
```php
public means() : array
```

Return the standard deviations calculated during fitting:
```php
public stddevs() : array
```

##### Example:
```php
use Rubix\ML\Transformers\ZScaleStandardizer;

$transformer = new ZScaleStandardizer();
```

---
### Neural Network
A number of the Estimators in Rubix are implemented as a Neural Network under the hood. Neural nets are trained using an iterative supervised learning process called Gradient Descent with Backpropagation (also called *Reverse Mode Autodiff*) that repeatedly takes small steps towards minimizing a supplied cost function. Networks can have an arbitrary number of intermediate computational layers called *hidden* layers. Hidden layers can perform a number of tasks such as feature detection, normalization, and regularization.

The [Multi Layer Perceptron](#multi-layer-perceptron) and [MLP Regressor](#mlp-regressor) are examples of multi layer neural networks capable of being built with a limitless combination of [Hidden layers](#hidden). The strength of deep neural nets (those with 1 or more hidden layers) are their ability to handle complex problems and large amounts of data. In general, the deeper the network, the better it will perform.

In addition to the multi layer networks, there are single layer networks that are designed to handle less complex problems with linear solutions. For example, both [Logistic Regression](#logistic-regression) and [Adaline](#adaline) are implemented as single layer networks under the hood. Single layer networks use a single output layer with no hidden layers.

### Activation Functions
The input to a node in the network is sometimes passed through an Activation Function (sometimes referred to as a *transfer* function) which determines its output behavior. In the context of a biologically inspired neural network, the activation function is an abstraction representing the rate of action potential firing of a neuron.

Activation Functions can be broken down into three classes - Sigmoidal (or *S* shaped) such as [Hyperbolic Tangent](#hyperbolic-tangent), Rectifiers such as [ELU](#elu), and Radial Basis Functions (*RBFs*) such as [Gaussian](#gaussian).

### ELU
Exponential Linear Units are a type of rectifier that soften the transition from non-activated to activated using the exponential function.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | alpha | 1.0 | float | The value at which leakage will begin to saturate. Ex. alpha = 1.0 means that the output will never be more than -1.0 when inactivated. |

##### Example:
```php
use Rubix\ML\NeuralNet\ActivationFunctions\ELU;

$activationFunction = new ELU(5.0);
```

### Gaussian
The Gaussian activation function is a type of Radial Basis Function (*RBF*) whose activation depends only on the distance the input is from the origin.

##### Parameters:
This Activation Function does not have any parameters.

##### Example:
```php
use Rubix\ML\NeuralNet\ActivationFunctions\Gaussian;

$activationFunction = new Gaussian();
```

### Hyperbolic Tangent
S-shaped function that squeezes the input value into an output space between -1 and 1 centered at 0.

##### Parameters:
This Activation Function does not have any parameters.

##### Example:
```php
use Rubix\ML\NeuralNet\ActivationFunctions\HyperbolicTangent;

$activationFunction = new HyperbolicTangent();
```

### ISRU
Inverse Square Root units have a curve similar to [Hyperbolic Tangent](#hyperbolic-tangent) and [Sigmoid](#sigmoid) but use the inverse of the square root function instead. It is purported by the authors to be computationally less complex than either of the aforementioned. In addition, ISRU allows the parameter alpha to control the range of activation such that it equals + or - 1 / sqrt(alpha).

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | alpha | 1.0 | float | The parameter that controls the range of activation. |

##### Example:
```php
use Rubix\ML\NeuralNet\ActivationFunctions\ISRU;

$activationFunction = new ISRU(2.0);
```

### Leaky ReLU
Leaky Rectified Linear Units are functions that output x when x > 0 or a small leakage value when x < 0. The amount of leakage is controlled by the user-specified parameter.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | leakage | 0.01 | float | The amount of leakage as a ratio of the input value. |

##### Example:
```php
use Rubix\ML\NeuralNet\ActivationFunctions\LeakyReLU;

$activationFunction = new LeakyReLU(0.001);
```

### ReLU
Rectified Linear Units output only the positive part of its inputs and are analogous to a half-wave rectifiers in electrical engineering.

##### Parameters:
This Activation Function does not have any parameters.

##### Example:
```php
use Rubix\ML\NeuralNet\ActivationFunctions\ReLU;

$activationFunction = new ReLU();
```

### SELU
Scaled Exponential Linear Unit is a self-normalizing activation function based on [ELU](#elu).

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | scale | 1.05070 | float | The factor to scale the output by. |
| 2 | alpha | 1.67326 | float | The value at which leakage will begin to saturate. Ex. alpha = 1.0 means that the output will never be more than -1.0 when inactivated. |

##### Example:
```php
use Rubix\ML\NeuralNet\ActivationFunctions\SELU;

$activationFunction = new SELU(1.05070, 1.67326);
```

### Sigmoid
A bounded S-shaped function (specifically the Logistic function) with an output value between 0 and 1.

##### Parameters:
This Activation Function does not have any parameters.

##### Example:
```php
use Rubix\ML\NeuralNet\ActivationFunctions\Sigmoid;

$activationFunction = new Sigmoid();
```

### Softmax
The Softmax function is a generalization of the [Sigmoid](#sigmoid) function that *squashes* each activation between 0 and 1, and all activations add up to 1.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | epsilon | 1e-8 | float | The smoothing parameter i.e a small value to add to the denominator for numerical stability. |

##### Example:
```php
use Rubix\ML\NeuralNet\ActivationFunctions\Softmax;

$activationFunction = new Softmax(1e-10);
```

### Soft Plus
A smooth approximation of the ReLU function whose output is constrained to be positive.

##### Parameters:
This Activation Function does not have any parameters.

##### Example:
```php
use Rubix\ML\NeuralNet\ActivationFunctions\SoftPlus;

$activationFunction = new SoftPlus();
```

### Softsign
A function that squashes the output of a neuron to + or - 1 from 0. In other words, the output is between -1 and 1.

##### Parameters:
This Activation Function does not have any parameters.

##### Example:
```php
use Rubix\ML\NeuralNet\ActivationFunctions\Softsign;

$activationFunction = new Softsign();
```

### Thresholded ReLU
Thresholded ReLU has a user-defined threshold parameter that controls the level at which the neuron is activated.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | threshold | 0.0 | float | The input value necessary to trigger an activation. |

##### Example:
```php
use Rubix\ML\NeuralNet\ActivationFunctions\ThresholdedReLU;

$activationFunction = new ThresholdedReLU(0.5);
```

### Cost Functions
In neural networks, the cost function is a function that the network wants to minimize during training. The cost of a particular sample is defined as the difference between the output of the network and what the correct output should be given the label. Different cost functions have different ways of punishing erroneous activations.

### Cross Entropy
Cross Entropy, or log loss, measures the performance of a classification model whose output is a probability value between 0 and 1. Cross-entropy loss increases as the predicted probability diverges from the actual label. So predicting a probability of .012 when the actual observation label is 1 would be bad and result in a high loss value. A perfect score would have a log loss of 0.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | epsilon | 1e-20 | float | The smoothing parameter i.e a small value to add to the loss for numerical stability. |

##### Example:
```php
use Rubix\ML\NeuralNet\CostFunctions\CrossEntropy;

$costFunction = new CrossEntropy();
```

### Exponential
This cost function calculates the exponential of a prediction's squared error thus applying a large penalty to wrong predictions. The resulting gradient of the Exponential loss tends to be steeper than most other cost functions. The magnitude of the error can be scaled by the parameter *tau*.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | tau | 1.0 | float | The scaling parameter i.e. the magnitude of the error to return. |

##### Example:
```php
use Rubix\ML\NeuralNet\CostFunctions\Exponential;

$costFunction = new Exponential(0.5);
```

### Least Squares
Least Squares or *quadratic* loss is a function that measures the squared error between the target output and the actual output of a network.

##### Parameters:
This Cost Function does not have any parameters.

##### Example:
```php
use Rubix\ML\NeuralNet\CostFunctions\LeastSquares;

$costFunction = new LeastSquares();
```

### Relative Entropy
Relative Entropy or *Kullback-Leibler divergence* is a measure of how the expectation and activation of the network diverge.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | epsilon | 1e-20 | float | The smoothing parameter i.e a small value to add to the loss for numerical stability. |

##### Example:
```php
use Rubix\ML\NeuralNet\CostFunctions\RelativeEntropy;

$costFunction = new RelativeEntropy();
```

---
### Initializers
Initializers are responsible for setting the initial weight parameters of a neural network. Different activation layers respond to different weight initializations therefore it is important to choose the  initializer that suits your network architecture.

### He
The He initializer was designed for hidden layers that feed into rectified linear layers such [ReLU](#relu), [Leaky ReLU](#leaky-relu), [ELU](#elu), and [SELU](#selu). It draws from a uniform distribution with limits defined as +/- (6 / (fanIn + fanOut)) ** (1. / sqrt(2)).

##### Parameters:
This Initializer does not have any parameters.

##### Example:
```php
use Rubix\ML\NeuralNet\Initializers\He;

$initializer = new He();
```

### Le Cun
Proposed by Yan Le Cun in a paper in 1998, this initializer was one of the first published attempts to control the variance of activations between layers through weight initialization. It remains a good default choice for many hidden layer configurations.

##### Parameters:
This Initializer does not have any parameters.

##### Example:
```php
use Rubix\ML\NeuralNet\Initializers\LeCun;

$initializer = new LeCun();
```

### Normal
Generates a random weight matrix from a Gaussian distribution with user-specified standard deviation.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | stddev | 0.05 | float | The standard deviation of the distribution to sample from. |

##### Example:
```php
use Rubix\ML\NeuralNet\Initializers\Normal;

$initializer = new Normal(0.1);
```

### Xavier 1
The Xavier 1 initializer draws from a uniform distribution [-limit, limit] where *limit* is squal to sqrt(6 / (fanIn + fanOut)). This initializer is best suited for layers that feed into an activation layer that outputs a value between 0 and 1 such as [Softmax](#softmax) or [Sigmoid](#sigmoid).

##### Parameters:
This Initializer does not have any parameters.

##### Example:
```php
use Rubix\ML\NeuralNet\Initializers\Xavier1;

$initializer = new Xavier1();
```

### Xavier 2
The Xavier 2 initializer draws from a uniform distribution [-limit, limit] where *limit* is squal to (6 / (fanIn + fanOut)) ** 0.25. This initializer is best suited for layers that feed into an activation layer that outputs values between -1 and 1 such as [Hyperbolic Tangent](#hyperbolic-tangent) and [Softsign](#softsign).

##### Parameters:
This Initializer does not have any parameters.

##### Example:
```php
use Rubix\ML\NeuralNet\Initializers\Xavier2;

$initializer = new Xavier2();
```

---
### Layers
Every network is made up of layers of computational units called neurons. Each layer processes and transforms the input from the previous layer.

There are three types of Layers that form a network, **Input**, **Hidden**, and **Output**. A network can have as many Hidden layers as the user specifies, however, there can only be 1 Input and 1 Output layer per network.

##### Example:
```php
use Rubix\ML\NeuralNet\FeedForward;
use Rubix\ML\NeuralNet\Layers\Placeholder;
use Rubix\ML\NeuralNet\Layers\Dense;
use Rubix\ML\NeuralNet\Layers\Activation;
use Rubix\ML\NeuralNet\Layers\Dropout;
use Rubix\ML\NeuralNet\Layers\Multiclass;
use Rubix\ML\NeuralNet\ActivationFunctions\ELU;
use Rubix\ML\NeuralNet\CostFunctions\CrossEntropy;
use Rubix\ML\NeuralNet\Optimizers\Adam;

$network = new FeedForward(new Placeholder(784), [
	new Dense(300),
    new Activation(new ELU()),
    new Dropout(0.3),
    new Dense(200),
    new Activation(new ELU()),
    new Dropout(0.3),
    new Dense(100),
    new Activation(new ELU()),
], new Multiclass(['dog', 'cat', 'frog', 'car'], 1e-4), new CrossEntropy(), new Adam(0.001));
```

### Input Layers
The entry point for data into a neural network is the input layer which is the first layer in the network. Input layers do not have any learnable parameters.

### Placeholder
The Placeholder input layer serves to represent the *future* input values of a mini batch to the network.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | inputs | None | int | The number of inputs to the network. |

##### Example:
```php
use Rubix\ML\NeuralNet\Layers\Placeholder;

$layer = new Placeholder(100);
```

### Hidden Layers
In multilayer networks, hidden layers are responsible for transforming the input space in such a way that can be linearly separable by the final output layer. The more complex the problem, the more hidden layers and neurons will be necessary to handle the problem.

### Activation
Activation layers apply a nonlinear activation function to their inputs.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | activation fn | None | object | The function computes the activation of the layer. |

##### Example:
```php
use Rubix\ML\NeuralNet\Layers\Activation;
use Rubix\ML\NeuralNet\ActivationFunctions\ReLU;

$layer = new Activation(new ReLU());
```

### Alpha Dropout
Alpha Dropout is a type of dropout layer that maintains the mean and variance of the original inputs in order to ensure the self-normalizing property of [SELU](#selu) networks with dropout. Alpha Dropout fits with SELU networks by randomly setting activations to the negative saturation value of the activation function at a given ratio each pass.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | ratio | 0.1 | float | The ratio of neurons that are dropped during each training pass. |

##### Example:
```php
use Rubix\ML\NeuralNet\Layers\AlphaDropout;

$layer = new AlphaDropout(0.1);
```

### Batch Norm
Normalize the activations of the previous layer such that the mean activation is close to 0 and the activation standard deviation is close to 1. Batch Norm can be used to reduce the amount of covariate shift within the network making it possible to use higher learning rates and converge faster under some circumstances.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | epsilon | 1e-8 | float | The variance smoothing parameter i.e a small value added to the variance for numerical stability. |

##### Example:
```php
use Rubix\ML\NeuralNet\Layers\BatchNorm;

$layer = new BatchNorm(1e-3);
```

### Dense
Dense layers are fully connected hidden layers, meaning each neuron is connected to each other neuron in the previous layer by a weighted *synapse*. Dense layers employ [Activation Functions](#activation-functions) that control the output of each neuron in the layer.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | neurons | None | int | The number of neurons in the layer. |
| 2 | initializer | He | object | The random weight initializer to use. |

##### Example:
```php
use Rubix\ML\NeuralNet\Layers\Dense;
use Rubix\ML\NeuralNet\Initializers\He;

$layer = new Dense(100, new He());
```

### Dropout
Dropout layers temporarily disable neurons during each training pass. Dropout is a regularization technique for reducing overfitting in neural networks by preventing complex co-adaptations on training data. It is a very efficient way of performing model averaging with neural networks.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | ratio | 0.5 | float | The ratio of neurons that are dropped during each training pass. |

##### Example:
```php
use Rubix\ML\NeuralNet\Layers\Dropout;

$layer = new Dropout(0.5);
```

### Noise
This layer adds random Gaussian noise to the inputs to the layer with a standard deviation given as a parameter. Noise added to neural network activations acts as a regularizer by indirectly adding a penalty to the
weights through the cost function in the output layer.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | amount | 0.1 | float | The amount of gaussian noise to add to the inputs i.e the standard deviation of the noise. |

##### Example:
```php
use Rubix\ML\NeuralNet\Layers\Noise;

$layer = new Noise(0.3);
```

### PReLU
The PReLU layer uses ReLU activation function's whose leakage coefficients are parameterized and optimized on a per neuron basis along with the weights and biases.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | initial | 0.25 | float | The value to initialize the alpha (leakage) parameters with. |

##### Example:
```php
use Rubix\ML\NeuralNet\Layers\PReLU;

$layer = new PReLU(0.1);
```

### Output Layers
Activations are read directly from the Output layer when making predictions. The type of output layer will determine the type of Estimator the neural network can power (i.e Binary Classifier, Multiclass Classifier, or Regressor).

### Binary
This Binary layer consists of a single [Sigmoid](#sigmoid) neuron capable of distinguishing between two discrete classes. The Binary layer is useful for neural networks that output a binary class prediction such as *yes* or *no*.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | classes | None | array | The unique class labels of the binary classification problem. |
| 2 | alpha | 1e-4 | float | The L2 regularization penalty. |

##### Example:
```php
use Rubix\ML\NeuralNet\Layers\Binary;

$layer = new Binary(['yes', 'no'], 1e-3);
```

### Continuous
The Continuous output layer consists of a single linear neuron that outputs a scalar value useful for regression problems.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | alpha | 1e-4 | float | The L2 regularization penalty. |

##### Example:
```php
use Rubix\ML\NeuralNet\Layers\Continuous;

$layer = new Continuous(1e-5);
```

### Multiclass
The Multiclass output layer gives a joint probability estimate of a multiclass classification problem using the [Softmax](#softmax) activation function.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | classes | None | array | The unique class labels of the multiclass classification problem. |
| 2 | alpha | 1e-4 | float | The L2 regularization penalty. |

##### Example:
```php
use Rubix\ML\NeuralNet\Layers\Multiclass;

$layer = new Multiclass(['yes', 'no', 'maybe'], 1e-4);
```

---
### Optimizers
Gradient Descent is an algorithm that takes iterative steps towards finding the best set of weights in a neural network. Rubix provides a number of pluggable Gradient Descent optimizers that control the step of each parameter in the network.

### AdaGrad
Short for *Adaptive Gradient*, the AdaGrad Optimizer speeds up the learning of parameters that do not change often and slows down the learning of parameters that do enjoy heavy activity.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | rate | 0.01 | float | The learning rate. i.e. the master step size. |
| 3 | epsilon | 1e-8 | float | The smoothing constant used for numerical stability. |

##### Example:
```php
use Rubix\ML\NeuralNet\Optimizers\AdaGrad;

$optimizer = new AdaGrad(0.025, 1e-5);
```

### Adam
Short for *Adaptive Momentum Estimation*, the Adam Optimizer uses both Momentum and RMS properties to achieve a balance of velocity and stability.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | rate | 0.001 | float | The learning rate. i.e. the master step size. |
| 2 | momentum | 0.9 | float | The decay rate of the Momentum property. |
| 3 | rms | 0.999 | float | The decay rate of the RMS property. |
| 4 | epsilon | 1e-8 | float | The smoothing constant used for numerical stability. |

##### Example:
```php
use Rubix\ML\NeuralNet\Optimizers\Adam;

$optimizer = new Adam(0.0001, 0.9, 0.999, 1e-8);
```

### Momentum
Momentum adds velocity to each step until exhausted. It does so by accumulating momentum from past updates and adding a factor to the current step.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | rate | 0.001 | float | The learning rate. i.e. the master step size. |
| 2 | decay | 0.9 | float | The Momentum decay rate. |

##### Example:
```php
use Rubix\ML\NeuralNet\Optimizers\Momentum;

$optimizer = new Momentum(0.001, 0.925);
```

### RMS Prop
An adaptive gradient technique that divides the current gradient over a rolling window of magnitudes of recent gradients.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | rate | 0.001 | float | The learning rate. i.e. the master step size. |
| 2 | decay | 0.9 | float | The RMS decay rate. |
| 3 | epsilon | 1e-8 | float | The smoothing constant used for numerical stability. |

##### Example:
```php
use Rubix\ML\NeuralNet\Optimizers\RMSProp;

$optimizer = new RMSProp(0.01, 0.9, 1e-10);
```

### Step Decay
A learning rate decay stochastic optimizer that reduces the learning rate by a factor of the decay parameter whenever it reaches a new *floor*. The number of steps needed to reach a new floor is defined by the *steps* parameter.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | rate | 0.001 | float | The learning rate. i.e. the master step size. |
| 2 | k | 10 | int | The size of every floor in steps. i.e. the number of steps to take before applying another factor of decay. |
| 3 | decay | 1e-5 | float | The decay factor to decrease the learning rate by every k steps. |

##### Example:
```php
use Rubix\ML\NeuralNet\Optimizers\StepDecay;

$optimizer = new StepDecay(0.001, 15, 1e-5);
```

### Stochastic
A constant learning rate Optimizer.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | rate | 0.001 | float | The learning rate. i.e. the master step size. |

##### Example:
```php
use Rubix\ML\NeuralNet\Optimizers\Stochastic;

$optimizer = new Stochastic(0.001);
```

### Snapshots
Snapshots are a way to capture the state of a neural network at a moment in time. A Snapshot object holds all of the parameters in the network and can be used to restore the network back to a previous state.

To take a snapshot of your network simply call the `take()` method on the Snapshot object. To restore the network from a snapshot pass the Snapshot to the `restore()` method on a network.

The example below shows how to take a snapshot and then restore the network via the snapshot.
```php
...
$snapshot = Snapshot::take($network);

...

$network->restore($snapshot);
...
```

---
### Kernels
Kernel functions are used to compute the similarity or distance between two vectors and can be plugged in to a particular Estimator to perform a part of the computation. They are pairwise positive semi-definite meaning their output is always 0 or greater. When considered as a hyperparameter, different Kernel functions have properties that can lead to different training and predictions.

### Distance
Distance functions are a type of Kernel that measures the distance between two coordinate vectors. They can be used throughout Rubix in Estimators that use the concept of distance to make predictions such as [K Nearest Neighbors](#k-nearest-neighbors), [K Means](#k-means), and [Local Outlier Factor](#local-outlier-factor).

### Canberra
A weighted version of [Manhattan](#manhattan) distance which computes the L1 distance between two coordinates in a vector space.

##### Parameters:
This Kernel does not have any parameters.

##### Example:
```php
use Rubix\ML\Kernels\Distance\Canberra;

$kernel = new Canberra();
```

### Cosine
Cosine Similarity is a measure that ignores the magnitude of the distance between two vectors thus acting as strictly a judgement of orientation. Two vectors with the same orientation have a cosine similarity of 1, two vectors oriented at 90° relative to each other have a similarity of 0, and two vectors diametrically opposed have a similarity of -1. To be used as a distance function, we subtract the Cosine Similarity from 1 in order to satisfy the positive semi-definite condition, therefore the Cosine *distance* is a number between 0 and 2.

##### Parameters:
This Kernel does not have any parameters.

##### Example:
```php
use Rubix\ML\Kernels\Distance\Cosine;

$kernel = new Cosine();
```

### Diagonal
The Diagonal (sometimes called Chebyshev) distance is a measure that constrains movement to horizontal, vertical, and diagonal from a point. An example that uses Diagonal movement is a chess board.

##### Parameters:
This Kernel does not have any parameters.

##### Example:
```php
use Rubix\ML\Kernels\Distance\Diagonal;

$kernel = new Diagonal();
```

### Euclidean
This is the ordinary straight line (*bee line*) distance between two points in Euclidean space. The associated norm of the Euclidean distance is called the L2 norm.

##### Parameters:
This Kernel does not have any parameters.

##### Example:
```php
use Rubix\ML\Kernels\Distance\Euclidean;

$kernel = new Euclidean();
```

### Hamming
The Hamming distance is defined as the sum of all coordinates that are not exactly the same. Therefore, two coordinate vectors a and b would have a Hamming distance of 2 if only one of the three coordinates were equal between the vectors.

##### Parameters:
This Kernel does not have any parameters.

##### Example:
```php
use Rubix\ML\Kernels\Distance\Hamming;

$kernel = new Hamming();
```

### Jaccard
The generalized Jaccard distance is a measure of similarity that one sample has to another with a range from 0 to 1. The higher the percentage, the more dissimilar they are.

##### Parameters:
This Kernel does not have any parameters.

##### Example:
```php
use Rubix\ML\Kernels\Distance\Jaccard;

$kernel = new Jaccard();
```

### Manhattan
A distance metric that constrains movement to horizontal and vertical, similar to navigating the city blocks of Manhattan. An example that used this type of movement is a checkers board.

##### Parameters:
This Kernel does not have any parameters.

##### Example:
```php
use Rubix\ML\Kernels\Distance\Manhattan;

$kernel = new Manhattan();
```

### Minkowski
The Minkowski distance is a metric in a normed vector space which can be considered as a generalization of both the [Euclidean](#euclidean) and [Manhattan](#manhattan) distances. When the *lambda* parameter is set to 1 or 2, the distance is equivalent to Manhattan and Euclidean respectively.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | lambda | 3.0 | float | Controls the curvature of the unit circle drawn from a point at a fixed distance. |

##### Example:
```php
use Rubix\ML\Kernels\Distance\Minkowski;

$kernel = new Minkowski(4.0);
```

---
### Cross Validation
Cross validation is the process of testing the generalization performance of a computer model using various techniques. Rubix has a number of classes that run cross validation on an instantiated Estimator for you. Each Validator outputs a scalar score based on the chosen metric.

### Validators
Validators take an [Estimator](#estimators) instance, [Labeled Dataset](#labeled) object, and validation [Metric](#validation-metrics) and return a validation score that measures the generalization performance of the model using one of various cross validation techniques. There is no need to train the Estimator beforehand as the Validator will automatically train it on subsets of the dataset chosen by the testing algorithm.

```php
public test(Estimator $estimator, Labeled $dataset, Validation $metric) : float
```

##### Example:
```php
use Rubix\ML\CrossValidation\KFold;
use Rubix\ML\CrossValidation\Metrics\Accuracy;

...
$validator = new KFold(10);

$score = $validator->test($estimator, $dataset, new Accuracy());

var_dump($score);
```

##### Output:
```sh
float(0.869)
```
Below describes the various Cross Validators available in Rubix.

### Hold Out
Hold Out is the simplest form of cross validation available in Rubix. It uses a *hold out* set equal to the size of the given ratio of the entire training set to test the model. The advantages of Hold Out is that it is quick, but it doesn't allow the model to train on the entire training set.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | ratio | 0.2 | float | The ratio of samples to hold out for testing. |
| 2 | stratify | false | bool | Should we stratify the dataset before splitting? |

##### Example:
```php
use Rubix\ML\CrossValidation\HoldOut;

$validator = new HoldOut(0.25, true);
```

### K Fold
K Fold is a technique that splits the training set into K individual sets and for each training round uses 1 of the folds to measure the validation performance of the model. The score is then averaged over K. For example, a K value of 10 will train and test 10 versions of the model using a different testing set each time.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | k | 10 | int | The number of times to split the training set into equal sized folds. |
| 2 | stratify | false | bool | Should we stratify the dataset before folding? |

##### Example:
```php
use Rubix\ML\CrossValidation\KFold;

$validator = new KFold(5, true);
```

### Leave P Out
Leave P Out tests the model with a unique holdout set of P samples for each round until all samples have been tested. Note that this process can become slow with large datasets and small values of P.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | p | 10 | int | The number of samples to leave out each round for testing. |

##### Example:
```php
use Rubix\ML\CrossValidation\LeavePOut;

$validator = new LeavePOut(50);
```

### Monte Carlo
Repeated Random Subsampling or Monte Carlo cross validation is a technique that takes the average validation score over a user-supplied number of simulations (random splits of the dataset).

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | simulations | 10 | int | The number of simulations to run i.e the number of tests to average. |
| 2 | ratio | 0.2 | float | The ratio of samples to hold out for testing. |
| 3 | stratify | false | bool | Should we stratify the dataset before splitting? |

##### Example:
```php
use Rubix\ML\CrossValidation\MonteCarlo;

$validator = new MonteCarlo(30, 0.1);
```

### Validation Metrics

Validation metrics are for evaluating the performance of an Estimator given some ground truth such as class labels. The output of the Metric's `score()` method is a scalar score. You can output a tuple of minimum and maximum scores with the `range()` method.

To compute a validation score on an Estimator with a Labeled Dataset:
```php
public score(Estimator $estimator, Labeled $testing) : float
```

To output the range of values the metric can take on:
```php
public range() : array
```

##### Example:
```php
use Rubix\ML\CrossValidation\Metrics\MeanAbsoluteError;

...
$metric = new MeanAbsoluteError();

$score = $metric->score($estimator, $testing);

var_dump($metric->range());

var_dump($score);
```

##### Output:
```sh
array(2) {
  [0]=> float(-INF)
  [1]=> int(0)
}

float(-0.99846070553066)
```

There are different metrics for the different types of Estimators listed below.

### Anomaly Detection
| Metric | Range |  Description |
|--|--|--|
| Accuracy | (0, 1) | A quick metric that computes the accuracy of the detector. |
| F1 Score | (0, 1) | A metric that takes the precision and recall  into consideration. |

### Classification
| Metric | Range |  Description |
|--|--|--|
| Accuracy | (0, 1) | A quick metric that computes the accuracy of the classifier. |
| F1 Score | (0, 1) | A metric that takes the precision and recall of into consideration. |
| Informedness | (0, 1) | Measures the probability of making an informed prediction by looking at the sensitivity and specificity of each class outcome. |
| MCC | (-1, 1) | Matthews Correlation Coefficient is a coefficient between the observed and predicted binary classifications. A coefficient of +1 represents a perfect prediction, 0 no better than random prediction, and −1 indicates total disagreement between prediction and label. |


### Clustering
| Metric | Range | Description |
|--|--|--|
| Completeness | (0, 1) | A measure of the class outcomes that are predicted to be in the same cluster. |
| Concentration | (-INF, INF) | A score that measures the ratio between the within-cluster dispersion and the between-cluster dispersion (also called *Calinski Harabaz* score).
| Homogeneity | (0, 1) | A measure of the cluster assignments that are known to be in the same class. |
| V Measure | (0, 1) | The harmonic mean between Homogeneity and Completeness. |

##### Example:
```php
use Rubix\ML\CrossValidation\Metrics\Accuracy;
use Rubix\ML\CrossValidation\Metrics\Homogeneity;

$metric = new Accuracy();

$metric = new Homogeneity();
```

### Regression
| Metric | Range | Description |
|--|--|--|
| Mean Absolute Error | (-INF, 0) | The average absolute difference between the actual and predicted values. |
| Median Absolute Error | (-INF, 0) | The median absolute difference between the actual and predicted values. |
| Mean Squared Error | (-INF, 0) | The average magnitude or squared difference between the actual and predicted values. |
| RMS Error | (-INF, 0) | The root mean squared difference between the actual and predicted values. |
| R-Squared | (-INF, 1) | The R-Squared value, or sometimes called coefficient of determination is the proportion of the variance in the dependent variable that is predictable from the independent variable(s). |

---
### Reports
Reports allow you to evaluate the performance of a model with a testing set. To generate a report, pass a *trained* Estimator and a testing Dataset to the Report's `generate()` method. The output is an associative array that can be used to generate visualizations or other useful statistics.

To generate a report:
```php
public generate(Estimator $estimator, Dataset $dataset) : array
```

##### Example:
```php
use Rubix\ML\Classifiers\KNearestNeighbors;
use Rubix\ML\Reports\ConfusionMatrix;
use Rubix\ML\Datasets\Labeled;

...
$dataset = new Labeled($samples, $labels);

list($training, $testing) = $dataset->randomize()->split(0.8);

$estimator = new KNearestNeighbors(7);

$report = new ConfusionMatrix(['positive', 'negative', 'neutral']);

$estimator->train($training);

$result = $report->generate($estimator, $testing);
```

Most Reports require a Labeled dataset because they need some sort of ground truth to go compare to. The Reports that are available in Rubix are listed below.

### Aggregate Report
A Report that aggregates the results of multiple reports. The reports are indexed by their order given at construction time.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | reports | [ ] | array | An array of Report objects to aggregate. |

##### Example:
```php
use Rubix\ML\Reports\AggregateReport;
use Rubix\ML\Reports\ConfusionMatrix;
use Rubix\ML\Reports\MulticlassBreakdown;
use Rubix\ML\Reports\PredictionSpeed;

...
$report = new AggregateReport([
	new ConfusionMatrix(['wolf', 'lamb']),
	new MulticlassBreakdown(),
	new PredictionSpeed(),
]);

$result = $report->generate($estimator, $testing);
```

### Confusion Matrix
A Confusion Matrix is a table that visualizes the true positives, false, positives, true negatives, and false negatives of a Classifier. The name stems from the fact that the matrix makes it easy to see the classes that the Classifier might be confusing.

##### Classification

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | classes | All | array | The classes to compare in the matrix. |

##### Example:
```php
use Rubix\ML\Reports\ConfusionMatrix;

...
$report = new ConfusionMatrix(['dog', 'cat', 'turtle']);

$result = $report->generate($estimator, $testing);

var_dump($result);
```

##### Output:

```sh
  array(3) {
    ["dog"]=> array(2) {
      ["dog"]=> int(842)
      ["cat"]=> int(5)
      ["turtle"]=> int(0)
    }
    ["cat"]=>
    array(2) {
      ["dog"]=> int(0)
      ["cat"]=> int(783)
      ["turtle"]=> int(3)
    }
    ["turtle"]=>
    array(2) {
      ["dog"]=> int(31)
      ["cat"]=> int(79)
      ["turtle"]=> int(496)
    }
  }
```

### Contingency Table

A Contingency Table is used to display the frequency distribution of class labels among a clustering of samples.

##### Clustering

##### Parameters:
This Report does not have any parameters.

##### Example:
```php
use Rubix\ML\Reports\ContingencyTable;

...
$report = new ContingencyTable();

$result = $report->generate($estimator, $testing);

var_dump($result);
```

##### Output:
```sh
array(3) {
    [1]=>
    array(3) {
      [1]=> int(13)
      [2]=> int(0)
      [3]=> int(2)
    }
    [2]=>
    array(3) {
      [1]=> int(1)
      [2]=> int(0)
      [3]=> int(12)
    }
    [0]=>
    array(3) {
      [1]=> int(0)
      [2]=> int(14)
      [3]=> int(0)
    }
  }
```

### Multiclass Breakdown
A Report that drills down in to each unique class outcome. The report includes metrics such as Accuracy, F1 Score, MCC, Precision, Recall, Cardinality, Miss Rate, and more.

##### Classification

##### Parameters:
This Report does not have any parameters.

##### Example:
```php
use Rubix\ML\Reports\MulticlassBreakdown;

...
$report = new MulticlassBreakdown();

$result = $report->generate($estimator, $testing);

var_dump($result);
```

##### Output:
```sh
...
["benign"]=>
	array(15) {
        ["accuracy"]=> int(1)
        ["precision"]=> float(0.99999999998723)
        ["recall"]=> float(0.99999999998723)
        ["specificity"]=> float(0.99999999998812)
        ["miss_rate"]=> float(1.2771450563775E-11)
        ["fall_out"]=> float(1.1876499783625E-11)
        ["f1_score"]=> float(0.99999999498723)
        ["mcc"]=> float(0.99999999999998)
        ["informedness"]=> float(0.99999999997535)
        ["true_positives"]=> int(783)
        ["true_negatives"]=> int(842)
        ["false_positives"]=> int(0)
        ["false_negatives"]=> int(0)
        ["cardinality"]=> int(783)
        ["density"]=> float(0.48184615384615)
	}
...
```

### Outlier Ratio
Outlier Ratio is the proportion of outliers to inliers in an [Anomaly Detection](#anomaly-detectors) problem. It can be used to gauge the amount of contamination that the Detector is predicting.

##### Anomaly Detection

##### Parameters:
This Report does not have any parameters.

##### Example:
```php
use Rubix\ML\Reports\OutlierRatio;

...
$report = new OutlierRatio();

$result = $report->generate($estimator, $testing);

var_dump($result);
```

##### Output:
```sh
  array(4) {
    ["outliers"]=> int(13)
    ["inliers"]=> int(307)
    ["ratio"]=> float(0.042345276871585)
    ["cardinality"]=> int(320)
  }
```

### Prediction Speed
 This report measures the prediction speed of an Estimator given as the number of predictions per second (PPS), per minute (PPM), as well as the average time to make a single prediction.

##### Classification, Regression, Clustering, Anomaly Detection

##### Parameters:
This Report does not have any parameters.

##### Example:
```php
use Rubix\ML\Reports\PredictionSpeed;

...
$report = new PredictionSpeed();

$result = $report->generate($estimator, $testing);

var_dump($result);
```

##### Output:
```sh
  array(4) {
    ["pps"]=> float(72216.1351696)
    ["ppm"]=> float(4332968.1101788)
    ["average_seconds"]=> float(1.3847287706694E-5)
    ["total_seconds"]=> float(0.0041680335998535)
    ["cardinality"]=> int(301)
  }

```

### Residual Breakdown
Residual Breakdown is a Report that measures the differences between the predicted and actual values of a regression problem in detail. The statistics provided in the report cover the first (*mean*), second (*variance*), third (*skewness*), and fourth order (*kurtosis*) moments of the distribution of residuals produced by a testing set as well as standard error metrics and r squared.

##### Regression

##### Parameters:
This Report does not have any parameters.

##### Example:
```php
use Rubix\ML\Reports\ResidualBreakdown;

...
$report = new ResidualBreakdown();

$result = $report->generate($estimator, $testing);

var_dump($result);
```

##### Output:
```sh
  array(12) {
    ["mean_absolute_error"]=> float(0.44927554249285)
    ["median_absolute_error"]=> float(0.30273889978541)
    ["mean_squared_error"]=> float(0.44278193357447)
    ["rms_error"]=> float(0.66541861529001)
    ["error_mean"]=> float(0.14748941084881)
    ["error_variance"]=> float(0.42102880726195)
    ["error_skewness"]=> float(-2.7901397847317)
    ["error_kurtosis"]=> float(12.967400285518)
    ["error_min"]=> float(-3.5540079974946)
    ["error_max"]=> float(1.4097829828182)
    ["r_squared"]=> float(0.99393263320234)
    ["cardinality"]=> int(80)
  }
```

---
### Other
This section includes broader functioning classes that do not fall under a specific category.

### Generators
Dataset Generators allow you to produce synthetic data of a user-specified shape, dimensionality, and cardinality. This is useful for augmenting a dataset with extra data or for testing and demonstration purposes.

To generate a Dataset object with **n** samples (*rows*):
```php
public generate(int $n = 100) : Dataset
```

Return the dimensionality of the samples produced:
```php
public dimensions() : int
```

##### Example:
```php
use Rubix\ML\Other\Generators\Blob;

$generator = new Blob([0, 0], 1.0);

$dataset = $generator->generate(3);

var_dump($generator->dimensions());

var_dump($dataset->samples());
```

##### Output:
```sh
int(2)

object(Rubix\ML\Datasets\Unlabeled)#24136 (1) {
  ["samples":protected]=>
  array(3) {
    [0]=>
    array(2) {
      [0]=> float(-0.2729673885539)
      [1]=> float(0.43761840244204)
    }
    [1]=>
    array(2) {
      [0]=> float(-1.2718092282012)
      [1]=> float(-1.9558245484829)
    }
    [2]=>
    array(2) {
      [0]=> float(1.1774185431405)
      [1]=> float(0.05168623824664)
    }
  }
}
```

### Agglomerate
An Agglomerate is a collection of other generators each given a label. Agglomerates are useful for classification, clustering, and anomaly detection problems where the label is a discrete value.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | generators | [ ] | array | A collection of generators keyed by their user-specified label (0 indexed by default). |
| 2 | weights | 1 / n | array | A set of arbitrary weight values corresponding to a generator's contribution to the agglomeration. |

##### Additional Methods:

Return the normalized weights of each generator in the agglomerate:
```php
public weights() : array
```

##### Example:
```php
use Rubix\ML\Other\Generators\Agglomerate;

$generator = new Agglomerate([
	new Blob([5, 2], 1.0),
	new HalfMoon([-3, 5], 1.5, 90.0, 0.1),
	new Circle([2, -4], 2.0, 0.05),
], [
	5, 6, 3, // Weights
]);
```

### Blob
A normally distributed n-dimensional blob of samples centered at a given mean vector. The standard deviation can be set for the whole blob or for each  feature column independently. When a global value is used, the resulting blob will be isotropic.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | center | [ ] | array | The coordinates of the center of the blob i.e. a centroid vector. |
| 2 | stddev | 1.0 | float or array | Either the global standard deviation or an array with the SD for each feature column. |

##### Additional Methods:
This Generator does not have any additional methods.

##### Example:
```php
use Rubix\ML\Other\Generators\Blob;

$generator = new Blob([1.2, 5.0, 2.6, 0.8], 0.25);
```

### Circle
Create a circle made of sample data points in 2 dimensions.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | center | [ ] | array | The x and y coordinates of the center of the circle. |
| 2 | scale | 1.0 | float | The scaling factor of the circle. |
| 3 | noise | 0.1 | float | The amount of Gaussian noise to add to each data point as a ratio of the scaling factor. |

##### Additional Methods:
This Generator does not have any additional methods.

##### Example:
```php
use Rubix\ML\Other\Generators\Circle;

$generator = new Circle([0.0, 0.0], 100, 0.1);
```

### Half Moon
Generate a dataset consisting of 2-d samples that form a half moon shape.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | center | [ ] | array | The x and y coordinates of the center of the circle. |
| 2 | scale | 1.0 | float | The scaling factor of the circle. |
| 3 | rotate | 90.0 | float | The amount in degrees to rotate the half moon counterclockwise. |
| 4 | noise | 0.1 | float | The amount of Gaussian noise to add to each data point as a ratio of the scaling factor. |

##### Additional Methods:
This Generator does not have any additional methods.

##### Example:
```php
use Rubix\ML\Other\Generators\HalfMoon;

$generator = new HalfMoon([0.0, 0.0], 100, 180.0, 0.2);
```

### Guessing Strategies
Guesses can be thought of as a type of *weak* prediction. Unlike a real prediction, guesses are made using limited information and basic means. A guessing Strategy attempts to use such information to formulate an educated guess. Guessing is utilized in both Dummy Estimators ([Dummy Classifier](#dummy-classifier), [Dummy Regressor](#dummy-regressor)) as well as the [Missing Data Imputer](#missing-data-imputer).

The Strategy interface provides an API similar to Transformers as far as fitting, however, instead of being fit to an entire dataset, each Strategy is fit to an array of either continuous or discrete values.

To fit a Strategy to an array of values:
```php
public fit(array $values) : void
```

To make a guess based on the fitted data:
```php
public guess() : mixed
```

##### Example:
```php
use Rubix\ML\Other\Strategies\BlurryMedian;

$values = [1, 2, 3, 4, 5];

$strategy = new BlurryMedian(0.05);

$strategy->fit($values);

var_dump($strategy->range()); // Min and max guess for continuous strategies

var_dump($strategy->guess());
var_dump($strategy->guess());
var_dump($strategy->guess());
```

##### Output:
```sh
array(2) {
  [0]=> float(2.85)
  [1]=> float(3.15)
}

float(2.897176548)
float(3.115719462)
float(3.105983314)
```
Strategies are broken up into the Categorical type and the Continuous type. You can output the set of all possible categorical guesses by calling the `set()` method on any Categorical Strategy. Likewise, you can call `range()` on any Continuous Strategy to output the minimum and maximum values the guess can take on.

Here are the guessing Strategies available to use in Rubix.

### Blurry Mean
This strategy adds a blur factor to the mean of a set of values producing a random guess centered around the mean. The amount of blur is determined as the blur factor times the standard deviation of the fitted data.

##### Continuous

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | blur | 0.3 | float | The amount of gaussian noise to add to the guess. |

##### Example:
```php
use Rubix\ML\Other\Strategies\BlurryMean;

$strategy = new BlurryMean(0.05);
```

### Blurry Median
A robust strategy that uses the median and median absolute deviation (MAD) of the fitted data to make guesses.

##### Continuous

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | blur | 0.3 | float | The amount of gaussian noise to add to the guess. |

##### Example:
```php
use Rubix\ML\Other\Strategies\BlurryMedian;

$strategy = new BlurryMedian(0.5);
```

### K Most Frequent
This Strategy outputs one of K most frequent discrete values at random.

##### Categorical

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | k | 1 | int | The number of most frequency categories to consider when formulating a guess. |

##### Example:
```php
use Rubix\ML\Other\Strategies\KMostFrequent;

$strategy = new KMostFrequent(5);
```

### Lottery
Hold a lottery in which each category has an equal chance of being picked.

##### Categorical

##### Parameters:
This Strategy does not have any parameters.

##### Example:
```php
use Rubix\ML\Other\Strategies\Lottery;

$strategy = new Lottery();
```

### Popularity Contest
Hold a popularity contest where the probability of winning (being guessed) is based on the category's prior probability.

##### Categorical

##### Parameters:
This Strategy does not have any parameters.

##### Example:
```php
use Rubix\ML\Other\Strategies\Lottery;

$strategy = new PopularityContest();
```

### Wild Guess
It is what you think it is. Make a guess somewhere in between the minimum and maximum values observed during fitting with equal probability given to all values within range.

##### Continuous

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | precision | 2 | int | The number of decimal places of precision for each guess. |

##### Example:
```php
use Rubix\ML\Other\Strategies\WildGuess;

$strategy = new WildGuess(5);
```

### Helpers


### Params
Generate distributions of values to use in conjunction with [Grid Search](#grid-search) or other forms of model selection and/or cross validation.

To generate a *unique* distribution of integer parameters:
```php
public static ints(int $min, int $max, int $n = 10) : array
```

To generate a distribution of floating point parameters:
```php
public static floats(float $min, float $max, int $n = 10) : array
```

To generate a uniform grid of parameters:
```php
public static floats(float $start, float $end, int $n = 10) : array
```

##### Example:
```php
use Rubix\ML\Other\Helpers\Params;

$ints = Params::ints(0, 100, 5);

$floats = Params::floats(0, 100, 5);

$grid = Params::grid(0, 100, 5);

var_dump($ints);
var_dump($floats);
var_dump($grid);
```

##### Output:
```sh
array(5) {
  [0]=> int(88)
  [1]=> int(48)
  [2]=> int(64)
  [3]=> int(100)
  [4]=> int(41)
}

array(5) {
  [0]=> float(42.65728411)
  [1]=> float(66.74335233)
  [2]=> float(15.1724384)
  [3]=> float(71.92631156)
  [4]=> float(4.63886342)
}

array(5) {
  [0]=> float(0)
  [1]=> float(25)
  [2]=> float(50)
  [3]=> float(75)
  [4]=> float(100)
}

```

##### Example:
```php
use Rubix\ML\GridSearch;
use Rubix\ML\Other\Helpers\Params;
use Rubix\ML\Clusterers\FuzzyCMeans;
use Rubix\ML\Kernels\Distance\Diagonal;
use Rubix\ML\Kernels\Distance\Minkowski;
use Rubix\CrossValidation\KFold;
use Rubix\CrossValidation\Metrics\VMeasure;

...
$params = [
	Params::grid(1, 5, 5), Params::floats(1.0, 20.0, 20), [new Diagonal(), new Minkowski(3.0)],
];

$estimator = new GridSearch(FuzzyCMeans::class, $params, new VMeasure(), new KFold(10));

$estimator->train($dataset);

var_dump($estimator->best());
```

##### Output:

```sh
array(3) {
  [0]=> int(4)
  [1]=> float(13.65)
  [2]=> object(Rubix\ML\Kernels\Distance\Diagonal)#15 (0) {
  }
}
```

---
### Tokenizers
Tokenizers take a body of text and converts it to an array of string tokens. Tokenizers are used by various algorithms in Rubix such as the [Word Count Vectorizer](#word-count-vectorizer) to encode text into word counts.

To tokenize a body of text:
```php
public tokenize(string $text) : array
```

##### Example:
```php
use Rubix\ML\Extractors\Tokenizers\Word;

$text = 'I would like to die on Mars, just not on impact.';

$tokenizer = new Word();

var_dump($tokenizer->tokenize($text));
```

##### Output:
```sh
  array(10) {
    [0]=> string(5) "would"
	[1]=> string(4) "like"
	[2]=> string(2) "to"
	[3]=> string(3) "die"
	[4]=> string(2) "on"
	[5]=> string(4) "Mars"
	[6]=> string(4) "just"
	[7]=> string(3) "not"
	[8]=> string(2) "on"
	[9]=> string(6) "impact"
  }
```

Below are the Tokenizers available in Rubix.

### Whitespace
Tokens are delimited by a user-specified whitespace character.

##### Parameters:
| # | Param | Default | Type | Description |
|--|--|--|--|--|
| 1 | delimiter | ' ' | string | The whitespace character that delimits each token. |

##### Example:
```php
use Rubix\ML\Extractors\Tokenizers\Whitespace;

$tokenizer = new Whitespace(',');
```

### Word Tokenizer
Tokens are matched via regular expression designed to pick out words from a block of text. Note that this tokenizer will only pick up on words that are 2 or more characters.

##### Parameters:
This Tokenizer does not have any parameters.

##### Example:
```php
use Rubix\ML\Extractors\Tokenizers\Word;

$tokenizer = new Word();
```

---
## Testing
Rubix utilizes a combination of static analysis and unit tests to reduce errors in code. Rubix provides two Composer scripts that can be run from the root directory that automate the testing process.

To run static analysis:
```sh
composer analyze
```

To run the unit tests:
```sh
composer test
```

---
## Contributing
Please make sure all your code is tested and passes static analysis (see [Testing](#testing) section above) before submitting it to the repository.
