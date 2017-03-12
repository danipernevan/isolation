
In the chapter "Game Tree Searching by Min / Max Approximation" the author, Ronald L. Rivest, present an iterative method for searching game trees by approximating the “min” and “max” operators. The approximation determine the next leaf node to expand. The results are drawn from playing 1000 games of 'Connect-Four’ and finding that proposed scheme is superior to minmax search with alpha-beta pruning, although this scheme has more CPU overhead.

Generalized Mean Values is preffered instead of 'min' and 'max' functions because it's partial derivative is continous where 'min' and 'max' is not. Taking derivatives of the generalized mean value functions at each node and using the chain rule we can identify which node contribute most to the value of root node.

Searching the game tree for optimal moves is done by exploring the tree and pick the path that correspond to Min and Max nodes depending on whose turn it is to play. When the tree is small it can be explored completely, so optimal play is possible but most interesting games have huge trees and an heursistic approximation is needed that minimax search with alpha-beta pruning may produce optimal play even though only a small fraction of the game tree is explored. The author in this chapter is presenting an optimized heuristic.

This method use a "penalty" weight for the cost to descend one level, that bad moves are penalized more that good moves. The "penalty" is defined as the sum of the penalties of all the edges between current node and the root. The next expanded node is the node with the smallest penalty.
   
- Searching by min/max approximation
- Implementation
- Experimental Results
- The game: Connect-Four 
 - The static evaluator
 - Resource bounds 
 - Minimax search with alpha-beta pruning
 - Penalty-based heuristic 
 - Results
TABLE 2. Experimental results
Resource bound per turn MM wins AB wins Ties
1 second 41 46 1 l
2 second 40 42 16
3 seconds 36 44 18
4 seconds 39 52 7
5 seconds 30 55 13
Total 186 239 65
1000 moves 47 35 16
2000 moves 50 35 13
3000 moves 42 47 9
4000 moves 49 42 7
5000 moves 61 31 6
Total 249 190 51 

 - Discussion
 - Open problems
 - Conclusion 
