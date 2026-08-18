# Label Encoding with Pandas and Scikit-learn

## Objective

Convert categorical text values into numeric labels using
`LabelEncoder`.

## Code

``` python
import pandas as pd
from sklearn.preprocessing import LabelEncoder

df = pd.read_csv("data.csv")

le = LabelEncoder()
df["Name"] = le.fit_transform(df["Name"])

print(df)
```

## Explanation

-   `import pandas as pd` imports pandas.
-   `LabelEncoder` converts text categories to integers.
-   `pd.read_csv("data.csv")` loads the CSV.
-   `le = LabelEncoder()` creates the encoder.
-   `fit_transform()` learns unique values and replaces them with
    integers.

## Example

Before:

  Name
  -------
  Ali
  Ahmed
  Sara
  Ali

After:

  Name
  ------
  1
  0
  2
  1

Mapping (alphabetical): - Ahmed → 0 - Ali → 1 - Sara → 2

## Notes

-   Use `LabelEncoder` for categorical features such as Gender or
    Result.
-   Avoid encoding Name in real ML projects because names usually do not
    help prediction.
-   To encode multiple columns:

``` python
for col in ["Gender", "Result", "Name"]:
    df[col] = le.fit_transform(df[col])
```
