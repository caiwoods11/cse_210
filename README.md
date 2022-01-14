# CSE 210 : Week 2 tic_tac_toe 
## tic_tac_toe 
__Course CSE 210__
__Cai Woods__
```
import os 
os.system("cls")
import random


class Board():
    def __init__(self):
            #becasue it is realted to the object of the board 
            # cells are self and they = a list 
            # need 0 to 9 cell spaces
        self.cell = ["0","1","2","3","4","5","6","7","8","9"]

            # Make fuction to display the self object
    def display(self):
            # create the row structure and then make 3 rows - print
        print (" %s | %s | %s " %(self.cell[1], self.cell[2], self.cell[3]))
        print ("-----------")
        print (" %s | %s | %s " %(self.cell[4], self.cell[5], self.cell[6]))
        print ("-----------")
        print (" %s | %s | %s " %(self.cell[7], self.cell[8], self.cell[9]))

        # Update cell Section
        # If statement to make sure there is no X or O in cell
            # Then update cell
    def update_cell(self, cell_no, player):
        if self.cell[cell_no] <= "9":
            self.cell[cell_no] = player

        # Determine the winner yes or no
    def is_winner(self, player):
        if self.cell[1] == player and self.cell[2] == player and self.cell[3] == player:
            return True
        if self.cell[1] == player and self.cell[4] == player and self.cell[7] == player:
            return True 
        if self.cell[1] == player and self.cell[5] == player and self.cell[9] == player:
            return True
        if self.cell[2] == player and self.cell[5] == player and self.cell[8] == player:
            return True
        if self.cell[3] == player and self.cell[6] == player and self.cell[9] == player:
            return True
        if self.cell[3] == player and self.cell[5] == player and self.cell[7] == player:
            return True
        if self.cell[4] == player and self.cell[5] == player and self.cell[6] == player:
            return True
        if self.cell[7] == player and self.cell[8] == player and self.cell[9] == player:
            return True 
  
        return False
    
        # Determine if board is a tie
    def is_tie(self):
        used_cell = 0
        for cell in self.cell:
            if cell >= "9":
                used_cell += 1
        if used_cell >= 9:
            return True
        else:
            return False
        
        # Reset board after player wins
    def reset(self):
        self.cell = ["0","1","2","3","4","5","6","7","8","9"]

        # Create AI to play against. 
     #def ai_move(self,player):
            # If center is open choose center
        #if self.cell[5] == "5" and self.cell[5] != "X" and self.cell[5] != "O":
            #self.update_cell(5, player)

            # AI Can Win

            # AI Blocks

            # Coose Random
        #for i in range(1,10):
            #if self.cell[i] <= "9" and self.cell[i] >= "X" and self.cell[i] >= "O":
                #self.update_cell(i, player)
                #break

board = Board()

# create welcome message
def print_header():
    print("Welcome to Tic_Tac_Toe\n")

def refresh_screen():
    # Clear the screen
    os.system("cls")

    # Print the header
    print_header()

    # Show the board
    board.display()

# Create loop to run game

while True:
    refresh_screen()

        # Get player X input
    x_choice = int(input("\nPlayer X) PLease choose 1-9. > "))

        # Update board with player O
    board.update_cell(x_choice, "X")

        # Refresh Screen
    refresh_screen()

        # Check for X win
    if board.is_winner("X"): 
        print("\nX wins!\n")
        play_again = input("Would you like to play again? > ").capitalize()
        if play_again == "Y" or  play_again == "Yes":
            board.reset()
            continue
        else:
            break
    
       
        # Check for Tie
    if board.is_tie(): 
        print("\nTie Game!\n")
        play_again = input("Would you like to play again? > ").capitalize()
        if play_again == "Y" or  play_again == "Yes":
            board.reset()
            continue
        else:
            break

        # Get player 0 input
    o_choice = int(input("\nPlayer O) PLease choose 1-9. > "))
        #board.ai_move("O") 
    
        # Refresh Screen
    refresh_screen()


        # Update board with player O
    board.update_cell(o_choice, "O")

         # Check for O win
    if board.is_winner("O"): 
        print("\nO wins!\n")
        play_again = input("Would you like to play again? > ").capitalize()
        if play_again == "Y" or  play_again == "Yes":
            board.reset()
            continue
        else:
            break

        # Check for Tie
    if board.is_tie(): 
        print("\nTie Game!\n")
        play_again = input("Would you like to play again? > ").capitalize()
        if play_again == "Y" or  play_again == "Yes":
            board.reset()
            continue
        else:
            break

```
