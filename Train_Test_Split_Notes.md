# Train-Test Split in Machine Learning using Pandas and Scikit-learn

## Objective

Learn how to divide a dataset into training and testing sets using
`train_test_split()`.

## Code

``` python
import pandas as pd
from sklearn.model_selection import train_test_split

df = pd.read_csv("data.csv")
X = df[["StudentID","Name","Age","Gender","Math","Physics","Chemistry","English","Attendance"]]
Y = df["Result"]

X_train, X_test, y_train, y_test = train_test_split(
    X, Y, test_size=0.2, random_state=42
)
```

## Explanation

-   Read the dataset using `pd.read_csv()`.
-   `X` contains the input features.
-   `Y` contains the target (Result).
-   `train_test_split()` divides the dataset into training and testing
    sets.
-   `test_size=0.2` means 20% testing and 80% training.
-   `random_state=42` ensures the same split every run.

### Output Variables

-   `X_train` -- Training features
-   `X_test` -- Testing features
-   `y_train` -- Training labels
-   `y_test` -- Testing labels

## Why use Train-Test Split?

-   Train the model on one portion of data.
-   Test it on unseen data.
-   Prevent overfitting.
-   Measure model performance fairly.

## Example

For 100 records: - Training: 80 - Testing: 20

## Key Points

-   X = Features (inputs)
-   Y = Label/Target (output)
-   Common split = 80:20
-   Never train and test on the same data.
