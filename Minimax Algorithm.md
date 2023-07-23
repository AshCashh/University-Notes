#cs
Minimax (sometimes referred as Minimax, MM or saddle point) is a kind of backtracking [[Algorithm]] that is used in decision making and game theory to find the optimal move for a player, assuming that your opponent also plays optimally.

It's formal definition is:
$$ \underline{v_i}=max\space min\space v_i(a_i,a_{-i})$$
where: 
- $i$ is the index of the player $i$
- $-i$ denotes all other players 
- $a_i$ is the action taken by the player $i$
- $a_{-i}$ denotes the actions taken by all other players
- $v_i$ is the value function of player $i$

Calculating the maximin value of a player is done in a worst-case approach: for each possible action of the player $i$, we check all possible actions of the other players and determine the worst possible combination of actions (the one that gives player $i$ the smallest value). Then, we determine which action player $i$ can take in order to make sure that his smallest value is the highest possible.

# In Zero-Sum Games
The algorithm is commonly used in two player [[Zero-Sum Game|Zero-Sum Games]] games such as Tic-Tac-Toe, Backgammon, [[Chess]], etc. 

Where the two players are called maximiser and minimiser. The maximiser tries to get the highest score possible while the minimiser tries to do the opposite and get the lowest score possible. Every board state has a value associated with it. In a given state if the maximiser has the upper hand then, the score of the board will tend to be some positive value. If the minimiser has the upper hand in that board state then it will tend to be some negative value. In chess this is known as the evaluation bar.