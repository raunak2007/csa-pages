---
toc: true
comments: true
layout: post
title: Java Console Game Hacks
description: NEW TOOLS CHECK
courses: { csa: {week: 1} }
type: hacks
---

::: {.cell .markdown id="2P4vPyRrX7Fz"}

------------------------------------------------------------------------

toc: true comments: true layout: post title: Java Console Game Hacks
description: NEW TOOLS CHECK courses: { csa: {week: 1} } type: hacks
\-\--
:::

::: {.cell .markdown id="24EiTWJIYfjC"}
# Notes for Tic-Tac-Toe Game Code

This markdown file provides an explanation of the key concepts and tools
used in the original Tic-Tac-Toe game code.

## Concepts and Tools Used

### 1. Static and Final Variables {#1-static-and-final-variables}

-   The `SIZE` variable is declared as
    `private static final int SIZE = 3;`.
-   `static` indicates that `SIZE` is a class-level variable and shared
    among all instances of the class.
-   `final` ensures that `SIZE` cannot be changed after its initial
    assignment.

### 2. Constructor Method {#2-constructor-method}

-   The constructor `public TicTacToeGame()` initializes the game when
    an instance of the `TicTacToeGame` class is created.
-   It uses nested loops to fill the `board` 2D array with empty cells
    (\'-\').

### 3. Conditional Statements (if-else) {#3-conditional-statements-if-else}

-   The player chooses their mark (\'X\' or \'O\') using an if-else
    statement based on user input.

### 4. Loops (for and while) {#4-loops-for-and-while}

-   `for` loops are used for iterating through rows and columns of the
    game board.
-   A `while` loop is used in the `computerTurn()` method to ensure the
    computer selects a valid move.

### 5. Objects and Object Instantiation {#5-objects-and-object-instantiation}

-   An instance of the `TicTacToeGame` class is created using
    `TicTacToeGame game = new TicTacToeGame();`.
-   This instance allows the game to be played through the `playGame()`
    method.

### 6. Arrays (2D Array) {#6-arrays-2d-array}

-   The `board` variable is a 2D array (`char[][] board`) that
    represents the Tic-Tac-Toe game board.

### 7. Methods and Functionality {#7-methods-and-functionality}

-   The code includes various methods to manage gameplay:
    `isBoardFull()`, `printBoard()`, `checkWin()`, `checkRowsForWin()`,
    `checkColumnsForWin()`, `checkDiagonalsForWin()`, `changePlayer()`,
    `computerTurn()`, `isValidMove()`, and `placeMark()`.

### 8. Random Number Generation {#8-random-number-generation}

-   The `Random` class is used to generate random numbers for the
    computer\'s move selection.

## Running the Game

-   Create an instance of the `TicTacToeGame` class:
    `TicTacToeGame game = new TicTacToeGame();`.
-   Start playing the game by calling the `playGame()` method on the
    created instance: `game.playGame();`.
:::

::: {.cell .code id="FSITo48zX7F1" outputId="6c193a54-011e-4661-fa27-936042325b8b"}
``` java
import java.util.Random;
import java.util.Scanner;

public class TicTacToeGame {
    private static final int SIZE = 3;
    private char[][] board = new char[SIZE][SIZE];
    private char playerMark, computerMark;
    private Random random = new Random();

    public TicTacToeGame() {
        for (int i = 0; i < SIZE; i++) {
            for (int j = 0; j < SIZE; j++) {
                board[i][j] = '-';
            }
        }
    }

    public boolean isBoardFull() {
        for (int i = 0; i < SIZE; i++) {
            for (int j = 0; j < SIZE; j++) {
                if (board[i][j] == '-') {
                    return false;
                }
            }
        }
        return true;
    }

    public void printBoard() {
        for (int i = 0; i < SIZE; i++) {
            for (int j = 0; j < SIZE; j++) {
                System.out.print(board[i][j] + " ");
            }
            System.out.println();
        }
    }

    public boolean checkWin() {
        return checkRowsForWin() || checkColumnsForWin() || checkDiagonalsForWin();
    }

    private boolean checkRowsForWin() {
        for (int i = 0; i < SIZE; i++) {
            if (board[i][0] == board[i][1] && board[i][1] == board[i][2] && board[i][0] != '-') {
                return true;
            }
        }
        return false;
    }

    private boolean checkColumnsForWin() {
        for (int i = 0; i < SIZE; i++) {
            if (board[0][i] == board[1][i] && board[1][i] == board[2][i] && board[0][i] != '-') {
                return true;
            }
        }
        return false;
    }

    private boolean checkDiagonalsForWin() {
        return (board[0][0] == board[1][1] && board[1][1] == board[2][2] && board[0][0] != '-') ||
               (board[0][2] == board[1][1] && board[1][1] == board[2][0] && board[0][2] != '-');
    }

    public void changePlayer() {
        playerMark = (playerMark == '❌') ? '🔴' : '❌';
        computerMark = (computerMark == '❌') ? '🔴' : '❌';
    }

    public void computerTurn() {
        int computerMove;
        while (true) {
            computerMove = random.nextInt(9) + 1;
            if (isValidMove(String.valueOf(computerMove))) {
                break;
            }
        }
        System.out.println("Computer chose " + computerMove);
        placeMark(String.valueOf(computerMove), computerMark);
    }

    public boolean isValidMove(String position) {
        switch (position) {
            case "1":
                return (board[0][0] == '-');
            case "2":
                return (board[0][1] == '-');
            case "3":
                return (board[0][2] == '-');
            case "4":
                return (board[1][0] == '-');
            case "5":
                return (board[1][1] == '-');
            case "6":
                return (board[1][2] == '-');
            case "7":
                return (board[2][0] == '-');
            case "8":
                return (board[2][1] == '-');
            case "9":
                return (board[2][2] == '-');
            default:
                return false;
        }
    }

    public void placeMark(String position, char mark) {
        switch (position) {
            case "1":
                board[0][0] = mark;
                break;
            case "2":
                board[0][1] = mark;
                break;
            case "3":
                board[0][2] = mark;
                break;
            case "4":
                board[1][0] = mark;
                break;
            case "5":
                board[1][1] = mark;
                break;
            case "6":
                board[1][2] = mark;
                break;
            case "7":
                board[2][0] = mark;
                break;
            case "8":
                board[2][1] = mark;
                break;
            case "9":
                board[2][2] = mark;
                break;
            default:
                System.out.println("Invalid position");
        }
    }

    public void playGame() {
        Scanner scan = new Scanner(System.in);
        System.out.println("Welcome to Raunak's Tic Tac Toe!");
        System.out.println("To play, enter any number from 1-9 to indicate your move!");
        printBoard();
        System.out.println("Choose your mark: ❌ or 🔴");
        playerMark = scan.nextLine().charAt(0);
        if (playerMark == '❌') {
            computerMark = '🔴';
        } else {
            computerMark = '❌';
        }

        while (true) {
            System.out.println("Enter your placement (1-9):");
            String userInput = scan.nextLine();
            if (isValidMove(userInput)) {
                placeMark(userInput, playerMark);
                printBoard();
                if (checkWin()) {
                    System.out.println("Player wins!");
                    break;
                }
                if (isBoardFull()) {
                    System.out.println("It's a tie!");
                    break;
                }
                computerTurn();
                printBoard();
                if (checkWin()) {
                    System.out.println("Computer wins!");
                    break;
                }
                if (isBoardFull()) {
                    System.out.println("It's a tie!");
                    break;
                }
            } else {
                System.out.println("Invalid position. Try again.");
            }
        }
    }
}

TicTacToeGame game = new TicTacToeGame();
game.playGame();
```

::: {.output .stream .stdout}
    Welcome to Raunak's Tic Tac Toe!
    To play, enter any number from 1-9 to indicate your move!
    - - - 
    - - - 
    - - - 
    Choose your mark: ❌ or 🔴
    Enter your placement (1-9):
    ❌ - - 
    - - - 
    - - - 
    Computer chose 4
    ❌ - - 
    🔴 - - 
    - - - 
    Enter your placement (1-9):
    Invalid position. Try again.
    Enter your placement (1-9):
    ❌ ❌ - 
    🔴 - - 
    - - - 
    Computer chose 8
    ❌ ❌ - 
    🔴 - - 
    - 🔴 - 
    Enter your placement (1-9):
    ❌ ❌ ❌ 
    🔴 - - 
    - 🔴 - 
    Player wins!
:::
:::
