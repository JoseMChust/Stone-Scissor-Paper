# Stone-Scissor-Paper

from random import randint
import numpy as np

victoryPlayer = 0
victoryMachine = 0
ties = 0



file1 = open("YOUR DIRECTORY","r")

# INSTEAD OF SEVERAL CONDITIONS, LET'S USE A RESULTS MATRIX,  T IS FOR TIE, W IS FOR PLAYER WIN, L IS FOR PLAYER LOSS
resolution = np.array((["T", "L", "W"], ["W", "T", "L"], ["L", "W", "T"]))

# THE CHOICES ARE IN A LIST, SO THE PLAYER AND THE MACHINE CHOOSE THE POSITION OF THEIR ANSWER IN THIS LIST
options = ["Stone", "Paper", "Scissors"]


# THE FILE WITH THE PLAYER CHOICES
fileRounds = open("YOUR DIRECTOTY FOR THE NEW FILE", "a")


# THESE ARE THE FUNCTIONS TO DISPLAY THE RESULTS
def rounds(winner):

    fileRounds.write("At the round {},{}\n".format(totalLines, winner))


def finalResults ():
    print("The final results are:"
            "\n The player has got {} victories"
            "\n The machines has got {} victories"
            "\n There have been {} ties".format(victoryPlayer, victoryMachine, ties))

    fileRounds.write("\n \n "
            "\nThe final results are:"
            "\n The player has got {} victories"
            "\n La maquina tiene {} victorias"
            "\n There have been {} ties".format(victoryPlayer, victoryMachine, ties))

'''
IT COUNTS THE TOTAL AMOUNT OF PLAYER CHOICES IN THE FILE AND DETERMINES HOW MANY ROUND THERE WILL BE.

IT READS EACH LINE AS A NUMBER FOR THE MATRIX ROW POSITION, THE MACHINE PICKS A RANDOM NUMBER FROM 0 T 2 AND IT OCCURS THE SAME

THEN, WITH BOTH RESPONSES CHECK THE VALUE OF THE POSITION IN THE MATRIX AND FALLS INTO A CERTAIN CONDITION

WITH EVERY GAME, THE VICTORY COUNTER ARE UPDATED UNTIL THE LOOP IS DONE

'''

totalLines = 0
i =0

for i in file1:
    totalLines +=1
    player = int(i)

    playerOption = options[player]

    machineAI = randint(0, 2)
    machineChoice = options[machineAI]

    print("The player chose {}".format(playerOption))
    print ("The machine chose {}".format(machineChoice))

    if resolution[player, machineAI] == "W":
        print("Player wins")
        victoryPlayer += 1
        rounds(winner="has won this round")

    elif resolution[player, machineAI] == "L":
        print("Machine wins")
        victoryMachine += 1
        rounds(winner="has won this round")

    else:
        print ("TIE")
        ties +=1
        rounds(winner="there has been a tie")

# IT'S TIME TO DISPLAY THE RESULTS!

finalResults()

file1.close()

fileRounds.close()
