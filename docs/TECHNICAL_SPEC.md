
# Campus Route Navigator – Technical Specification

## 1. Programming Language
Java

## 2. Architecture
The application uses a weighted, undirected graph.

- Node = College building
- Edge = Walking path
- Edge weight = Walking distance in metres

## 3. Common Java Packages

com.campusnavigator
- model
- graph
- algorithms
- ui
- visualization

## 4. Shared Classes and Interfaces

### Node.java
Represents a campus building.

Fields:
- String id
- String name
- double xMeters
- double yMeters

### Edge.java
Represents a walking connection.

Fields:
- String destinationId
- double distanceMeters

### CampusGraph.java
Stores the campus graph.

Required methods:
- addNode(Node node)
- addUndirectedEdge(String fromId, String toId, double distanceMeters)
- getNode(String id)
- getNodes()
- getNeighbors(String nodeId)

### SearchResult.java
Stores algorithm results.

Required fields:
- boolean found
- List<String> pathNodeIds
- List<String> exploredNodeIds
- double totalDistanceMeters
- long executionTimeNanos

### SearchAlgorithm.java
Common interface for all algorithms.

Method:
SearchResult findPath(
    CampusGraph graph,
    String startId,
    String goalId
);

## 5. Algorithm Implementations

### AStarSearch.java
- Use PriorityQueue.
- Use g(n) + h(n).
- Use Euclidean distance as an admissible heuristic.
- Return the optimal distance route.

### BreadthFirstSearch.java
- Use Queue.
- Explore level by level.
- Return a route with the fewest edges.

### DepthFirstSearch.java
- Use Stack or recursion.
- Explore depth first.
- Return a valid discovered route.
- Optimality is not guaranteed.

## 6. Result Comparison

All algorithms must return the same SearchResult structure.

Compare:
- Execution time
- Number of explored nodes
- Total route distance
- Final route

## 7. Important Rules

1. Do not change shared class or method names.
2. Use the exact package names.
3. All distances must be positive.
4. All algorithms must use the same CampusGraph.
5. Do not include UI code inside algorithm classes.
6. Commit code only to the assigned branch.
7. Create Pull Requests to main.
8. Test your module before submitting.

## 8. GitHub Branch Assignment

- feature/graph-map
- feature/astar
- feature/bfs
- feature/dfs
- feature/ui-visualization

Project Lead:
Integration, code review and testing.
