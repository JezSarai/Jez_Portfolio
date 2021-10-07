# Prediction of Heart Attack

## Code
```markdown
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

dataset = pd.read_csv('heart.csv')
X = dataset.iloc[:, :-1].values
y = dataset.iloc[:, -1].values

from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.2, random_state = 0)

from sklearn.linear_model import LinearRegression
regressor = LinearRegression()
regressor.fit(X_train, y_train)

y_pred = regressor.predict(X_test)

y_pred = regressor.predict(X_test)
np.set_printoptions(precision=2)
print(np.concatenate((y_pred.reshape(len(y_pred),1), y_test.reshape(len(y_test),1)),1))

print(regressor.coef_)
print(regressor.intercept_)
```

## Results
[[ 0.07  0.  ]
 [ 0.72  1.  ]
 [ 0.74  0.  ]
 [ 0.01  0.  ]
 [ 0.24  1.  ]
 [ 0.52  0.  ]
 [ 0.18  0.  ]
 [ 0.27  0.  ]
 [-0.19  0.  ]
 [-0.24  0.  ]
 [ 0.65  1.  ]
 [ 0.9   1.  ]
 [ 0.11  0.  ]
 [ 0.76  1.  ]
 [ 0.99  1.  ]
 [ 0.62  1.  ]
 [ 0.17  1.  ]
 [ 0.65  1.  ]
 [-0.15  0.  ]
 [ 0.76  1.  ]
 [ 0.72  1.  ]
 [ 0.45  0.  ]
 [ 0.25  0.  ]
 [ 0.24  0.  ]
 [ 0.8   1.  ]
 [ 0.58  0.  ]
 [ 0.32  0.  ]
 [ 0.48  0.  ]
 [ 1.06  1.  ]
 [ 0.61  1.  ]
 [ 0.62  0.  ]
 [-0.06  0.  ]
 [ 1.    1.  ]
 [ 0.66  1.  ]
 [ 0.87  1.  ]
 [ 0.57  0.  ]
 [ 0.07  0.  ]
 [ 0.78  1.  ]
 [ 0.18  0.  ]
 [ 0.32  0.  ]
 [ 0.67  1.  ]
 [ 0.74  1.  ]
 [ 0.43  1.  ]
 [ 0.19  0.  ]
 [ 0.52  1.  ]
 [ 0.65  1.  ]
 [ 0.75  1.  ]
 [ 0.6   0.  ]
 [ 0.14  0.  ]
 [ 0.74  1.  ]
 [ 0.78  1.  ]
 [ 0.57  1.  ]
 [ 1.    1.  ]
 [ 0.77  1.  ]
 [ 1.25  1.  ]
 [ 0.25  0.  ]
 [ 0.93  1.  ]
 [ 0.88  0.  ]
 [ 0.69  1.  ]
 [ 0.95  1.  ]
 [ 0.72  1.  ]]

[-0.   -0.23  0.1  -0.   -0.   -0.04  0.01  0.   -0.16 -0.06  0.03 -0.12
 -0.09]

0.9006087429910432
