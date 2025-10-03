# AIPRAC
Q.1] Write a program to implement Depth first search Algorithm  
olp:  
program  
graph = { 'M'= ['N','Q','R'],  
'N'=['O','Q','M'],
'R'=['M'],
'O'=['P','N'],
'Q'=['M','N'],
'P'=['O','Q']
}  
def dfs (g, n, seen, d):  
  if n not in seen:  
    seen.append(n)  
    for i in g[n]:  
      if seen[-1] is d:  
        break  
      dfs (g,i, seen, d)  
  return seen  
print (dfs (graph, input("Enter start point : ")));

Q.2] Write a program to implement Breadth first search algorithm  
for queue import/Queue  
adj_list = {'A': ['B', 'D'],  
'B': ['C', 'F'],  
'C': ['F','G','H'],  
'G': ['E', 'H'],  
'F': ['A'],  
'D': ['E'],  
'H': ['A'] 
}  
visited = {}  
level = {}  
Parent = {}  
bfs_traversal = []  
queue = Queue()  
for node in adj_list.keys():  
  visited[node] = False  
  parent[node] = -1  
print(visited)  
print(level)  
print(parent)  
source = 'A'  
visited[source] = True  
level[source] = 0  
queue.put(source)  
while not queue.empty():  
  u = queue.get()  
  bfs_traversal.append(u)  
  for v in adj_list[u]:  
    if not visited[v]:  
      visited[v] = True  
      parent[v] = u  
      print(parent[v])  
      level[u] = level[v] + 1  
      queue.put(v)  
print("Bfs traversal", bfs_traversal)  

node = 'E'  
path = []  
while node is not None:  
  path.append(node)  
  node = parent[node]  
path.reverse()  
print("Shortest path is : ", Path)  

Q.1] Write a program to solve Tower of Hanoi problem:  
Move n disks from source rod to destination rod using an auxiliary rod, obeying these rules:  
1. Only one disk can be moved at a time.  
2. A larger disk cannot be placed on top of a smaller disk.  
3. Only top disk of any rod can be moved.  
def tower_of_hanoi(n, a, b, c):  
  if n==1:  
    print (f"move disk 1 from {a} to {b}")  
    return  
  tower_of_hanoi(n-1,a,c,b)  
  print (f"Move disk {n} from {a} to {c}")  
  tower_of_hanoi(n-1, b, a, c)  
num_disks = 3  
tower_of_hanoi(num_disks, 'A', 'B','C')  

Q.2]Write a program to simulate 4-Queen/N-Queen problem.  
- we create a 4x4 board filled with '.' which means empty.  
- Checking if placing a queen at (row, col) is safe by checks:  
  -  Same column above  
  -  Same row  
  -  upper left diagonal  
  -  upper right diagonal  
Code:  def print_board(board):  
  for row in board:  
    print(" ".join(row))  
  print()  
def is_safe(board, row, col, n):  
  for i in range(row):  
    if board[i][col] == 'Q':  
      return False  
  i, j = row, col  
  while i>=0 and j>=0:  
    if board[i][j] == 'Q':  
      return False  
    i -= 1  
    j -= 1  
  i, j = row, col  
  while i>=0 and j<n:  
    if board[i][j] == 'Q':  
      return False  
    i -= 1  
    j += 1  
  return True  

def solve_queens(board, row, n):  
  if row == n:  
    print_board(board)  
    return True  
  for col in range(n):  
    if is_safe(board, row, col, n):  
      board[row][col] = 'Q'  
      if solve_queens(board, row+1, n):  
        return True  
      board[row][col] = '.'  
  return False  

def four_queens():  
  n = 4  
  board = [['.' for _ in range(n)] for _ in range(n)]  
  if not solve_queens(board, 0, n):  
    print("No Solution found")  
four_queens()  

Q.1]Alpha Beta Search.  
tree = {  
  'A': ['B', 'C'],  
  'B': [3,5],  
  'C': [6,9]
}  
def minimax_alpha_beta(node, depth, alpha, beta, max_player):  
  if depth==0 :
  if node in tree: 
  return tree[node][0] if max_player else tree[node][0]
  else:
    return node  
  
  if max_player:  
    value = float('-inf')  
    for child in tree[node]:  
      value = max(value, minimax_alpha_beta(child, depth-1, alpha, beta, False))  
      alpha = max(alpha, value)  
      if alpha >= beta:  
        print(f"Pruning branch at node {node}")  
        break  
    return value  
  else:  
    value = float('inf')  
    for child in tree[node]:  
      value = min(value, minimax_alpha_beta(child, depth-1, alpha, beta, True))  
      beta = min(beta, value)  
      if beta <= alpha:  
        print(f"Pruning branch at node {node}")  
        break  
    return value  
  
