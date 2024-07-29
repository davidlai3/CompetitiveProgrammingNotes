## Prerequisites
- An **impartial game** is a game where there are two players, where the only difference between them is the order in which they play
- Games under the **normal play convention** are games that end when there are no moves left for a player to make (that player loses)
- In impartial games, we don't think of game states relative to the player they belong to. We think of them as either winning or losing positions, because the player who is at that position is relative
- **Nimbers**, also called **Grundy numbers** are special numbers that tell us if a certain position in a game is winning or losing.
	- If the game is in a terminal position, a state where no moves are possible, the Grundy number is 0
	- If the position in non-terminal, the Grundy number is the minimum excludant (mex) of the Grundy numbers of the positions reachable in one move
- In games whose positions are indexed by natural numbers (like nim itself, which is indexed by its heap sizes), the sequence of Grundy numbers for successive positions of the game is called the **nim-sequence** of the game

## Overview
- The Sprague-Grundy Theorem states that every impartial game under the normal play convention is equivalent to a one-heap game of nim

## Doubts
- What exactly is a Grundy number?
- Why do we use xor for nim sums?