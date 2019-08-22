[![DOI](https://zenodo.org/badge/136833836.svg)](https://zenodo.org/badge/latestdoi/136833836)


# Image Characterization through Layered Estimations of Algorithmic Information (Kolmogorov Complexity)

![morphological-perturbation](https://raw.githubusercontent.com/andandandand/images-for-colab-notebooks/master/layered-bdm.png)

![weighted-graph](https://raw.githubusercontent.com/andandandand/images-for-colab-notebooks/master/weighted-graph-adj-matrix.png)

A layered version of the Block Decomposition Method [1, 2] ("Layered BDM"), serves as a descriptor of both weighted networks and grayscale or color images.  This descriptor provides an estimate of Kolmogorov Complexity that's sensitive to morphological perturbation.  To estimate the complexity of a grayscale texture, we quantize it and aggregate the estimated Kolmogorov complexity values of binary 4 x 4 squares, estimated through the Coding Theorem Method [3, 4].

### Pseudocode description of the Layered BDM algorithm
```
// CTMs is a hashtable with binary 2D blocks as keys
// their respective values being estimations of Kolmogorov complexity 
// obtained through the Coding Theorem Method
function LayeredBDM (grayImage, CTMs, blockSize, blockOffset, q)

	// the image is quantized in q digital levels
	imag <- quantize(grayImage, q)
	
	blocksList = {}
	for i in 1:q
	    // the quantized image is binarized through the q digital layers
   		binImag <- binarize(i, imag)
   		// and decomposed into n x n blocks, which are added to the blockList
   		blocksList.append(blockDecompose(binImag, blockSize, blockOffset))

	// we count the appearance of all binary blocks through all layers 
	// and store the count of each into a hash table with the blocks as keys
	// and the blockCount as values
	blockHT(blocks:blockCount) <- countBlocks(blockList)

	// The blocks' CTM values are retrieved from the CTMs hashtable, these and 
	// the Log2 of the cardinality of each are added to compute the BDM value
	lBDM <- CTMs(keys(blockHT)) + Log2(values(blockHT))
	return(lBDM)

```

### References
[1] Antonio Rueda-Toicen, "Morphological Image Analysis through Estimations of Kolmogorov Complexity" (in preparation)

[2] Hector Zenil, Santiago Hernández-Orozco, Narsis A.Kiani, Fernando Soler-Toscano, Antonio Rueda-Toicen, and Jesper Tegner "A Decomposition Method for Global Evaluation of Shannon Entropy and Local Estimations of Algorithmic Complexity", https://arxiv.org/abs/1609.00110

[3] Fernando Soler - Toscano, Hector Zenil, Jean-Paul Delahaye, and Nicolas Gauvrit (2014) "Calculating Kolmogorov Complexity from the Output Frequency Distributions of Small Turing Machines." PLoS ONE 9 (5) : e96223.

[4] Hector Zenil, Fernando Soler-Toscano, K. Dingle, and Aard Louis (2014) "Correlation of Automorphism Group Size and Topological Properties with Program-size Complexity Evaluations of Graphs and Complex Networks", Physica A : Statistical Mechanics and its Applications, vol.404, pp.341-358. 

***If you use this code or algorithm for a publication, please cite the above references and the following***:

Rueda-Toicen, Antonio, Image Analysis with Algorithmic Information, (2018), GitHub repository, https://github.com/andandandand/ImageAnalysisWithAlgorithmicInformation, DOI: /10.5281/zenodo.1291510 

#### BibTex
```
@misc{Rueda-Toicen2018,
  author = {Rueda-Toicen, Antonio},
  title = {Image Analysis with Algorithmic Information},
  year = {2018},
  publisher = {GitHub},
  howpublished = {https://github.com/andandandand/ImageAnalysisWithAlgorithmicInformation},
  DOI = {/10.5281/zenodo.1291510}
  url = {https://doi.org/10.5281/zenodo.1291510}
  }
```

### Author: Antonio Rueda-Toicen
- antonio "dot" rueda "." toicen "at" gmail 'dot' com
- antonio "dot" rueda "." toicen "at" algorithmicnaturelab 'dot' com

### License: FreeBSD 

DOI: https://zenodo.org/record/1291511#.WyWwtKdKhRY
