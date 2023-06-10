# dynamic-ARG-viz
Draft repo for creating graph-like representations of succinct tree sequences, with user interaction

The idea would be the ability to create graph-like plots e.g. below
([code](https://github.com/jeromekelleher/sc2ts/blob/c6180696b7dd51a46689b9f7fa2ebd9efceec626/sc2ts/utils.py#L1457)
in the sc2ts repo). The options to the `plot_subgraph` function give some idea of the flexibility required (e.g. plotting mutations on edges, node IDs, etc)

Ideally, the end result would be an interactive plot within a Jupyter notebook. The user should be able to specify a tree sequence and a specified start node or nodes.

A suggested approach is that the code
1. converts the tree sequence to networkx form
2. calls graphviz (via pygraphviz or (better) pydot) to obtain an initial layout
3. Uses the graphviz positions to layout out the points and edges using javascript/d3js.

One optional constraint should be to set the Y position of the notes to actual time (or log time), rather than the default "rank"  The resulting plot should be interactive, allowing the user to drag points around (optionally constrained so that the y-position does not change), and to click at the end of unexpanded (dotted) branches to add more nodes to the plot (or select an existing node to remove it). The ability to use a d3js "force model" to re-layout any new graph would be very useful.

An additional useful ability would be to output the positions to a file, so that the plot can be recreated. Similarly reading in initial positions from a file would be useful.

![false_positive_top2_nxcld_large_graph](https://github.com/hyanwong/dynamic-ARG-viz/assets/4699014/06eb6f9e-0b7d-45fc-8ad4-879be2fa756c)
