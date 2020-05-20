---
layout: post
title:  "Interpolation"
date:   2020-05-20 00:29:00 -0400
categories: machine learning
---

## Test Header

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
