# Stone-Scissor-Paper
As a journey into coding and data science, I want to develop some basic AI to play against

The used IDE is PyCharm

The logic behind: instead of creating several conditions, I created a matrix with the results of the iteration:

                          machine
                   _______________________
                   _Stone__Paper__Scissors__
        ¦ Stone   ¦  T     ¦   L  ¦    W    ¦
player  ¦Paper    ¦  W     ¦   T  ¦    L    ¦
        ¦Scissors ¦  L     ¦   W  ¦    T    ¦

"W" , player wins

"L" , machine wins

"T", there is a tie

This branches uses a txt fullfilled by the player with the choices typed from 0 to 2, as it checks a list and each choice provides the axis 0 for the matrix.

Then, with the module random the machine select a number from 0 to 2 and checks the same list and each choice provides the axis 1 for the matrix.
