# Dynamics-of-Complex-Networks-and-Systems
Notes from Graph Theory course plus some code

Eulerian Circuit 
    
    visit every edge only once
    solvable in O(|E|)
    (nodes may be repeated)

Hamiltonian Cycle

    visit every node only once
    NP-Hard

Cocitation
    
    Build a network (undirected) that captures the similarity of connectivity in the original(directed) graph
    ex. Nodes i and j are simliar because there are "many" nodes that point to both of them

Tree

    A tree is a connected, undiected network with no cycles.
    Forest is a network made up of a collection of trees

Path

    [A]ij nonzero if there exists a r-length path from j to i

Eigenvector Centrality

    Degree assigns importance equally in terms of the # of neighbors
    eigenvector centrality assigns importance proportional to the importance of the node's neighbor

Katz Centrality(add more info about)

    x(t+1) = alpha*A*x(t) + Beta*onevector

PageRank Centrality(Google)

    "Exploring conservation of centrality"

Erdos Renyi Random Graph

    G(n, p) - n = # nodes, p = probability to connect any pair of nodes, p percent from 0 to 1 inclusive
    1. Add n nodes
    2. For each (unique) pair i, j flip a biased coin:
        
        i. Heads has probability p => create an edge between i->j
        ii. Trails has probability 1 - p => do not create an edge
    P(m) = probability of generating a graph with m edges
    P(m) = (m m)p^{m}*(1-p)^{M-m} where M is total number of edges
    Binomial Distribution - distribution that captures the number of "successes" in a sequence of idepenedent trials

Configuration Model

    Adapt the idea of radom graphs to mimic realistic degree distributino
    Still maintina some of the analytic tractability of the Erdos-Renyi random network
    Takes as input the desired degree sequence
    1. Degree sequence {ki}^n
    2. Add n nodes and give the ith node ki "stubs" of edges
    3. Pick two stubs uniformily randomly and connect them as an edge
    Like in ER the uniform probability is the property that provides analytic tractability
    Node that the # of stubs must be even, ie ki such that summation of ki si equal to 2m.

Friendship Paradox

    observation that friends of indivuals tend to have more firends than the indivual themselves

Barabasi-Albert Model

    BA(n, q)
    Initialization: start with a clique of q nodes(q(q-1)/2 edges)
    clique is group of nodes that are completely connected to each other
    At each "time" step: 
        * add a new node vt with q connections made to existing nodes
        * edge between vt and vi with probability ki/(summation of kj from j = 0 to t-1)-Preferential Attachment
    Means nodes with high degree more likely to receive edge from new node
    Prefferential attachment("rich get richer") is a model of network formation that leads to scale-free degree behavior

Local Attachment

    LA(n, q, qr) st qr less than equal to q nd Inherently directed
    Initialization: start with a clque of q + 1 nodes
    At each "time" step: 
        * Add qr edges randomly with uniform probability
        * Add q - qr edges randomly(uniformly) to the outbound neighbors of the nodes connected to in 1
    Local attachment is also a mechanism that leads to scale free degree distribution
    can exhibit high clustering

Vertex Copying

    another(biologically inspired) model that can generate scale free degree distribution
    DD(n, p)
    Initialization: begin with 2 connected nodes
    At each "time" step: 
        * randomly(uniformly) select a node and duplicate it
        * Retain the orignal edges with probaility p (if no edges are retained, discard and redo)


Regular Netwoks

    all nodes have the same degree
    used in applications like game theory

Small World Netowrks

    SW(n, q, p) such that q much be even
    1. place nodes in a ring and connect each node to q/2 nodes to its left and right
    2. randomly (uniformly) connect nodes with probaility p
    Combines clustering(regular networks) with short average paths(random graph)

Percolation

    node(site) percolation - removing the fraction of nodes in a network (and the adjacent edges)
    edge (bond) percolation - removing a fraction fo the eges in a network
    Removable can represent failure/destruction/death
    Removal isn't always a bad thing: vaccination "removes" people from a contingent network

Occupation probability

    if prob = 1: no nodes reomved, "occupied" nodes are functional
    if prob = 0: all nodes removed
    as pro = 1 -> prob = 0, there is a percolation threshold at which a giant component(giant cluster) dissovles
    ex. For disease spread, when above percolation threshold that means an epidemic and while below that means disease is confined to small sections of population
    ex. For internet, when above percolation threshold then most nodes can communicate and when below that means cannot reach all nodes
    Percolation can be random(mimicing failure) or can be strategic, eg. by degree(mimicing attacks)
    The configuration model captures most of the major percolation properties in an analytic framework
    
Cascading Failures

    A single failure can lead to successive failures
    often linked to capcaities-max flow
    Use max flow min cut thm along with edmond karp thm
    ex. power grids, biochemical cascades, finance(systemic risks), traffic,,,

