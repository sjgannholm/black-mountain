# welcome to black-mountain

## title: Visualizing Black Mountain Writers

## description:
This is a final project for INFO-664 that uses Wikidata to generate data visualizations in the NetworkX library. It represents the pilot stage of a linked data project mapping relationships between individuals associated with Black Mountain College, an experimental arts college in North Carolina that ran from 1933-1957. This early phase culled a specific slice of the dataset — faculty and alumni identified as writers — for small-scale network visualization prototyping. The use of linked data to visualize creative networks is inspired by projects at the Semantic Lab at Pratt Institute, particularly Linked Jazz, an ongoing fifteen-year project that represents the rich relationships that define the jazz community.

## rationale:
Black Mountain College and the lives and careers of its faculty and alumni are largely well-documented, and extensive efforts have been made toward the preservation of its memory. I was surprised that no tools exist that visualize the many complex and generative relationships that formed between practitioners of many disciplines. This project is an attempt to shed light on these relationships, and to make visible the intangible and collaborative environment that shaped midcentury experimental art and writing.

## workflow:
1. Scraped names of faculty and alumni of Black Mountain College as .csv file using **Wikidata Query Service** (https://query.wikidata.org/)
2. Used **OpenRefine** to clean both datasets and Reconcile each name
3. Added columns from reconciled values to pull in information from Wikidata including "occupation", "employer", and "educated at", then faceted occupation column to show each record containing "writer"
4. Imported **NetworkX** library from **matplotlib** into **JupyterLab** and created nodes and edges to represent basic relationships between individuals, Black Mountain College, and the occupation attribute of "writer".
5. Generated a visualization in **NetworkX** and adjusted the spacing, colors, and other visual elements to create a useful and appealing network graph.

## further uses:
This project constitutes an early foray into mapping networks that emerged at Black Mountain College using linked data. This assignment's parameters limited the scope of the dataset to Wikidata, which encodes formalized and established attributes and relationships about public individuals. In pursuit of mapping the highly dynamic, nuanced, and interdisciplinary associations sparked at Black Mountain College, more rigorous research into primary and secondary sources, including correspondences, diaries, and oral histories, is needed.

## files list:
- BMC_alumni_wikidata.csv
- BMC_faculty_wikidata.csv
- BMC_alumni_refined.csv
- BMC_faculty_refined.csv
- networkx_bmw_visualization.ipynb