best_score = minimax_alpha_beta('A', 1, float('-inf'), float('inf'), True)  
print(f"The Best score is: {best_score}")  

Q.2]Rock, paper, scissors.  
import random  
def play():  
  user = input("Enter your choice from rock, paper, scissors: ").lower()  
  choices = ["rock", "paper", "scissors"]  
  computer = random.choice(choices)  
  print(f"You chose : {user}")  
  print(f"Computer chose: {computer}")  
  if user == computer:  
    return "It's a tie!"  
  elif (user == "rock" and computer == "scissors") or 
  (user == "paper" and computer == "rock") or
  (user == "scissors" and computer == "paper"):  
    return "You win!!"  
  elif user not in choices:  
    return "Invalid choice!"  
  else:  
    return "Computer wins!"  

print(play())  

@1] Greedy Breadth First Search.  
graph = {  
  'Arad': [['zerind', 'Sibiu', 'Timisoara'], 366],  
  'Zerind': [['Arad', 'Oradea'], 374],  
  'Oradea': [['zerind', 'Sibiu'], 380],  
  'Sibiu': [['Arad', 'Oradea', 'fagaras', 'Rimnicu Vilcea'], 253],  
  'Timisoara': [['Arad', 'Lugoj'], 329],  
  'Lugoj': [['Timisoara', 'mehadia'], 244],  
  'mehadia': [['Lugoj', 'Drobeta'], 241],  
  'Drobeta': [['mehadia', 'Craiova'], 242],  
  'Craiova': [['Drobeta', 'Rimnicu vilcea', 'Pitesti'], 160],  
  'Rimnica': [['sibiu', 'Craiova', 'Pitesti'], 193],  
  'Fagaras': [['sibiu', 'Bucharest'], 176],  
  'Pitesti': [['Rimnicu Vilcea', 'Craiova', 'Bucharest'], 100],  
  'Bucharest': [['fagaras', 'Pitesti'], 0]  
}  

def greedy_search_rec(graph, prev, dst, path, q):  
  print("Connected nodes of current node", prev, "with h(n) values:")  
  for n in graph[prev]:  
    q[n]=graph[n][1]
    print(n,"→", q[n])  
  while q:  
    mn=min(q, key=q.get)  
    print("Taking minimum h(n) vertex: ", mn)  
    if dst==mn:  
      return path + [dst]  
    new_path = greedy_search_rec(graph, mn, dst, path + [mn], q)  
    if new_path:  
      return new_path  
  return []  

print("Greedy Search Recursive: ", " ->".join(greedy_search_rec(graph, "Arad", "Bucharest", ["Arad"], {})) or "Path not found")  

Q1]. Write a Program to solve water jug problem.
→def water-jug-manual_path():
    steps = []
    a, b = 0, 0
    steps.append((a, b))
    a=5
    steps.append((a, b))
    transfer = min(a,a, 4-b)
    a -= transfer
    b += transfer
    steps.append((a,b))
    b = 0
    steps.append((a, b))
    transfer = min(a, 4-b)
    a -= transfer
    b += transfer
    steps.append((a, b))
    a = 5
    steps.append((a,b))
    transfer = min(a, 4-b)
    a -= transfer
    b += transfer
    steps.append((a, b))
    b = 0
    steps.append((a, b))
    print('steps to reach (2,4):')
    for idx, state in enumerate(steps):
        print(f"Step {idx}: jug1 = [state{0},jug2=[state])
water-jug-manual_path()

Q2]. Write a program to solve travelling salesman problem
→import random
distance = [[0,2,9,10],
[2,0,6,4],
[9,6,0,3],
[10,4,3,0], ]

def get_cost(tour):
    cost = 0
    for i in range(len(tour)):
        cost += distance[tour[i-1]][tour[i]]
    return cost

def get_neighbour(tour):
    a, b = random.sample(range(len(tour)), 2)
    tour[a], tour[b] = tour[b], tour[a]
    return tour

