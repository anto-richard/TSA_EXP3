# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)

Date: 11-03-24

### AIM:

To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model type to fit the data.

### ALGORITHM:

#### Step 1:

Import the necessary packages.

#### Step 2:

Find the mean, variance and then implement normalization for the data.

#### Step 3:

Implement the correlation using necessary logic and obtain the results.

#### Step 4:

Store the results in an array.

#### Step 5:

Represent the result in graphical representation as given below.

### PROGRAM:

```python

import matplotlib.pyplot as plt
import numpy as np

data = [3, 16, 156, 47, 246, 176, 233, 140, 130,
        101, 166, 201, 200, 116, 118, 247,
        209, 52, 153, 232, 128, 27, 192, 168, 208,
        187, 228, 86, 30, 151, 18, 254,
        76, 112, 67, 244, 179, 150, 89, 49, 83, 147, 90,
        33, 6, 158, 80, 35, 186, 127]
lags = range(35)

# Pre-allocate autocorrelation table:
acorr = len(lags) * [0]

# Mean:
mean = sum(data) / len(data)

# Variance:
var = sum([(x - mean)**2 for x in data]) / len(data)

# Normalized data:
ndata = [x - mean for x in data]

# Go through lag components one-by-one:
for l in lags:
    c = 1 # Self correlation

    if (l > 0):
        tmp = [ndata[l:][i] * ndata[:-l][i]
            for i in range(len(data) - l)]

        c = sum(tmp) / len(data) / var
        #print(c)
        acorr[l] = c

print(acorr)
plt.grid(True)
plt.stem(acorr[:36], use_line_collection=True)
plt.plot(acorr)
plt.title("Autocorrelation plot")
plt.xlabel("Lags")
plt.show()

```

### OUTPUT:

![img4](https://github.com/anto-richard/TSA_EXP3/assets/93427534/6647f9a1-33c6-414f-ade5-b2f3163e4e53)

### RESULT:

Thus, we have successfully implemented the auto correlation function in python.

