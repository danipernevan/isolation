#### Air Cargo Problem 1
| Algorithm | Expansions | Goal Tests | New nodes | Exec. time |
| ------ | ------ | ------ | ------ | ------ |
|breadth_first_search| 43 | 56 | 180 |  0.047907 |
|breadth_first_tree_search|1458 | 1459 | 5960 | 1.425874 |
|depth_first_graph_search | 12 |13|48 |  0.012796 |
|depth_limited_search | 101 | 271 | 414 | 0.147167 |
|uniform_cost_search | 55 | 57 | 224 | 0.059183 |
|recursive_best_first_search with h_1 | 4229|4230|17029|4.214284|
|greedy_best_first_graph_search with h_1 | 7| 9| 28 | 0.008175 |
|astar_search with h_1 |  55| 57| 224 | 0.060421 |
|astar_search with h_ignore_preconditions | 41 |43|170|0.047280|
|astar_search with h_pg_levelsum | 41 |43 | 170 | 4.259263 |

Air cargo problem 1 is best solved by depth_first_graph_search with best time and fewer node expansions beside greedy_best_first_graph_search with h_1. A greedy approach is not optimal.
Action plan length 12: Fly(P1, SFO, JFK)	Fly(P2, JFK, SFO)	Load(C1, P2, SFO)	Fly(P2, SFO, JFK)	Fly(P1, JFK, SFO)	Unload(C1, P2, JFK)	Fly(P2, JFK, SFO)	Fly(P1, SFO, JFK)	Load(C2, P1, JFK)	Fly(P2, SFO, JFK)	Fly(P1, JFK, SFO)	Unload(C2, P1, SFO)

#### Air Cargo Problem 2
| Algorithm | Expansions | Goal Tests | New nodes | Exec. time |
| ------ | ------ | ------ | ------ | ------ |
|breadth_first_search| 3343 | 4609 | 30509 |  18.510304 |
|breadth_first_tree_search|||| >10 min |
|depth_first_graph_search |582|583|5211 | 4.139676 |
|depth_limited_search |||| >10 min |
|uniform_cost_search | 4852 |4854 |44030 | 65.056449 |
|recursive_best_first_search with h_1 |||| >10 min |
|greedy_best_first_graph_search with h_1 |  990|992|8910 | 10.295505 |
|astar_search with h_1 | 4852|4854|44030 | 66.349751 |
|astar_search with h_ignore_preconditions |1506|1508|13820 |18.112600|
|astar_search with h_pg_levelsum |||| >10 min |

Air cargo problem 2 is best solved by h_ignore_preconditions even if it takes longer, it has an optimal action plan. Plan length = 9: Load(C3, P3, ATL)	Fly(P3, ATL, SFO)	Unload(C3, P3, SFO)	Load(C2, P2, JFK)	Fly(P2, JFK, SFO)	Unload(C2, P2, SFO)	Load(C1, P1, SFO)	Fly(P1, SFO, JFK)	Unload(C1, P1, JFK)

#### Air Cargo Problem 3
| Algorithm | Expansions | Goal Tests | New nodes | Exec. time |
| ------ | ------ | ------ | ------ | ------ |
|breadth_first_search|16437|22627|156038 | 209.801065 |
|breadth_first_tree_search|||| >10 min |
|depth_first_graph_search |1277|1278|11497|15.933575|
|depth_limited_search |||| >10 min |
|uniform_cost_search |||| >10 min |
|recursive_best_first_search with h_1 |||| >10 min |
|greedy_best_first_graph_search with h_1 |||| >10 min |
|astar_search with h_1 |||| >10 min |
|astar_search with h_ignore_preconditions |5513|5515|51078|145.248961|
|astar_search with h_pg_levelsum |3147|3149|28865|8281.490298|

Air cargo problem 3 is best solved by h_ignore_preconditions.
Action Plan length 12 :Load(C2, P2, JFK)	Fly(P2, JFK, ORD)	Load(C4, P2, ORD)	Fly(P2, ORD, SFO)	Unload(C4, P2, SFO)	Load(C1, P1, SFO)	Fly(P1, SFO, ATL)	Load(C3,P1, ATL)	Fly(P1, ATL, JFK)	Unload(C3, P1, JFK)	Unload(C2, P2, SFO)	Unload(C1, P1, JFK)

![](https://raw.githubusercontent.com/danipernevan/isolation/master/img/planning_chart.png)

"ignore preconditions heuristic drops all preconditions from actions. Every action becomes applicable in every state, and any single goal fluent can be achieved in one step (if there is an applicable action — if not, the problem is impossible). This almost implies that the number of steps required to solve the relaxed problem is the number of unsatisfied goals—almost but not quite, because (1) some action may achieve multiple goals and (2) some actions may undo the effects of others. For many problems an accurate heuristic is obtained by considering (1) and ignoring (2). First, we relax the actions by removing all preconditions and all effects except those that are literals in the goal. Then, we count the minimum number of actions required such that the union of those actions' effects satisfies the goal" (Russell&Norvig 2003)

astar_search with h_ignore_preconditions performs better than astar_search with h_pg_levelsum because computing first heuristic is much more cost effective.