def hill_climb():
    current = [0,1,2,3]
    random.shupple(current)
    current_cost = get_cost(current)
    print("Starting tour:", current, "cost:", current_cost)
    for i in range(10):
        neighbour = current[:]
        neighbour = get_neighbour(neighbour)
        neighbour_cost = get_cost(neighbour)
         random.shupple(current)
    current_cost = get_cost(current)
    print("Starting tour:", current, "cost:", current_state)
    for i in range(10):
        neighbour = current[:]
        neighbour = get_neighbour(neighbour)
        neighbour_cost = get_cost(neighbour)
        if neighbour_cost < current_cost:
            current = neighbour
            current_cost = neighbour_cost
            print("Better tour found:", current, "cost:", current_cost)
    return current, current_cost

best_tour, best_cost = hill_climb()
print("Best tour:", best_tour)
print("Best cost:", best_cost)

Q1]Cannibals & Missionaries.
moves = [(2,0),(0,2),(1,1),(1,0),(0,1)]
def is_valid(m_left, c_left, m_right, c_right):
    if m_left < 0 or m_right < 0 or c_right < 0:
        return False
    if (m_left > 0 and m_left < c_left) or (m_right > 0 and m_right < c_right):
        return False
    return True

def solve():
    from collections import deque
    start = (3,3,1)
    goal = (0,0,0)
    queue = deque()
    queue.append((start, [start]))
    visited = set()
    while queue:
        (m_left, c_left, boat), path = queue.popleft()
        if (m_left, c_left, boat) in visited:
            continue
        visited.add((m_left, c_left, boat))
        if (m_left, c_left, boat) == goal:
            return path
        for m,c in moves:
            if boat == 1:
                new_m_left = m_left - m
                new_c_left = c_left - c
                new_boat = 0
            else:
                new_m_left = m_left + m
                new_c_left = c_left + c
                new_boat = 1
            new_m_right = 3 - new_m_left
            new_c_right = 3 - new_c_left
            if is_valid(new_m_left, new_c_left, new_m_right, new_c_right):
                new_state = (new_m_left, new_c_left, new_boat)
                if new_state not in visited:
                    queue.append((new_state, path + [new_state]))
    return None

steps = solve()
if steps:
    for i, (m,c,b) in enumerate(steps):
        side = "Left" if b == 1 else "Right"
        print(f"Step {i}: Missionaries Left: {m}, Cannibals left: {c}, Boat on: {side}")
else:
    print("No solution found.")

Q2]Number Puzzle (8-Puzzle)
from collections import deque
goal = "123456780"
moves = {
    0: [1,3],
    1: [0,2,4],
    2: [1,5],
    3: [0,4,6],
    4: [1,3,5,7],
    5:[2,4,8] ,
    6:[3,7] ,
    7:[4,6,8] ,
    8:[5,7] 
}

def bfs(start):
    visited = set()
    queue = deque([(start, [])])
    while queue:
        state, path = queue.popleft()
        if state == goal:
            return path + [state]
        if state in visited:
            continue
        visited.add(state)
        zero = state.index('0')
        for move in moves[zero]:
            new_state = list(state)
            new_state[zero], new_state[move] = new_state[move], new_state[zero]
            queue.append((''.join(new_state), path + [state]))
    return None

start = '123405678'
solution = bfs(start)
if solution:
    print("steps to solve:")
    for s in solution:
        print(s[0:3])
        print(s[3:6])
        print(s[6:9])
        print("---")
else:
    print("No solution found.")

Q1]Shuffle deck of cards
import random
suits = ['Hearts', 'Diamonds', 'Clubs', 'Spades']
ranks = ['2','3','4','5','6','7','8','9','10','Jack','Queen','King','Ace']
deck = [rank + ' of ' + suit for suit in suits for rank in ranks]
random.shuffle(deck)
print("Shuffled deck of cards:")
for card in deck:
    print(card)

Q2]Tic-Tac-Toe game
board = ['' for _ in range(9)]
player = 'X'
def show_board():
    print(f'{board}|{board[1]}|{board}')
    print('-----')
    print(f'{board}|{board}|{board}')
    print('-----')
    print(f'{board}|{board}|{board}')

def is_winner(p):
    return (
        (board[0] == p and board[1] == p and board[2] == p) or
        (board[3] == p and board[4] == p and board[5] == p) or
        (board[6] == p and board[7] == p and board[8] == p) or
        (board[0] == p and board[3]== p and board[6] == p) or
        (board[1] == p and board[4] == p and board[7] == p) or
        (board[2] == p and board[5] == p and board[8] == p) or
        (board[0] == p and board[4] == p and board[8] == p) or
        (board[2]== p and board[4]== p and board[6]== p)
    )

def is_tie():
    return '' not in board

