# Implementation-of-Logistic-Regression-Using-Gradient-Descent

## AIM:
To write a program to implement the the Logistic Regression Using Gradient Descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Read the given dataset.
2. Fitting the dataset into the training set and test set.
3. Applying the feature scaling method.
4. Fitting the logistic regression into the training set.
5. Prediction of the test and result
6. Making the confusion matrix
7. Visualizing the training set results.

## Program:
```
/*
Program to implement the the Logistic Regression Using Gradient Descent.
Developed by: HEMANTH KUMAR B.
RegisterNumber:  21222044047
*/
import numpy as np
import matplotlib.pyplot as plt
from scipy import optimize
data = np.loadtxt("ex2data1.txt",delimiter=',')
X = data[:,[0,1]]
y = data[:,2]
X[:5]
y[:5]
plt.figure()
plt.scatter(X[y==1][:,0],X[y==1][:,1],label="Admitted")
plt.scatter(X[y==0][:,0],X[y==0][:,1],label="Not admitted")
plt.xlabel("Exam 1 score")
plt.ylabel("Exam 2 score")
plt.legend()
plt.show()
def sigmoid(z):
  return 1/(1+np.exp(-z))
plt.plot()
X_plot = np.linspace(-10,10,100)
plt.plot(X_plot,sigmoid(X_plot))
plt.show()
def costFunction(theta,X,Y):
  h = sigmoid(np.dot(X,theta))
  J = -(np.dot(y,np.log(h))+np.dot(1-y,np.log(1-h))) / X.shape[0]
  grad = np.dot(X.T,h-y) / X.shape[0]
  return J,grad
X_train = np.hstack((np.ones((X.shape[0],1)),X))
theta = np.array([0,0,0])
J, grad  = costFunction(theta,X_train,y)
print(J)
print(grad)
X_train = np.hstack((np.ones((X.shape[0],1)),X))
theta = np.array([-24,0.2,0.2])
J, grad  = costFunction(theta,X_train,y)
print(J)
print(grad)
def cost(theta,X,y):
  h = sigmoid(np.dot(X,theta))
  J = -(np.dot(y,np.log(h))+np.dot(1-y,np.log(1-h))) / X.shape[0]
  return J

def gradient(theta,X,y):
  h = sigmoid(np.dot(X,theta))
  grad = np.dot(X.T,h-y)/X.shape[0]
  return grad
X_train = np.hstack((np.ones((X.shape[0],1)),X))
theta = np.array([0,0,0])
res = optimize.minimize(fun=cost,x0=theta,args=(X_train,y),method='Newton-CG',jac=gradient)
print(res.fun)
print(res.x)
def plotDecisionBoundary(theta,X,y):
  x_min ,x_max = X[:,0].min()-1,X[:,0].max()+1
  y_min ,y_max = X[:,1].min()-1,X[:,1].max()+1
  xx,yy = np.meshgrid(np.arange(x_min,x_max,0.1),
                      np.arange(y_min,y_max,0.1))
  X_plot = np.c_[xx.ravel(),yy.ravel()]
  X_plot = np.hstack((np.ones((X_plot.shape[0],1)),X_plot))
  y_plot = np.dot(X_plot,theta).reshape(xx.shape)

  plt.figure()
  plt.scatter(X[y==1][:,0],X[y==1][:,1],label="Admitted")
  plt.scatter(X[y==0][:,0],X[y==0][:,1],label="Not admitted")
  plt.contour(xx,yy,y_plot,levels=[0])
  plt.xlabel("Exam 1 score")
  plt.ylabel("Exam 2 score")
  plt.legend()
  plt.show()
plotDecisionBoundary(res.x,X,y)
prob = sigmoid(np.dot(np.array([1,45,85]),res.x))
print(prob)
def predict(theta,X):
  X_train = np.hstack((np.ones((X.shape[0],1)),X))
  prob = sigmoid(np.dot(X_train,theta))
  return (prob>=0.5).astype(int)
np.mean(predict(res.x,X)==y)

```

## Output:
![image](https://user-images.githubusercontent.com/116530537/204099275-2e070272-96cd-4340-9909-b042b4b3378e.png)

![logistic regression using gradient descent2](folder/s1.png)
![logistic regression using gradient descent2](folder/s2.png)
![image](https://user-images.githubusercontent.com/116530537/204099295-362f2dae-c6a2-4f3b-bd2f-b5a9755004fb.png)

![image](https://user-images.githubusercontent.com/116530537/204099332-415e00eb-245a-4326-a47b-fc06f78b63c9.png)

![image](https://user-images.githubusercontent.com/116530537/204099350-05c5fb09-dda9-4beb-bf5a-3e6dc563f65b.png)

![logistic regression using gradient descent3](folder/s3.png)
![logistic regression using gradient descent4](folder/s4.png)



## Result:
Thus the program to implement the the Logistic Regression Using Gradient Descent is written and verified using python programming.

