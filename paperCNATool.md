# CNATool - Complex Network Analysis Tool
tags:
  - CNATool
  - complex network analysis
  - graph
  - network
  - degree
  - clustering
  - centrality
  - Pajek 
authors:
  - name: Roberto Luiz Souza Monteiro
    orcid: 0000-0002-3931-5953
    equal-contrib: true
    affiliation: "1, 2" # (Multiple affiliations must be quoted)
  - name: Renata Souza Freitas Dantas Barreto
    equal-contrib: true # (This is how you can denote equal contributions between multiple authors)
    affiliation: 2
  - name: Hernane Borges de Barros Pereira
    corresponding: true # (This is how to denote the corresponding author)
    affiliation: 3
affiliations:
 - name: SENAI CIMATEC University, Brasil
   index: 1
 - name: Universidade do Estado da Bahia, Brasil
   index: 2
 - name: Universidade Estadual de Santa Cruz, Brasil
   index: 3
date: 29 Dezembro 2022
bibliography: paperCNATool.bib

# Optional fields if submitting to a AAS journal too, see this blog post:
# https://blog.joss.theoj.org/2018/12/a-new-collaboration-with-aas-publishing
aas-doi: 10.3847/xxxxx <- update this with the DOI from AAS once you know it.
aas-journal: Astrophysical Journal <- The name of the AAS journal.
---

# Summary

CNATool is an online program for analyzing complex and social networks. It was developed to allow quick and simplified analysis of network graphs from any device connected to the Internet. It supports graphs in Pajek and JSON formats, creates graphs of artificial networks, displays graphs, selects the layout algorithm and displays its properties (average degree, density, average clustering coefficient, average shortest path, diameter and efficiency). It also displays detailed properties of the vertices and saves the graph in Pajek, JSON and SVG formats, in addition to generating HTML reports.

# Introduction

The analysis of complex networks has become frequent, considering that many social, biological and technological phenomena can be represented as network diagrams (also known as Graphs), allowing not only a visual analysis of the problem, but the use of tools developed for a given application involving graph theory [1], in solving problems different from those originally thought. Pereira, Freitas and Sampaio [2], in their study on LPAs (local productive arrangements), used networks theory to study the processes of cooperation and collaboration between companies that make up an LPA of confections by analyzing the data using the Pajek software [3] [4]. Vieira et al. [5] studied collaboration processes between researchers at an important research institute, using similar techniques applying Gephi software in their analysis, also used by Casteigts et al. [6] in their research on time-varying networks (TVGs). Monteiro et al. [7] proposed a model appropriate to explain evolution of species in an affinity network, based on an evolutive algorithm that incorporates the same network properties. Ferreira et al. [8], analyzed the stock exchanges for 20 countries in a multiscale network identifying the linkages between markets. Ying et al. [9] used complex network theory to monitor coupled risks. Zhu et al. [10] applied centrality calculations to study the functional architecture of healthy individuals trying to determine their regulatory mechanism. Chang et al. [11] studied the deterioration of associative memory in individuals with mild amnesia, analyzing semantic clusters. Li et al. [12] analyzed the effect of centrality of directors on social network in charitable donations. Guo et al. [13] showed how the Chinese construction industry applies complex network analysis to study accident risks. Zhang et al. [14] proposed a model of public opinion diffusion in social networks applying the theory of scale-free networks. Krajewskiet al. [15] studied the effect of centrality in collaborative networks among criminal members of the Italian-American mafia.

Health studies have also benefited from the use of network theory and its computational tools. Bullmore and Sporns [16] studied the structure and functions of the brain using graph theory. Goulas, Schaefer and Margulies [17]. Inspired by studies on social networks, they analyzed the neural network of monkey cortex and demonstrated the important role of weak connections in the cohesion of the studied network. Hilgetag et al. [18] also studied the visual cortex of monkeys and cats using complex network analysis techniques.

These are just some applications involving the use of techniques and software developed for social and complex network analysis. Watts [19], in its review on the state of the art in complex network analysis presents other applications, highlighting economy, transportation and energy distribution.

It is in this context that we developed the CNATool software, based on the need to perform fast data analysis involving models represented as complex networks from any device connected to the Internet. This need is due to the fact that many ideas arise when we are not in front of a computer to run traditional programs in network analysis. On the other hand, researchers are often involved in the analysis and comparison of multiple networks. Analyzes of this type usually require time to be performed, involving the construction of scripts for batch processing. The tool presented here fulfills not only the need for an online network analysis program, but also the batch processing of an arbitrary number of networks, in a simple and accurate way.

Next, we will present the requirements taken into consideration for the CNATool development, its architecture and implementation.


# Problems and Background 

Newman [1] presents the main concepts involved in complex and social network analysis. The author discusses the types of networks, topologies, local and global properties. Regarding the types of networks, Newman highlights social, informational, technological and biological networks. These networks, despite having different natures, present common properties such as number of vertices, number of edges, density [20][21], average degree, average clustering coefficient [22], average shortest path [23], diameter [24] and efficiency [25]. And even at micro scale, similar parameters are observed, highlighting the clustering coefficient and the closeness [26][27][28] and betweenness [29][30][31][32] centralities. With regard to topologies, networks of apparently different natures, such as social and biological, often present phenomena common to small-world [33][34][35][36] and scale-free networks [37][38].

These similarities allow the use of the same software for the analysis of different phenomena in different study objects, as long as these phenomena and objects can be expressed as network diagrams (graphs).

This premise has led us to consolidate the main parameters used by the authors in the mental map presented in Figure 1. In this map we highlight, besides the network properties and topologies found in the literature, the main free software used in the references surveyed. In the mind map, the Tools node presents the software Gephi, Pajek, SocNetV and CNATool (the tool described in this article). For comparison purposes, we have considered the aspects accuracy, complexity of use, operating platform, and computing technology. It is clear from this graph that the three softwares are accurate, differentiating with respect to the complexity of operation, operational platform, and computing technology. In this respect it is important to stress that an increase in complexity does not represent a demerit but stems from a greater number of resources presented by the software. Likewise, a limitation regarding the operating platform does not invalidate its use but is only restricted to users of the operating systems highlighted in the graph. On the other hand, the computing technology used represents a great differential. Applications capable of using the graphics card processing cores (GPU) present superior performance, especially when processing graphs with a large number of vertices and edges. In this research, only CNATool offered this possibility. Moreover, CNATool implements some properties not found in other software, for example incidence-fidelity index [39]. Table 1 presents a summary of the main features presented by each of the analyzed programs.

CNATool's development took these aspects into consideration, prioritizing accuracy and speed, but not neglecting parameters such as usability and mobility.


# Citations

Citations to entries in paper.bib should be in
[rMarkdown](http://rmarkdown.rstudio.com/authoring_bibliographies_and_citations.html)
format.

If you want to cite a software repository URL (e.g. something on GitHub without a preferred
citation) then you can do it with the example BibTeX entry below for @fidgit.

For a quick reference, the following citation commands can be used:
- `@author:2001`  ->  "Author et al. (2001)"
- `[@author:2001]` -> "(Author et al., 2001)"
- `[@author1:2001; @author2:2001]` -> "(Author1 et al., 2001; Author2 et al., 2002)"

# Figures

Figures can be included like this:
![Caption for example figure.label{fig:example}](figure.png)
and referenced from text using autoref{fig:example}.

Figure sizes can be customized by adding an optional second parameter:
![Caption for example figure.](figure.png){ width=20% }

# Acknowledgements

We acknowledge contributions from Brigitta Sipocz, Syrtis Major, and Semyeong
Oh, and support from Kathryn Johnston during the genesis of this project.

# References