def game():
    global player
    while True:
        show_board()
        try:
            move = int(input(f"Player {player} enter 0-8: "))
            if 0 <= move <= 8 and board[move] == '':
                board[move] = player
                if is_winner(player):
                    show_board()
                    print(f"Player {player} wins!")
                    break
                elif is_tie():
                    show_board()
                    print("It's a tie!")
                    break
               if player == 'X':
                   player='O'
                   else:
                      player='X'
            else:
                print("Invalid move")
        except (ValueError, IndexError):
            print("Invalid input. Enter a number 0-8")
game()

Q1]Map Coloring
import itertools
variables = ["A", "B", "C"]
colors = ["Red", "Blue", "Yellow"]
all_assignments = itertools.product(colors, repeat=len(variables))
def valid(assignment):
    A, B, C = assignment
    return (A != B) and (B != C) and (A != C)
solutions = []
for assignment in all_assignments:
    if valid(assignment):
        solutions.append(dict(zip(variables, assignment)))
print("Valid colorings of map:")
for sol in solutions:
    print(sol)

Q1]Arithmetic Associative Law
a = int(input("Enter value for a: "))
b = int(input("Enter value for b: "))
c = int(input("Enter value for c: "))
lhs_add = (a + b) + c
rhs_add = a + (b + c)
print(f"(a + b) + c = ({a} + {b}) + {c} = {lhs_add}")
print(f"a + (b + c) = {a} + ({b} + {c}) = {rhs_add}")
if lhs_add == rhs_add:
    print("Addition associative law holds")
else:
    print("Addition associative law does not hold")

lhs_mul = (a + b) * c
rhs_mul = a * (b + c)
print(f"(a + b) * c = ({a} + {b}) * {c} = {lhs_mul}")
print(f"a * (b + c) = {a} * ({b} + {c}) = {rhs_mul}")
if lhs_mul == rhs_mul:
    print("Multiplication associative law holds")
else:
    print("Multiplication associative law does not hold")

->Boolean Associative Law
print("Enter boolean values as 1 (True) or 0 (False): ")
A = bool(int(input("Enter value for A: ")))
B = bool(int(input("Enter value for B: ")))
C = bool(int(input("Enter value for C: ")))

# OR law
lhs_or = (A or B) or C
rhs_or = A or (B or C)
print(f"(A or B) or C = ({A} or {B}) or {C} = {lhs_or}")
print(f"A or (B or C) = {A} or ({B} or {C}) = {rhs_or}")
if lhs_or == rhs_or:
    print("OR associative law holds")
else:
    print("OR associative law does not hold")

# AND law
lhs_and = (A and B) and C
rhs_and = A and (B and C)
print(f"(A and B) and C = ({A} and {B}) and {C} = {lhs_and}")
print(f"A and (B and C) = {A} and ({B} and {C}) = {rhs_and}")
if lhs_and == rhs_and:
    print("AND associative law holds")
else:
    print("AND associative law does not hold")

Q2]Arithmetic Distributive Law
a = int(input("Enter value for a: "))
b = int(input("Enter value for b: "))
c = int(input("Enter value for c: "))
lhs_add = a * (b + c)
rhs_add = (a * b) + (a * c)
print(f"a * (b + c) = {a} * ({b} + {c}) = {lhs_add}")
print(f"(a * b) + (a * c) = ({a} * {b}) + ({a} * {c}) = {rhs_add}")
if lhs_add == rhs_add:
    print("Arithmetic distributive law holds")
else:
    print("Arithmetic distributive law does not hold")
->Boolean Distributive Law
print("Enter boolean values as 1 (True) or 0 (False): ")
A = bool(int(input("Enter value for A: ")))
B = bool(int(input("Enter value for B: ")))
C = bool(int(input("Enter value for C: ")))
lhs_or = A or (B and C)
rhs_or = (A or B) and (A or C)
print(f"A or (B and C) = {A} or ({B} and {C}) = {lhs_or}")
print(f"(A or B) and (A or C) = ({A} or {B}) and ({A} or {C}) = {rhs_or}")
if lhs_or == rhs_or:
    print("Boolean OR over AND distributive law holds")
else:
    print("Boolean OR over AND distributive law does not hold")

lhs_and = A and (B or C)
rhs_and = (A and B) or (A and C)
print(f"A and (B or C) = {A} and ({B} or {C}) = {lhs_and}")
print(f"(A and B) or (A and C) = ({A} and {B}) or ({A} and {C}) = {rhs_and}")
if lhs_and == rhs_and:
    print("Boolean AND over OR distributive law holds")
else:
    print("Boolean AND over OR distributive law does not hold")
