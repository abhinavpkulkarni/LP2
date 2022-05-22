# LP2
// Selection sort
def sort(nums):
    for i in range(5):
        minpos = i
        for j in range(i,6):
            if nums[j]<nums[minpos]:
                minpos=j
        temp=nums[i]
        nums[i]=nums[minpos]
        nums[minpos]=temp
        
nums=[3,5,6,1,8,4]
sort (nums)
print(nums)

// bfs
import collections
def bfs(graph, root):
    visited = set()
    queue = collections.deque([root])
    while queue:
        vertex = queue.popleft()
        visited.add(vertex)
        for i in graph[vertex]:
            if i not in visited:
                queue.append(i)
    print(visited)

if _name_ =="_main_":
    graph = {0:[1,2], 1:[2], 2:[3], 3:[1,2]}
    bfs(graph, 0)
    
// dfs
def dfs(graph, start, visited=None):
    if visited is None:
        visited = set()
    visited.add(start)
    print(start)
    for next in graph[start] - visited:
        dfs(graph, next, visited)
    return visited
graph = {'0' : set (['1','2']),
        '1' : set (['0','3','4']),
        '2' : set (['0']),
        '3' : set (['1']),
        '4' : set (['2','3'])

}
dfs(graph, '0')

// a* algo
def A_star(graph, start_node, end_node, state):
    m ={}
    value = 0
    if start_node == end_node:
        return
    for node, v in graph[start_node].items():
        value = state[node] + v
        m[node] = value 
    if (m != {}):  
        path[min(m, key=m.get)] = value
        A_star(graph, min(m, key=m.get), end_node, state)
    return path


path = {}
path['A'] = 0
bp = (A_star(graph,'A','J',state))

print (list(bp))
print("Total cost: {}".format(sum(bp.values())))
print(bp)

// Nqueen problem
global N
N = 4
 
def printSolution(board):
    for i in range(N):
        for j in range(N):
            print (board[i][j], end = " ")
        print()
 
def isSafe(board, row, col):
 
    
    for i in range(col):
        if board[row][i] == 1:
            return False
 
    
    for i, j in zip(range(row, -1, -1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    for i, j in zip(range(row, N, 1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    return True
 
def solveNQUtil(board, col):
    
    
    if col >= N:
        return True
 
    for i in range(N):
 
        if isSafe(board, i, col):
            
            
            board[i][col] = 1
 
            
            if solveNQUtil(board, col + 1) == True:
                return True
 
        
            board[i][col] = 0
 
    return False
 
def solveNQ():
    board = [ [0, 0, 0, 0],
            [0, 0, 0, 0],
            [0, 0, 0, 0],
            [0, 0, 0, 0] ]
 
    if solveNQUtil(board, 0) == False:
        print ("Solution does not exist")
        return False
 
    printSolution(board)
    return True
 
# Driver Code
solveNQ()
