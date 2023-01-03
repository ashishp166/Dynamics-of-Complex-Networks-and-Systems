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

Barabasi-Albert Model

    BA(n, q)
    Initialization: start with a clique of q nodes(q(q-1)/2 edges)
    At each "time" step: 
        add a new node vt with q connections made to existing nodes
        edge between vt and vi with probability ki/(summation of kj from j = 0 to t-1)-Preferential Attachment
    Prefferential attachment is a model of network fomration that leads to scale-free degree behavior
    

