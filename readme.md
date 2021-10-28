# Matching Cut Implementation
An implementation submitted for the Parameterized Algorithms Course at NITC in 2021.
The python notebook consists of the implementation of FPT kernelisation algorithm mentioned in the paper<br>[*Komusiewicz, Christian & Kratsch, Dieter & Le, Van Bang. (2019). Matching Cut: Kernelization, Single-Exponential Time FPT, and Exact Exponential Algorithms. Discrete Applied Mathematics. 283. 10.1016/j.dam.2019.12.010.*](https://drops.dagstuhl.de/opus/volltexte/2019/10220/pdf/LIPIcs-IPEC-2018-19.pdf)<br>
<br>Under each subsection of the code, the details of the implementation are specified in the python notebok as markdown and can be accessed by simply opening the notebook <br><br> 
The is divided into implementation into 4 different parts - the graph specific functionalities, functions that support the matching cut problem and finally the kernel class that contains the functions to run the kernelisation algorithm. This is followed by outputs from the testcases ran. The testcases are available [here](https://drive.google.com/drive/folders/1sojbaOGuOrXuOJmeJ4WcAYFs4n2ol4Si?usp=sharing)<br>
Each of these sections can be accessed through the Table of Contents in the left tab of the notebook.
## Libraries/Modules
The implementation start with the libraries we are going to use for various operations<br>
***networkx*** provides support to visualise the graph we feed to it<br>
***matplotlib*** provide support for plotting which combined with networkx gives us the visualisation we need<br>
***copy*** provides a tool deepcopy to create a copy of even a user defined data structure
## Graph Defintion and Functionalities
It continues with defining how our graph is implemented as code followed by the methods to manipulate(add/delete) and get subgraphs from it <br><br>
Usage of the functions:<br>
`restoreGraph()` -> replaces the existing graph with a backup created when the graph was generated <br>
`visualise()` -> generates a plot of the graph to visualise, using networkx <br>
`deleteNodes(nodeList)` -> delete a list of nodes from the graph <br>
`deleteEdges(edgeList)` -> delete a list of edges from the graph <br>
`addEdges(edgeList)` -> add a list of edges to the graph <br>
`generateGraph(txt)` -> takes a string of a textfile name to generate a graph. The graph requires a specific formatting: the first line contains an integer providing the number of nodes in our graph, the following lines contains a pair of labels of the nodes providing information about edges between these 2 nodes <br>
`generateFile(txt)` -> takes a string of textfile name to generate a file based on the format mentioned above. Default generate file name is set as genFile.txt<br>
`getComponent(node)` -> takes a node to return the tree in the graph forest containing that node <br>
`findClusters()` -> returns all the trees in the graph forest
We run a test of the graph class by generating through [csacademy.com/app/graph_editor](https://csacademy.com/app/graph_editor/)
## Functions for Matching Cut
We have 3 functions:<br>
`cluster3fApprox(G)` -> Generates a 3 factor approximation of cluster vertex deletion problem <br>
`isCut(G, M)` -> checks if a given edge set M is a cut <br>
`isMatchingCut(G, C)` -> Given a vertex set, we check if that and the remaining graph can form a partition such that the set of edges between them is a matching cut <br>
`matchingCut(G, M, V)` -> Recursively applies a bruteforce to find if there is a matching cut in the graph
## Kernelisation Algorithm
The class matchingCutKernel consists of functions to calculate the kernel of the problem <br>
It has 8 functions for the rules defined in the report and the paper. <br> A `n2()` function is also defined to calculate the N2 of each vertices in U as per the defintion provided in the report<br> The `checkRules()` checks the rules in sequence and return True for the first True returned. This supports the kernelisation method required.  <br>
`getKernel()` runs the rules in sequence untill it can no longer reduce the graph. It also visualises the rules passed indicating if a rule is applied and a visualisaton of the graph and the clusters are plotted.
## Test Cases
The test cases section contains the output of the test cases of the graphs provided in the drive featuring the rules ran and the output graph along with the graph without the U set.<br>
The snippets may not be required to be run to obtain the outputs for the testcases but it can be run if necessary
Documentation of the algorithm discussed in the paper compiled into a report: https://docs.google.com/document/d/1ii7yvMGJRXF-N5eaUHlymW9HXF5UZ-WLjlIYIOkz4bI/edit?usp=sharing
