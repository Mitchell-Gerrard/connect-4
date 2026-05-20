# Connect N — Configurable Connect 4 in Python
 
A terminal-based Connect 4 engine built in Python, written as a first-year university project. Supports variable board sizes, multiple human and AI players, and a configurable win condition (not just 4 in a row).
 
---
 
## Features
 
- **Configurable board** — set any grid size and choose how many in a row to win
- **Human vs AI, Human vs Human, or AI vs AI** — up to 7 players total
- **Minimax AI with alpha-beta pruning** — searches the game tree and prunes branches that can't affect the result, keeping the AI competitive without brute-forcing every possibility
- **Numba JIT compilation** — the core minimax and board evaluation functions are decorated with `@njit` via [Numba](https://numba.pydata.org/), significantly speeding up the AI's lookahead
- **Adjustable difficulty** — search depth scales with the number of players; five difficulty levels from Easy to Impossible
- **Matplotlib visualisation** — the board state is plotted after every move with colour-coded players and a winning line highlight
---
 
## How it works
 
The AI uses the **minimax algorithm** with **alpha-beta pruning**:
 
- Minimax explores possible future moves to a given depth, assuming the AI plays optimally and the opponent does too
- Alpha-beta pruning cuts off branches of the search tree that can't possibly improve the result, making the search significantly faster
- A heuristic scoring function evaluates non-terminal board states by rewarding partial sequences of the AI's pieces and penalising the opponent's
The hot path (minimax, win detection, board updates) is compiled to native machine code at runtime using Numba's `@njit` decorator, which avoids Python's interpreter overhead in the most computationally expensive parts of the code.
 
---
 
## Requirements
 
```
python >= 3.7
numpy
matplotlib
numba
```
 
Install dependencies:
 
```bash
pip install numpy matplotlib numba
```
 
---
 
## Usage
 
```bash
python connetc4.py
```
 
You'll be prompted to configure:
 
1. **Win condition** — how many in a row to win (e.g. 4 for classic Connect 4)
2. **Board size** — number of rows and columns (classic is 6×7)
3. **Number of human players**
4. **Number of AI players**
5. **Difficulty** — affects how deep the AI searches
---
 
## Project context
 
Written in 2020 as a first-year university project. The goal was to implement a working adversarial game AI from scratch and explore ways to make it run faster — which led to picking up Numba for JIT compilation.
