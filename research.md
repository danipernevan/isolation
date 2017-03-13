# heuristic analysis

### 1. own moves - 2 times opponent moves   
```python
    if game.is_loser(player):
        return float("-inf")

    if game.is_winner(player):
        return float("inf")
       
    own_moves = len(game.get_legal_moves(player))
    opp_moves = len(game.get_legal_moves(game.get_opponent(player)))
    return float(own_moves - 2 * opp_moves )
``` 
```
*************************
 Evaluating: ID_Improved 
*************************

Playing Matches:
----------
  Match 1: ID_Improved vs   Random            Result: 16 to 4
  Match 2: ID_Improved vs   MM_Null           Result: 19 to 1
  Match 3: ID_Improved vs   MM_Open           Result: 7 to 13
  Match 4: ID_Improved vs MM_Improved         Result: 10 to 10
  Match 5: ID_Improved vs   AB_Null           Result: 18 to 2
  Match 6: ID_Improved vs   AB_Open           Result: 8 to 12
  Match 7: ID_Improved vs AB_Improved         Result: 10 to 10


Results:
----------
ID_Improved         62.86%

*************************
   Evaluating: Student   
*************************

Playing Matches:
----------
  Match 1:   Student   vs   Random            Result: 18 to 2
  Match 2:   Student   vs   MM_Null           Result: 16 to 4
  Match 3:   Student   vs   MM_Open           Result: 10 to 10
  Match 4:   Student   vs MM_Improved         Result: 12 to 8
  Match 5:   Student   vs   AB_Null           Result: 18 to 2
  Match 6:   Student   vs   AB_Open           Result: 11 to 9
  Match 7:   Student   vs AB_Improved         Result: 12 to 8


Results:
----------
Student             69.29%
```

### 2. own moves - 3 times opponent moves
```python
    if game.is_loser(player):
        return float("-inf")

    if game.is_winner(player):
        return float("inf")
       
    own_moves = len(game.get_legal_moves(player))
    opp_moves = len(game.get_legal_moves(game.get_opponent(player)))
    return float(own_moves - 3 * opp_moves )
``` 
```
*************************
 Evaluating: ID_Improved 
*************************

Playing Matches:
----------
  Match 1: ID_Improved vs   Random            Result: 16 to 4
  Match 2: ID_Improved vs   MM_Null           Result: 17 to 3
  Match 3: ID_Improved vs   MM_Open           Result: 9 to 11
  Match 4: ID_Improved vs MM_Improved         Result: 10 to 10
  Match 5: ID_Improved vs   AB_Null           Result: 18 to 2
  Match 6: ID_Improved vs   AB_Open           Result: 11 to 9
  Match 7: ID_Improved vs AB_Improved         Result: 10 to 10


Results:
----------
ID_Improved         65.00%

*************************
   Evaluating: Student   
*************************

Playing Matches:
----------
  Match 1:   Student   vs   Random            Result: 15 to 5
  Match 2:   Student   vs   MM_Null           Result: 15 to 5
  Match 3:   Student   vs   MM_Open           Result: 11 to 9
  Match 4:   Student   vs MM_Improved         Result: 8 to 12
  Match 5:   Student   vs   AB_Null           Result: 17 to 3
  Match 6:   Student   vs   AB_Open           Result: 9 to 11
  Match 7:   Student   vs AB_Improved         Result: 5 to 15


Results:
----------
Student             57.14%
```

### 3. own moves - 2 times opponent moves but avoid margin squares to not be trapped
```python
    if game.is_loser(player):
        return float("-inf")

    if game.is_winner(player):
        return float("inf")
       
    (x,y) = game.get_player_location(player)
    penalty_x = 2 if x in [0,6] else 0
    penalty_y = 2 if y in [0,6] else 0
    own_moves = len(game.get_legal_moves(player))
    opp_moves = len(game.get_legal_moves(game.get_opponent(player)))
    return float(own_moves - 2 * opp_moves - penalty_x - penalty_y)
``` 
```
*************************
 Evaluating: ID_Improved 
*************************

Playing Matches:
----------
  Match 1: ID_Improved vs   Random            Result: 19 to 1
  Match 2: ID_Improved vs   MM_Null           Result: 16 to 4
  Match 3: ID_Improved vs   MM_Open           Result: 8 to 12
  Match 4: ID_Improved vs MM_Improved         Result: 10 to 10
  Match 5: ID_Improved vs   AB_Null           Result: 18 to 2
  Match 6: ID_Improved vs   AB_Open           Result: 12 to 8
  Match 7: ID_Improved vs AB_Improved         Result: 10 to 10


Results:
----------
ID_Improved         66.43%

*************************
   Evaluating: Student   
*************************

Playing Matches:
----------
  Match 1:   Student   vs   Random            Result: 17 to 3
  Match 2:   Student   vs   MM_Null           Result: 16 to 4
  Match 3:   Student   vs   MM_Open           Result: 9 to 11
  Match 4:   Student   vs MM_Improved         Result: 9 to 11
  Match 5:   Student   vs   AB_Null           Result: 17 to 3
  Match 6:   Student   vs   AB_Open           Result: 10 to 10
  Match 7:   Student   vs AB_Improved         Result: 6 to 14


Results:
----------
Student             60.00%
```

I finnaly chose the first heuristic for the following reasons:
  - it is less cpu intensive and the algorithm can explore more nodes in the time amount to find the best solution
  - it beats "improved" heursistic by folowing a path to restrict opponend moves
  - it make better move choices over second heuristic by focusing on own available moves not that much as restricting oponent moves
  
