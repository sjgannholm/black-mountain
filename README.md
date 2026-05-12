# welcome to black-mountain project

## title: Visualizing Black Mountain College

## description:
This is a final project for INFO-664 that uses Wikidata to generate data visualizations in the NetworkX library. It represents the pilot stage of a linked data project mapping relationships between individuals associated with Black Mountain College, an experimental liberal arts college in North Carolina in operation from 1933-1957. The first phase of this pilot arranged faculty and alumni data in a simple radial network graph to represent total known individuals involved with the college. The second phase culled a secondary dataset of writers included in *Black Mountain College: An Anthology* (2019) and plotted their collaborations with artists of other mediums, as mentioned in the anthology's introduction, in excerpts of their own work, and through my own recent research into the Merce Cunningham Video Archive held in New York Public Library's Digital Collections.
The use of linked data to visualize creative networks is inspired by projects at the Semantic Lab at Pratt Institute, particularly Linked Jazz, an ongoing fifteen-year project representing the rich relationships that define the jazz community.

## rationale:
Black Mountain College and the lives and careers of its faculty and alumni are largely well-documented, and extensive efforts have been made toward preserving its legacy. I was surprised that no tools exist that visualize the many complex and generative relationships that formed between practitioners of many disciplines. This project is an attempt to shed light on these relationships, and to make visible the intangible and collaborative environment that shaped midcentury experimental art and writing.

## cleaned workflow:

### GRAPH 1: Individuals connected to Black Mountain College
1. Scraped names of faculty and alumni of Black Mountain College as .csv file using **Wikidata Query Service** (https://query.wikidata.org/)
2. Used **OpenRefine** to clean both datasets and Reconcile each name, creating BMC_alumni_refined.csv and BMC_faculty_refined.csv
3. Combined the refined alumni and faculty datasets after reading **NetworkX** documentation and used it to create two new .csv files, one for NODES (bmc_nodes.csv) and one for EDGES (bmc_edges_2tuple.csv). The NODES .csv file had to be structured as a dictionary ("ID":"label"), while the EDGES .csv file had to be structured as a two- or three-tuple ("source", "target")
4. Read both .csv files as dataframes in **jupyter-lab** using the **pandas** library, then saved the NODES df to .json (bmc_nodes.json) and the EDGES df to a tuple format (edges_tuple)
5. Imported **NetworkX** and created an empty graph object (G = nx.Graph()), then added NODES and EDGES (see documentation). *It turned out that the graph could be plotted from just the EDGES dataframe, which resulted in fewer bugs, so EDGES were commented out for the sake of simplifying this project. The metadata contained in the EDGES dataframe will become necessary in a later iteration, so was kept.*
6. Plotted the graph using the **NetworkX** spring_layout, adding optional parameters from the library's documentation including labels, a title, and adjustments to the figure size

<img width="1570" height="1580" alt="spring_layout: Individuals connected to Black Mountain College" src="https://github.com/user-attachments/assets/b69ca4fb-5154-45e0-8a2f-80149141853e" />


### GRAPH 2: Black Mountain Writers and Collaborators
7. Created a new EDGES file (bmc_writers_edges-2tuple.csv) with connections discovered in "Black Mountain Poems" anthology (2019)
8. Read bmc_writers_edges-2tuple.csv file as dataframe, then saved as tuples
9. Created new graph entity (G2) and added writers-edges-tuple
10. Plotted graph using kamada_kawai_layout, adjusting **kwargs for readability

<img width="660" height="499" alt="kamanda_kawai_layout: Black Mountain Writers and Collaborators" src="https://github.com/user-attachments/assets/744aaf6b-786d-4336-b148-9b9deb1c9306" />


## further uses:
This assignment's parameters limited the scope of the dataset to Wikidata, which encodes formalized and established attributes and relationships about public individuals. In pursuit of mapping the highly dynamic, nuanced, and interdisciplinary associations sparked at Black Mountain College, more rigorous research into primary and secondary sources, including correspondences, diaries, and oral histories, is needed. Next steps will involve adding node and edge labels to further encode identities and relationships; introducing interactive elements to facilitate searching; and conducting further research.

## files list:
- BMC_alumni_wikidata.csv
- BMC_faculty_wikidata.csv
- BMC_alumni_refined.csv
- BMC_faculty_refined.csv
- bmc_nodes.csv
- bmc_edges_2tuple.csv
- bmc_nodes.json
- bmc_writers_edges_2tuple.csv
- project_bmc_pandas-networkx-workflow.ipynb

## references
- (2019). *Black Mountain Poems: An Anthology* (J. Creasy, Ed.) New Directions Publishing Corporation.
