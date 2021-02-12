---
title: "* Reduced Order Modeling"
collection: research
excerpt: "<p style='text-align: justify;'> Reduced order models (ROMs) are low-dimensional representation that is computationally efficient to solve, while capturing the main characteristics of the investigated system. For example, if you are simulating a fluid flow, you may design your mesh, perform discretization, and solve the governing equations at each grid point for every time step. In this scenario, you are tracking the evolution of the flow at each grid point (representing the degrees of freedom), which is often computationally expensive for complex systems. Instead, you can <em>intelligiently</em> select a few <em>features</em> and track their dynamics to reveal the equivalent amount of information about that system. Naively, you can use a coarse-grained simulation (e.g., replace your initial 1000*1000*1000 mesh by 10*10*10). However, this would significantly hurt the resulting accuracy and stability charachteristics. You can also think of a non-uniform mesh with a few grid points, located at the regions of action (e.g., something like Gaussian quadrature in numerical integration). Now, it is clear that the smart selection of the features that sufficiently describe the system is a key for effective ROMs. </p> "
permalink: /research/2_rom
---

<p style='text-align: justify;'> Despite the gigantic progress in computational power and numerical simulations accuracy, dealing with complex realisticsituations is still prohibitive. This is particularly important in geophysical flows (e.g., atmosphere and oceans) characterized by a wide span of spatiotemporal scales. Resolving all of these scales on a fine grid covering the globe is just impossible, even with the largest supercomputer in the world nowadays. Reduced order modeling offers an alternative to handle these complex simulations in a more efficient way. In general, a reduced order models (ROMs) respresents approximate substitutes to the original system. Those substitutes should be cheaper to solve and analyze while retaining similar dynamics to the original system. Fortunately, this is feasible given the fact that these complex systems (e.g., fluid flows) are often dominated by a few underlying dynamical structures controlling most of the mass, momentum, and energy transfer. The idea of ROM is simple; insteadof <em>'watching'</em> each grid point, we may just follow a small number of features and still be able to know equivalent amount ofinformation </p>


<p style='text-align: justify;'> In other words, rather than simulating every single point (which represents a degree of freedom in computations), ROM enables us to detect the major directions over which most variations occur. By superposing the contributions of a small number of these directions, an approximate <em>surrogate</em> of the original system is obtained. The remaining directions are cut-off assuming their contributions are minimum. Dealing with that truncated surrogate saves a large portion of computational power, time, and storage. This is especially evident when multiple forward simulations are required as in digital twin applications. This also extends to data assimilation, optimal control, parameter estimation, and uncertainty quantification frameworks. </p>

<p style='text-align: justify;' style='color:blue'> <strong>To buid a ROM, we need to answer two main questions; (1) what are the most important handful of features that reveals the essential information we care about?, and (2) how can we track or model the dynamics of these features efficiently and accurately? </strong> </p>

<p style='text-align: justify;'> Regarding the first question, for some cases, this can be done by analyzing the system considering a 1D or 2D models if the variation along the remaining direction(s) is insignificant. On the other hand, this feature selection process can be automated thanks to advances in data-driven pattern recognition algorithms. One of the most popular techniques in fluid mechanics community is the proper orthogonal decomposition (POD), also knonw as principal component analysis (PCA). POD works by extracting spatial basis functions (or modes), defining the underlying patterns or coherent structures that dominate the flow. From a linear algebra perspective, the POD approach can be formulated as a singular value decomposition, providing an optimal low-rank matrix approximation. This, indeed, can leverage highly performant and scalable algorithms to handle extremely large datasets, benefiting from the rich legacy of linear algebra investigations. Considering only the first few principal components (i.e. the leading left singular vectors of the data matrix), one can define an optimal <em>linear</em> subspace onto which the data can be orthogonally projected while minimizing and estimating the amount of information lost in the process. From a statistical point of view, this orthogonal projection provides <em>linearly uncorrelated</em> features. Despite that, it cannot reveal nonlinear correlations in the data. On the other hand, <em>manifold learning</em> (or representation learning) techniques aim at accounting for such nonlinear correlations to further reduce the dimensionality of the problem. Examples include neural network-based autoencoder (AE) applications, composed mainly of two parts; encoder and decoder. For the encoder, the input is the full order flow field, while the output is a reduced order representation of the field, defined by a bottleneck layer (i.e., using a smaller number of neurons). This represents the projection step in ROM paradigm. The decoder does the opposite job, taking the reduced representation and recovering back the flow field (i.e., reconstruction). This is often considered as a generalization of the POD process to account for nonlinear manifolds.</p>



<p style='text-align: justify;'> 

</p>


<p style='text-align: justify;'> 

</p>



<p style='text-align: justify;'> 

</p>


<!-- <p align='center'> <img src='/images/dt.png' width='75%'> </p>
<img align='right' src='/images/dt3.jpg' width='45%'> Imagine that your computer carries a software that duplicates yourself, including your body, organs, and behavior (maybe?). You might wear an Apple watch that streams your vital signs to that software. 
Then, your DT can process and analyze these data to provide you with any potential health problems, and even recommend a doctor visit. 
Moreover, it might be connected to your credit cards, bandk accounts, and insurance companies to predict the influence a purchase you might do onto your future savings.
Thus, you can adjust your consumption, selling, or purchasing accordingly. **It is really interesting, isn't it?** 
-->
