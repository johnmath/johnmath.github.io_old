---
layout: post
title:  "Reproducing 'Does data interpolation contradict statistical optimality?'"
date:   2020-05-20 00:29:00 -0400
categories: machine learning
---
#### Introduction

During one of my biweekly research meetings, my group reviewed *[Does data interpolation contradict statistical optimality?](https://arxiv.org/abs/1806.09471)* by Mikhali Belkin, Alexander Rakhlin, and Alexandre B, Tsybakov

The aim of this paper was to show that interpolating training data can still lead to optimal results in nonparametric regression and prediction with square loss. Since the double descent phenomenon exhibits itself when the model capacity surpasses the "interpolation threshold", I thought that reproducing the results from this paper would help me understand how a model interpolates data.

[1]


<img src="{{site.baseurl}}/media/double_descent.png" alt="" style='height: 75%; width: 75%; object-fit: contain'>)


#### Math and Code

This paper takes a look at interpolation using the **Nadaraya-Watson Estimator**.

Let $$(X, Y)$$ be a random pair on $$\mathbb{R}^{d} \times \mathbb{R}$$ with distribution $$P_{XY}$$, and let $$ \mathbb{E}[Y \vert X = x]$$ be the regression function.


Given a sample $$(X_{1}, Y_{1}),...,(X_{n}, Y_{n})$$ drawn independently from $$P_{XY}$$, we can approximate $f(x)$ using the Nadaraya-Watson Estimator where $$K: \mathbb{R}^{d} \rightarrow \mathbb{R}$$ is a kernel function and $$h > 0$$ is a bandwidth



<img src="{{site.baseurl}}/media/sine_nw_singular.gif" alt="" style='height: 75%; width: 75%; object-fit: contain'>


```python
def nadaraya_watson_estimator(x, X, Y, h, K=stats.norm.pdf):
    cols=[]
    for i in range(len(X)):

        cols.append(np.array(K((x - X[i])/h)))


    Kx = np.column_stack(tuple(cols))

    row_sums = np.sum(Kx, axis=1)

    W = Kx / row_sums[:, None]

    result = np.matmul(W,Y)
    result.shape = (result.shape[0], 1)
    return result
```


References:

* Does data interpolation contradict statistical optimality? - <https://arxiv.org/abs/1806.09471>
* [1] - <https://www.cs.ubc.ca/labs/lci/mlrg/slides/dl_generalization.pdf>
