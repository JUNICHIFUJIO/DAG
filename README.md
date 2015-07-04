# DAG
A simple Directed Acyclic Graph implementation in C++ to keep my skills from CSS 502 sharp.
--------------------------------------------------------------------------------------------------------------------------------
# CONCEPTS
A Graph is a very simple computer science concept. You have one or more nodes connected to each other by edges. Each node contains some data that is pertinent, and the connections between nodes symbolize the logical connections between the related points of data.

A directed graph signifies that a connection between two nodes has a direction. A direction signifies that there is some logical relationship between the two data points such that a property applies when considering them in a certain order, but not vice versa. In other words, the property is not reflexive.

An acyclic graph is simply a graph where starting at any given node, it is impossible to reach that node again by following edges. Naturally, an undirected graph is cyclic.

--------------------------------------------------------------------------------------------------------------------------------
# IMPLEMENTATION
Each DAG requires:
  1) Nodes
  2) Edges
  3) Some way of storing and quickly accessing a node given some data input
  4) The ability to traverse to a connected node, given a data selection criteria
  5) The ability to add nodes/edges
  6) The ability to delete nodes/edges
  7) Refusal to add nodes/edges if a cycle would occur
  8) Each node must have zero or more edges to other nodes
  9) Each edge must connect two, and only two, nodes
  10) An edge may contain a data field that defines the relationship between the two connected nodes

To address each requirement:
  1) Nodes will be defined as a structure that contains the data desired. There will be no such thing as an empty node.
  2) Edges will be defined as a simple structure referencing a "from" node and a "to" node
  3) Hashmaps are easy ways of finding nodes if given a data value to search them by.
  4) Having each node contain a hashmap of connected nodes (up to n^2 space required for n nodes)
  5) Needs any kind of dynamic collection object, not an array
  6) Needs a dynamic collection object able to shrink in size (list, vector, queue, deque)
  7) Label each node with an unsigned int "level". If a node is the root of a path, have that label equal 0. Otherwise, have it equal to the highest level of its parent node plus 1. i.e. if two nodes connect to a newly established node, where one parent node has a level of 4 and the other has a level of 8, the newly established node should have a level of 9. In this way, if any node tries to establish a connection with a node of a lower level, the potential for a cycle exists and must be refused.
