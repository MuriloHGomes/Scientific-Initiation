# Scientific-Initiation
Development of a project to analyse topological features in skin nevus images using persistence homology. 

In this first approach we investigated the hypothesis that the abstract concept of homogeneity of symmetry, edge and colouring of spots could be quantified in terms of the quantity, persistence and degree of homologies found by different persistence homology methods and modelling. The aim is to find a model that allows us to distinguish at least those classes that present a health risk from those that do not. 

In the following code we test the following modelling:

  - Pre-process each image by: resize, take region of interess (using Topological Image Processing), create a multi-channel image grouping RGB and HSV channels;
  - Selecting m=10 random regions on each multi-channel image;
  - For every sub-region found in each image, we calculate the persistence homology using the cubical homology library of Giotto-TDA
  - Each image is then represented by a distance matrix calculated from the difference between the cubic persistence homology of its sub-regions. The difference are calculated by the bottleneck or Wasserstein metrics;
  - As we know that each distance matrix can be represented by a graph, we used the Vietoris-Rips algorithm from the GHUDI library to calculate the persistence homology associated with each graph. This gives us an abstract way of quantifying the persistence homology of the whole image from small parts of it.

Our hypothesis is that images with a more homogeneous texture, i.e. more symmetrical, with more regular edges and colouring, will have fewer differences between the persistence homologies calculated in their sub-regions. Consequently, for each distance used, we need to find distance matrices that represent these differences in such a way that they have lower values than those calculated for less homogeneous patches.  In this way, we would distinguish these classes by observing that the graphs representing the less homogeneous images would be more sparse than the graphs representing the more homogeneous patches.  We could then quantify this sparsity by the degree, number and lifetime of homology features found in the graph representing each image. We hypothesise that less sparse graphs should have a greater number and longer lifetime of higher degrees of homology compared to more sparse graphs. 
