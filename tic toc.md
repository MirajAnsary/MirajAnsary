<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <title>Tic Tac Toe</title>
    <style type="text/css">
        body {
    font-family: Arial, sans-serif;
    background: rgb(63,94,251);
    background: radial-gradient(circle, rgba(63,94,251,1) 0%, rgba(252,70,107,1) 100%);
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    text-align: center;
    background: rgb(131,58,180);
background: linear-gradient(90deg, rgba(131,58,180,1) 0%, rgba(29,253,89,1) 50%, rgba(92,232,83,1) 64%, rgba(114,224,81,1) 69%, rgba(252,176,69,1) 100%);
}

h1 {
    font-size: 36px;
}

.board {
    display: grid;
    grid-template-columns: repeat(3, 100px);
    gap: 5px;
    margin-top: 20px;
}

.cell {
    width: 100px;
    height: 100px;
    background: rgb(238,174,202);
    background: radial-gradient(circle, rgba(238,174,202,1) 0%, rgba(148,180,233,1) 100%);
    border: 1px solid #ccc;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 24px;
    cursor: pointer;
}

button {
    margin-top: 20px;
    padding: 10px 20px;
    background-color: #3498db;
    color: #fff;
    border: none;
    font-size: 18px;
    cursor: pointer;
}

button:hover {
    background-color: #2980b9;
}

#result {
    font-size: 24px;
    font-weight: bold;
    margin-top: 10px;
}

    </style>
</head>
<body>
    <div class="container">
        <h1>Tic Tac Toe</h1>
        <div class="board">
            <div class="cell" onclick="makeMove(0)"></div>
            <div class="cell" onclick="makeMove(1)"></div>
            <div class="cell" onclick="makeMove(2)"></div>
            <div class="cell" onclick="makeMove(3)"></div>
            <div class="cell" onclick="makeMove(4)"></div>
            <div class="cell" onclick="makeMove(5)"></div>
            <div class="cell" onclick="makeMove(6)"></div>
            <div class="cell" onclick="makeMove(7)"></div>
            <div class="cell" onclick="makeMove(8)"></div>
        </div>
        <p id="result"></p>
        <button onclick="resetBoard()">Reset</button>
    </div>
    <script>
        let currentPlayer = 'X';
let board = ['', '', '', '', '', '', '', '', ''];
let gameActive = true;

function makeMove(cellIndex) {
    if (board[cellIndex] === '' && gameActive) {
        board[cellIndex] = currentPlayer;
        document.getElementsByClassName('cell')[cellIndex].textContent = currentPlayer;
        
        if (checkWinner(currentPlayer)) {
            document.getElementById('result').textContent = `${currentPlayer} wins!`;
            gameActive = false;
        } else if (board.every(cell => cell !== '')) {
            document.getElementById('result').textContent = "It's a draw!";
            gameActive = false;
        } else {
            currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
        }
    }
}

function checkWinner(player) {
    const winPatterns = [
        [0, 1, 2],
        [3, 4, 5],
        [6, 7, 8],
        [0, 3, 6],
        [1, 4, 7],
        [2, 5, 8],
        [0, 4, 8],
        [2, 4, 6]
    ];

    return winPatterns.some(pattern =>
        pattern.every(cellIndex => board[cellIndex] === player)
    );
}

function resetBoard() {
    currentPlayer = 'X';
    board = ['', '', '', '', '', '', '', '', ''];
    gameActive = true;
    document.getElementById('result').textContent = '';
    const cells = document.getElementsByClassName('cell');
    for (let i = 0; i < cells.length; i++) {
        cells[i].textContent = '';
    }
}

resetBoard();

    </script>
</body>
</html>
