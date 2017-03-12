
In the chapter **"Game Tree Searching by Min / Max Approximation"** the author, Ronald L. Rivest, present an iterative method for searching game trees by approximating the “min” and “max” operators. The approximation determine the next leaf node to expand. The results are drawn from playing 1000 games of 'Connect-Four’ and finding that proposed scheme is superior to minmax search with alpha-beta pruning, although this scheme has more CPU overhead.

Generalized Mean Values is preferred instead of 'min' and 'max' functions because it's partial derivative is continuous where 'min' and 'max' function is not. Taking derivatives of the generalized mean value functions at each node and using the chain rule he can identify which node contribute most to the value of root node.

Searching the game tree for optimal moves is done by exploring the tree and pick the path that correspond to Min and Max nodes depending on whose turn it is to play. When the tree is small it can be explored completely, so optimal play is possible, but most interesting games have huge game trees and an heuristic approximation is needed that minimax search with alpha-beta pruning may produce optimal play even though only a small fraction of the game tree is explored. The author is presenting an optimized heuristic.

This method use a "penalty" weight for the cost to descend one level. Bad moves are penalized more that good moves. The "penalty" is defined as the sum of the penalties of all the edges between current node and the root. The next expanded node is the node with the smallest penalty.

The "min/max approximation" heuristic is special case of the penalty-based search method, where the penalties are defined in terms of the derivatives of the approximating functions. When p (from generalized mean formula) gets large, the heuristic should grow very deep but narrow trees and for small p, the heuristic should grow broad trees. 

This heuristic is very cpu intensive but when computing the generalized means exactly, the play is improved. The benefits of min-max approximations can be seen from example that M<sub>10</sub>(35, 40) > M<sub>10</sub>(30, 40) although max(35, 40) = max(30, 40). The
min/max approximation pays attention to good backup or secondary moves.

The author conducted experiments consisting of 98 games with different bounds, limited time bound and limited moves bound. When the time was limited, Alpha-Beta was superior, but when number of moves was limited, min/max approximation was superior. With the time bound, alpha-beta considered three times more distinct positions in the same amount of time. When the move operator is expensive to implement, the move-based comparison would be more relevant.

In conclusion the author says that this heuristic outplays alpha-beta with iterative deepening, when both schemes are restricted to the same number of calls to the move operator.
