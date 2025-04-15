# Tic-Tac-Toe-Game-in-Python
# Function to print the current game board
def print_board(board):
    print(f"{board[0]} | {board[1]} | {board[2]}")
    print("--+---+--")
    print(f"{board[3]} | {board[4]} | {board[5]}")
    print("--+---+--")
    print(f"{board[6]} | {board[7]} | {board[8]}")

# Function to check if a player has won
def is_winner(board, player):
    win_conditions = [
        [0, 1, 2],  # top row
        [3, 4, 5],  # middle row
        [6, 7, 8],  # bottom row
        [0, 3, 6],  # left column
        [1, 4, 7],  # middle column
        [2, 5, 8],  # right column
        [0, 4, 8],  # diagonal (top-left to bottom-right)
        [2, 4, 6],  # diagonal (top-right to bottom-left)
    ]
    for condition in win_conditions:
        if board[condition[0]] == board[condition[1]] == board[condition[2]] == player:
            return True
    return False

# Game logic function
def tic_tac_toe_game():
    board = ['1', '2', '3', '4', '5', '6', '7', '8', '9']
    current_player = 'X'
    
    while True:
        print_board(board)
        move = get_player_input(board)
        board[move] = current_player
        
        if is_winner(board, current_player):
            print_board(board)
            print(f"Player {current_player} wins!")
            break
        
        if is_draw(board):
            print_board(board)
            print("It's a draw!")
            break
        
        current_player = 'O' if current_player == 'X' else 'X'

# Run the game
tic_tac_toe_game()
