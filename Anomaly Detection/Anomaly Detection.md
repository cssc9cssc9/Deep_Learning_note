# Description of anomaly detection
Make machine know the data is it doesn't know.
- Given a set of training data $\{x_1, x_2,\dots, x_N\}$
- We want to find a function detecting input $x$ is **similar to training data or not**.

![[anomaly detection_1.jpg]]
Anomaly detection is as known as outlier detection, novelty detection and exceptions detection.

## What is Anomaly
If a observation is significally different to the other data observation, then we say the observation is anomaly (outlier).

## Application
1.  Fraud Detection 
	- Training data: Normal comsume behavior.
	- Target: Detect the behavior is fraud or not.
	- Real data resource: 
		*  [Synthetic Financial Datasets For Fraud Detection](https://www.kaggle.com/ntnu-testimon/paysim1/home)
		* [Credit Card Fraud Detection](https://www.kaggle.com/mlg-ulb/creditcardfraud/home)
2. Network Instrusion Detection
	* Training data: Normal In
	* Target: Detect the behavior is intrusion or not.
	* Real data resource: 
		* [KDD Cup 1999 Data](https://kdd.ics.uci.edu/databases/kddcup99/kddcup99.html)
3. Cancer Detection
	* Training data: Normal Ceil
	* Target: Detect the cancer ceil
	* Real data resource:
		* [Predict whether the cancer is benign or malignant](https://www.kaggle.com/uciml/breast-cancer-wisconsin-data/home)


## Binary Classification is not realistic
As our intuition, we would think binary classification can be applied in anomaly detection, like below:
- Given normal data ${x_1, x_2, \dots, x_N}\rightarrow C_0$ 
- Given anomaly data $\bar{x_1},\bar{x_2},\dots, \bar{x_N}\rightarrow C_1$
- Then training a binary classifer
- Done.

Whereas, is not realistic!

1. The anomaly is universal such that it cannot be considered as a class.
	![[anomaly detection_2.jpg|480]]
2. In some cases, it is difficult to find anomaly example like state-of-the art hacking behavior.

## Categories of anomaly detection
We have training data $\{x_1\dots x_N\}$, then we can categorize the anomaly detection problem into:
- Supervised or Unsupervised
	* Supervised: 
		* Training data with labels $y=\{y_1,\dots,y_N\}$
		* Targer: The classifer can output $\bar{y_i }:$`unknown`, where $\bar{y_i} \notin y$. $\rightarrow$ Open-set recognition.
	* Unsupervised:
		* Clean: All the training data is normal.
		* Polluted: A little bit of training data is anomaly.

### 1. Supervised anomaly problem 
#### Case: [Simpson's characters detection](https://www.kaggle.com/alexattia/the-simpsons-characters-dataset)
![[anomaly_detection_3.jpg|560]]
1. Construct the classifier to classifer the character of Simpson's family.
2. Furthermore, we let the classifier output **confidence score** to score the confidence of class it predict.
![[anomaly_detection_4.jpg|560]]
3. Based on the confidence score $c$, we can set some threshold $f(x)=\begin{cases}\text{normal},& c(x)>\lambda \\anomaly, &c(x)\leq\lambda\end{cases}$