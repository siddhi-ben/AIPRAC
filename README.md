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
