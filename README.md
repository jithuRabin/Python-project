# Python-project - 1 ( xox game)
def print_board(board):
    for row in board:
        print("|".join(row))
        print("-" * 5)

def check_winner(board):
    # Check rows
    for row in board:
        if row[0] == row[1] == row[2] != " ":
            return row[0]
    for col in range(3):
        if board[0][col] == board[1][col] == board[2][col] != " ":
            return board[0][col]
    if board[0][0] == board[1][1] == board[2][2] != " ":
        return board[0][0]
    if board[0][2] == board[1][1] == board[2][0] != " ":
        return board[0][2]
    return None

def play_game():
    board = [[" " for _ in range(3)] for _ in range(3)]
    current_player = "X"
    winner = None
    while not winner:
        print_board(board)
        row = int(input("Enter the row (0-2): "))
        col = int(input("Enter the col (0-2): "))
        if board[row][col] != " ":
            print("Invalid move. Try again.")
            continue
        board[row][col] = current_player
        winner = check_winner(board)
        current_player = "O" if current_player == "X" else "X"
    print_board(board)
    print("Player", winner, "wins!")

play_game()



#Python project - 2 (Password creater)
import string
import random

length = int(input("Enter password length: "))
 
print('''Choose character set for password from these :
         1. Letters
         2. Digits 
         3. Special characters
         4. Exit''')
 
characterList = ""
 
while(True):
    choice = int(input("Pick a number "))
    if(choice == 1):
         
        # Adding letters to possible characters
        characterList += string.ascii_letters
    elif(choice == 2):
         
        # Adding digits to possible characters
        characterList += string.digits
    elif(choice == 3):
         
        # Adding special characters to possible
        # characters
        characterList += string.punctuation
    elif(choice == 4):
        break
    else:
        print("Please pick a valid option!")
 
password = []
 
for i in range(length):
   
    # Picking a random character from our
    # character list
    randomchar = random.choice(characterList)
     
    # appending a random character to password
    password.append(randomchar)
 
print("The random password is " + "".join(password))
