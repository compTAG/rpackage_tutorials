---
layout: "post"
title: "Persistent Homology and Persistence Diagrams"
author: "Ben Holmgren"
---

# Introduction to Persistent Homology


#### Objectives
* Understand and be able to define persistent homology
* Conceptualize the importance of persistent homology in TDA
* Be able to construct and read a persistence diagram

---
In TDA, a core approach to understanding the topological structure of data is through persistent homology, which quantifies the persistence of features in a family of nested topological spaces.
---
In layman's terms, when we are looking at a data set, most often in the form of a point cloud, it is helpful to be able to look at the 'shape' of that data. To do so, we can observe the persistence of features in that data as we manipulate certain parameters.
---
In TDA, we use different filtrations as a means to manipulate these specific parameters. Inevitably, this will cause features in the data set to emerge (so called 'births') and disappear, (so called 'deaths'). We can think of this manipulation as occurring over a time parameter t, and in plotting the times at which births and deaths occur, we gain a helpful visualization of the structure of a data set which is algebraic in nature.
---
For example, imagine a point cloud along the unit circle.
![circular point cloud](/assets/ph&pd-images/unit_circle_pt_cloud.png)
---
Then, recall a ![Rips Filtration](https://comptag.github.io/rpackage_tutorials/2019/04/15/rips.html), and imagine the simplicial complexes that would be created over time if we were to conduct the filtration on our point cloud.
---
At time 0, we would only be able to see all of the vertices in the data set. Over time, higher dimensional simplices would be added, and lower dimensional simplices would disappear as a result. To visualize, we can trace these birth and death events by plotting them on a grid, with each axis devoted to equal units of time.
---
![unit circle rips pd](/assets/ph&pd-images/unit_circle_rips_pd.png)
---
Since both axes represent the same units of time, the line running through the middle of the figure is representative of the course of time; if every feature were to be born and die immediately, all of the points would lie along this line. Note that all features are born at time 0, since the Rips filtration begins with all vertices simultaneously. Features die respective to when they are engulfed by the growing simplicial complex, and one feature dies at time infinity (meaning it never dies). This is the simplex which is the final remaining feature in the simplicial complex.
