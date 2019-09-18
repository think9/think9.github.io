---
layout: post
title: 텐서플로 예제
subtitle: Python Tensorflow Examples
---

## Linear Regression

```python
import tensorflow as tf

x_data = [1., 2., 3.]
y_data = [1., 2., 3.]

# try to find values for w and b that compute y_data = W * x_data + b
W = tf.Variable(tf.random_uniform([1], -1.0, 1.0))
b = tf.Variable(tf.random_uniform([1], -1.0, 1.0))

# my hypothesis
hypothesis = W * x_data + b

# Simplified cost function
cost = tf.reduce_mean(tf.square(hypothesis - y_data))

# minimize
rate = tf.Variable(0.1)  # learning rate, alpha
optimizer = tf.train.GradientDescentOptimizer(rate)
train = optimizer.minimize(cost)

# before starting, initialize the variables. We will 'run' this first.
init = tf.initialize_all_variables()

# launch the graph
sess = tf.Session()
sess.run(init)

# fit the line
for step in range(2001):
    sess.run(train)
    if step % 20 == 0:
        print('{:4} {} {} {}'.format(step, sess.run(cost), sess.run(W), sess.run(b)))

# learns best fit is W: [1] b: [0]
```

<br>

## Linear Regression using placeholder

```python
import tensorflow as tf

x_data = [1., 2., 3., 4.]
y_data = [2., 4., 6., 8.]

# range is -100 ~ 100
W = tf.Variable(tf.random_uniform([1], -100., 100.))
b = tf.Variable(tf.random_uniform([1], -100., 100.))

X = tf.placeholder(tf.float32)
Y = tf.placeholder(tf.float32)

hypothesis = W * X + b

cost = tf.reduce_mean(tf.square(hypothesis - Y))

rate = tf.Variable(0.1)
optimizer = tf.train.GradientDescentOptimizer(rate)
train = optimizer.minimize(cost)

init = tf.initialize_all_variables()

sess = tf.Session()
sess.run(init)

for step in range(2001):
    sess.run(train, feed_dict={X: x_data, Y: y_data})
    if step % 20 == 0:
        print(step, sess.run(cost, feed_dict={X: x_data, Y: y_data}), sess.run(W), sess.run(b))

print(sess.run(hypothesis, feed_dict={X: 5}))           # [ 10.]
print(sess.run(hypothesis, feed_dict={X: 2.5}))         # [5.]
print(sess.run(hypothesis, feed_dict={X: [2.5, 5]}))    # [  5.  10.], 원하는 X의 값만큼 전달.
```

<br>

## Find closest equation

```python
import tensorflow as tf
import numpy as np
import matplotlib.pyplot as plt

N = 50
x_data = np.linspace(-2, 2, N).astype(np.float32)
w, b = 3, 10
np.random.seed(1)
y_data = w*x_data + b + np.random.normal(0, 1, N) #직선에 가까운 잡음 추가
y_data = y_data.astype(np.float32)

X = tf.placeholder(tf.float32, [None])
Y = tf.placeholder(tf.float32, [None])
B = tf.Variable(tf.zeros([1]))
W = tf.Variable(tf.zeros([1]))
Y_ = W*X + B

cost = tf.reduce_sum(tf.square(Y - Y_)) #(Y-Y_)**2
train_step = tf.train.GradientDescentOptimizer(0.01).minimize(cost)

print(x_data)
print(y_data)

with tf.Session() as sess:
    sess.run(tf.global_variables_initializer())

    for step in range(10):
        sess.run(train_step, feed_dict={X:x_data, Y:y_data})
        w_pred = sess.run(W).tolist()[0]
        b_pred = sess.run(B).tolist()[0]
        print(step, w_pred, b_pred)

    y_pred = w_pred*x_data + b_pred
    plt.plot(x_data, y_data, 'ro', label="points in y={}*x+N(0,1)".format(w, b))
    plt.plot(x_data, y_pred, 'g', label="predictions y={}*x {:+}".format(w_pred, b_pred))
    
plt.legend(loc="best")
plt.show()
```
