# HalmaGame
The Halma gameboard is defined by a 16 times 16
checkerboard. The game can be played by two or four
players, starting in opponent corners. When played by two
players, each player is equipped with 19 pieces, which can
be colored stones, wooden ponds or small checkers. For
simplicity, Halma is used as a reference for the game with
two players. The object of the game is to move all of your
pieces to the target area first, which is your opponent’s
starting position.
![image](/Images/Halma_bw.png "Halma Board")

The game starts by randomly selecting a player to make the
first move. All pieces can move in eight different directions
(orthogonally and diagonally). The easiest move for a piece is to move it to one of the adjacent free spaces, resulting in
terminating the move. More complex moves include jumping
over adjacent pieces of any color as long as a free square
is available on the direct opposite side. The same piece can
be used to make more jumps or the turn is ended. Once a
piece is in the goal area it can move within the goal area but
not outside of it. In Halma pieces cannot be captured as in
other board games like Chess. The simplicity of the game
makes Halma suitable for beginners as well as advanced
strategists.

![image](/Images/Halma_ove.png "Halma Board")

## How to interact with the game

To create a game you need to first define your 2 Agents that will be playing. You can do this by stating which execute_move_function you want to use:

- execute_random_move
- execute_human_move
- execute_move (which has the parameters the evaluation function you want to use and the depth of search for each iteration)

An example of a game instance would be:

```
game = ConnectHalmaGame(execute_random_move, execute_move(evaluation_function_1, 2))
```

After you have the game instance defined what you need to do is specify how many matches you want to run, the maximum time for each game and if you want the board states to be printed at each movement or not.

An example of a run match would be:

```
game.run_n_matches(6, 300, False)
```

Where the output of matches will state which player won each match, how many victories and draws there were and the total time used to compute the result.

Result would be similar to:
```
End of game! Player 2 wins!
End of game! Player 2 wins!
End of game! Player 2 wins!
End of game! Player 2 wins!
End of game! Player 2 wins!
End of game! Player 2 wins!

=== Elapsed time: 19 seconds ===
  Player 1: 0 victories
  Player 2: 6 victories
  Draws: 0 
===============================
```

In order to interact with the game you need to call the execute_human_move function as one of the arguments of the ConnectHalmaGame:

```
game = ConnectHalmaGame(execute_human_move, execute_move(evaluation_function_1, 2))
```

For each iteration you will have two different inputs:

- An index input that consists on the index of the piece we
want to perform the move on. This move index should
be written in the form of: `1,1` ; `0,0` ; `2,1` etc...
- The name of the move we want to perform on the selected
piece. This name should follow the given structure: `up`,
`down left`, `jump down`, `jump up right`, etc...

It should be also considered the fact that consecutive jumps
may be available and for that case, after a jump is made, there
will show an option input asking if the player wants to perform
a consecutive jump or not (options: `yes`, `no`) and if the player
types `yes` it will show then another input for the name of
the move he wants to perform on that piece.

After performing a consecutive jump the prompt will always ask you if you want to do another jump because there is always a possibility that you stay in an infinite loop jumping
so when you are done with your move just type `no` when he asks if you want to do another jump.




(We advise you to play against execute_move(evaluation_function_1, 1) since he is the best performing agent so far) 

Have fun :smile:
