### heuristic analysis

1. own moves - 2 times opponent moves 
```python
    if game.is_loser(player):
        return float("-inf")

    if game.is_winner(player):
        return float("inf")
       
    own_moves = len(game.get_legal_moves(player))
    opp_moves = len(game.get_legal_moves(game.get_opponent(player)))
    return float(own_moves - 2 * opp_moves )
``` 
![first heuristic](/img/score.jpg#right)

2. own moves - 3 times opponent moves
```python
    if game.is_loser(player):
        return float("-inf")

    if game.is_winner(player):
        return float("inf")
       
    own_moves = len(game.get_legal_moves(player))
    opp_moves = len(game.get_legal_moves(game.get_opponent(player)))
    return float(own_moves - 3 * opp_moves )
``` 
![first heuristic](/img/3times.jpg#right)

3. own moves - 2 times opponent moves but avoid margin squares to not be trapped
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
![first heuristic](/img/avoid.jpg#right)


