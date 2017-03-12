uh

```python
    if game.is_loser(player):
        return float("-inf")

    if game.is_winner(player):
        return float("inf")
       
    own_moves = len(game.get_legal_moves(player))
    opp_moves = len(game.get_legal_moves(game.get_opponent(player)))
    return float(own_moves - 3 * opp_moves )
```

