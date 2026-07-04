# Matplotlib Line Plot Notes

## Objective

Learn how to create a simple line graph using Matplotlib.

## Code

``` python
import matplotlib.pyplot as plt

values1=(1,2,3,4,5,6)
values2=(10,20,30,40,50,60)

plt.plot(values1,values2,"*:")
plt.xlabel("values of value1")
plt.ylabel("values of value2")
plt.title("Graph")
plt.grid(color='cyan', linestyle='--', linewidth=0.5)
plt.show()
```

## Explanation

-   Import `matplotlib.pyplot` as `plt`.
-   `values1` contains X-axis values.
-   `values2` contains Y-axis values.
-   `plt.plot()` draws a line graph.
-   `"*:"` uses star markers with a dotted line.
-   `xlabel()` sets the X-axis label.
-   `ylabel()` sets the Y-axis label.
-   `title()` adds the graph title.
-   `grid()` customizes the grid.
-   `show()` displays the graph.

## Key Points

-   Matplotlib is used for data visualization.
-   `plot()` creates line charts.
-   Grid makes graphs easier to read.
