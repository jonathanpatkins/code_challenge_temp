# Easy

## Is Palindrome

Bob is being interrogated by a bunch of Aliens! Aliens, because they are dumb, are unable to identify if strings are palindrome. Aliens suggest that if Bob the astronaut can figure out if the inputted string is a palindrome, they won’t kill him. Save Bob!

```python
def is_pal(word):
	"""
	>>> is_pal("cars")
	False
	>>> is_pal("tacocat")
	True
	>>> is_pal("aa")
	True
	>>> is_pal("aba")
	False
	>>> is_pal("tacobcat")
	False
	"""
	pass
```

### Solution

```python
def is_pal(word):
	return word == word[::-1]
```

## Adding Up Evens

Bob needs to add up the even indices of an inputted array. Recall that arrays are 0-indexed

```python
def add_evens(nums):
	"""
	>>> add_evens([5])
	5
	>>> add_evens([1, 2, 3, 4, 5])
	9
	>>> add_evens([-4, 3, 0, 2])
	-4
	"""
	pass
	
```

### Solution

```python
def add_evens(nums):
	total = 0
	for i in range(0, len(nums), 2):
		total += nums[i]
	return total
```

## Adding Up Evens Followup

Dale the astronaut wants to sum up the even indices of a number. Note, for a number the rightmost digit is at the 0th index. 

For example for the number 123 →3 is in index 0, 2 is index 1, and 1 is in index 3. 

```python
def add_evens(nums):
	"""
	>>> add_evens(5)
	5
	>>> add_evens(12345)
	9
	>>> add_evens(4302])
	5
	"""
	pass
	
```

### Solution

```python
def add_evens(nums):
	total = 0
	index = 0
	while nums > 0:
		if index % 2 == 0:
			total += nums % 10
		index += 1
		nums //= 10
	return total
```

# Medium

## Cheese

One day, Sam decides to bathe in cheese. For the amount of cheese necessary, we want to make a bucket of cheese that is `goal` kilograms. We have a number of `small` cheese (1 kilo each) and `big` cheese (5 kilo each).  Return `True` if it is possible to make the goal by choosing from the given cheeses and otherwise `False`. This is a little harder than it looks and can be done without any loops.

Input:

- `small`: number of `small` cheese
- `big`: number of `large` cheese
- `goal`: the target weight

Output:

- whether we can make the target weight or not

```python
def can_cheese(small: int, big: int, goal: int) -> bool:
	"""
	>>> can_cheese(3, 1, 8)
	True
	>>> can_cheese(3, 1, 9)
	False
	>>> can_cheese(3, 2, 10)
	True
	>>> can_cheese(1, 3, 12)
	False
	>>> can_cheese(13, 1, 13)
	True
	>>> can_cheese(14, 0, 13)
	True
	"""
	pass
```

### Solution

```python
def can_cheese(small: int, big: int, goal: int) -> bool:
	if goal > small + big * 5:
		return False
	else:
		return goal % 5 <= small
```

## Cheese Followup

Consider the same problem as before but now the size of the small cheese and the size of the big cheese are now inputs to the function. 

```python
def can_cheese(small, small_size, big, big_size, goal) -> bool:
	"""
	More test cases to come...
	>>> can_cheese(3, 3, 5, 5, 27)
	True
	>>> can_cheese(3, 3, 5, 5, 28)
	True
	>>> can_cheese(3, 3, 5, 5, 32)
	False
	"""
	pass
```

### Solution

```python
def can_cheese(small, small_size, big, big_size, goal) -> bool:
	for a in range(0, small):
		for b in range(0, big):
			if (a * small_size + b * big_size) == goal:
				return True
	return False
```

## Min of the Maxes

Bob is exploring the moon and finds martians holding hands in a line, they cannot let go of the hands they are holding and the line must be kept perfectly straight as per tradition. Each martian holds in their pockets some number of marbles. Bob checks the `k` sequential martians in a row at a time. In this group of `k` he finds the minimum number of marbles a martian is holding in the group and writes it down in his notepad. Bob checks all possible groups of `k` sequential martians from the line of martians. Back at base with his data, Bob emails his supervisor the max number of marbles that he sees from the various counts of marbles that he jotted down.

Input:

- `nums`: array of numbers
- `k`: the size of the sequential martians Bob can check in `nums`

Output:

- the minimum value of all the subsets

```python
def min_of_maxes(nums: int, k: int) -> int:
	"""
	>>> min_of_maxes([1,3,-1,-3,5,3,6,7], 3)
	3
	>>> min_of_maxes([1,3,-1,-3,5,3,6,7], 1)
	-3
	"""
	pass
```

### Solution

```python
def min_of_maxes(nums: int, k: int) -> int:
	maxes = []
	for i in range(len(nums) - k + 1):
		subset = nums[i:i+k]
		mins.append(max(subset))
	return min(maxes)
```

# Hard

## Astronaut Acquaintance

Astronauts in space want to gather together because they are lonely. Given two lists of equal length where astronauts in corresponding indices know each other (ie: [A, B], [C, D] where A and C know each other and B and D know each other), return the min acquaintance sum from all trios. If no trio exists, return -1.

Definitions:

Trio: a group of three astronauts where each astronaut knows each other. 

Acquaintance sum: the number of astronauts a particular trio knows outside of the current trio. We count a trio as knowing an astronaut if one or more members of the trio know the astronaut. 

Input: 

- `space_from`: first list of dogs where each dog knows the dog in the corresponding index in `space_to`
- `space_to`: second list of dogs where each dog knows the dog in the corresponding index in `space_from`

 Output:

- the min acquaintance sum of all doggy trios

```python
def space_acquaintance(space_from: list, space_to: list) -> int:
	"""
	>>> space_acquaintance([1, 2, 2, 3, 4, 5], [2, 4, 5, 5, 5, 6])
	3
	>>> space_acquaintance([1, 4, 4, 2, 5, 6, 7, 2], [3, 1, 3, 5, 6, 7, 5, 6])
	0
	"""
	pass
	
```

### Solution

```python
def space_acquaintance(space_from: list, space_to: list) -> int:
  return_val = float("inf")
  graph = dict()
  
  for a, b in zip(space_from, space_to):
    if a in graph:
      graph[a].add(b)
    else:
      graph[a] = {b}
    if b in graph:
      graph[b].add(a)
    else:
      graph[b] = {a}

  for space1, space1_knows in graph.items():
    for space2 in space1_knows:
      space2_knows = graph[space2]
      for space3 in space2_knows:
        space3_knows = graph[space3]
        if space1 in space3_knows and space1 != space3:
          return_val = min(return_val, len(space1_knows) + len(space2_knows) + len(space3_knows) - 6)

  return -1 if return_val == float("inf") else return_val
```

## Shortest Path

Alex is in space station A, and needs to get to a robotics competition at space station B. Unfortunately, Google Space Maps TM is giving incorrect paths due to malicious people on the way. Luckily, each station is connected to each other by a series of other space stations. Find the shortest path for Alex assuming the cost from traveling from adjacent space stations is one. 

- there will always be a path from space station A to space station B
- the cost of traveling to adjacent space stations is 1

In this question, the space station graph will be represented by a dictionary where the key
is a particular space station, and the value will be a list of other space stations which there is an path to. 

Input: 

- `graph`: the dictionary representation of the graph
- `A`: start node
- `B`: end node

Output:

- the length of the shortest path from `A` to `B`

```python
def shortest_path(graph: dict, A: int, B: int) -> int:
	"""
	>>> shortest_path({1:[2], 2:[]}, 1,2)
	1
	>>> shortest_path({1: [2, 3], 2: [1, 3, 8], 3: [1, 2, 4, 8], 5: [3, 6], 6: [5, 7], 7: [6, 8], 8: [2, 7]}, 1, 1)
	0
	>>> shortest_path({1: [2, 3], 2: [1, 3, 8], 3: [1, 2, 4, 8], 5: [3, 6], 6: [5, 7], 7: [6, 8], 8: [2, 7]}, 1, 8)
	2
	>>> shortest_path({1: [2, 3], 2: [1, 3, 8], 3: [1, 2, 4, 8], 5: [3, 6], 6: [5, 7], 7: [6, 8], 8: [2, 7]}, 4, 7)
	3
	"""
	pass
	
```

### Solution

```python
def shortest_path(graph, A, B):
  q = list()

  q.add(A)
  level = 0
  while len(q) > 0:
    next_level = set()
    for node in q:
      if node == B:
        return level
      for neighbor in graph[node]:
        next_level.add(node)
    q = list(next_level)
    level += 1
```

## Uppercasing (this can be made even harder by assuming that the string can wrap) - ex abcd, a and d are considered adjacent

Terrie has a string of characters. She has the ability to turn uppercase `k` of the letters. What is the length of longest substring of uppercase characters that Terrie can create.

Example:

`k` = 2

input string: “aabbakaa”

To make the max uppercase substring I choose to capitalize the letters “a” and “b”. 

This results in the string “AABBAkAA”.

The longest uppercase substring is therefore “AABBA” which is of length 5.

```python
def longest_uppercase(input, k):
	"""
	>>> longest_uppercase("aaabbcajnnaddgfjn", 2)
	5
	>>> longest_uppercase("aaabbbcajnnnnaddgfjn", 1)
	4
	>>> longest_uppercase("aaabbbcajnnnnadddgfjn", 4)
	9
	"""
	pass
```

### Solution

```python
def longest_uppercase(input, k):
	max_length = 0
	upper = dict()
	curr_len = 0
	leftmost_character = input[0]
	for index, value in enumerate(input):
		if value in upper.keys():
			upper[value] = index
			curr_len += 1
		else if value not in upper.keys() and k > 0:
			upper[value] = index
			curr_len += 1
			k -= 1
		else:
			max_length = max(max_length, curr_length)
			curr_len = index - upper.pop(leftmost_character)
	return max(max_length, curr_len)
```

# These Are Being Shelved Bc of Difficulty or Boring

## Eating Ice Cream

You have a bunch of different ice creams. Each ice cream has an associated tastiness and melting factor. You can eat the ice creams in any order; however, when you eat an ice cream, the other ice creams start to melt. Specifically, all uneaten ice creams get their tastiness multiplied by the melting factor. What is the max tastiness that the person having eaten all the ice cream can achieve?

Each tastiness will be in the range [0,100] and each melting factor will be in
the range [0,1]. All outputs will be rounded to 5 decimal places.

Example: [(4, .9), (6, .5) - If I eat 4 first, then the tastiness will be 
4 + 6*.9 = 9.4. If I eat 6 first, then the utility will be 6 + 4*.5 = 8. The max 
tastiness is therefore 9.4

```python
def max_tastiness(ice_creams):
	"""
	>>> round(max_tastiness([(4,.9), (6,.5)]), 5)
	9.4
	>>> round(max_tastiness([(10,0.1),(5,0.1),(4,0.2),(2,0.6)]), 5)
	10.544
  >>> round(max_tastiness([(0,1),(1,1),(0,0),(1,0),(5,0.4),(4,0.5),(2,0.7)]), 5)
	8.14
	>>> ar = [((0.003*x*x*x + 0.001*x*x + 4.159)%100, (0.00265*x*x)%1) for x in range(10000)]
	>>> round(max_tastiness(ar), 5)
	7534.58121
	"""
  pass
```

### Solution

```python
def max_tastiness(ice_creams):
	ice_creams = [ic for ic in ice_creams if ic[0] > 0]
	ice_creams.sort(key=lambda ic: (1-ic[1])/ic[0])
	f = 1
	total = 0
	for ic in ice_creams:
		total += ic[0] * f
		f *= ic[1]
	return total
```

## Lol Don’t Drown

Due to too many annoying children and uneducated adults at waterparks, all the current lifeguards have quit. The owner, trying to save more money and not caring about lives of children, has employed numbers of impoverished high schoolers as lifeguards. There exists a list of underpaid potential lifeguards, and the times they can be on duty, represented as a tuple (start_minute, end_minute). If we hire a lifeguard, we need to pay them $1/minute for the lifeguard's whole interval (no partial hires). What is the least amount of money we can spend to cover the interval (0, 1440)?

Note: all intervals include start but exclude end. For example, (0,5) means 0,1,2,3,4.  

Constraints:
start_minute ≤ end_minute for each lifeguard
all inputs are integers
there will always be a possible solution

```python
def lifeguard_budget(intervals):
	"""
	>>> lifeguard_budget([(0,1000),(0,500),(500,1440)])
  1440
	>>> lifeguard_budget([(0,1000),(0,500),(501,1440)])
  1939
	>>> lifeguard_budget([(a*5-7,a*5) for a in range(400)])
  2016
  >>> lifeguard_budget([(a*6-10,a*6-2) for a in range(400)][::-1])
  1928
	"""
	pass

```

### Solution

```python
def lifeguard_budget(intervals):
	intervals.sort(key=lambda i: i[0])
	budgets = [float('inf')]*1440
	for i,(st,nd) in reversed(list(enumerate(intervals))):
		cost_if_hire = nd - st + (0 if nd >= 1440 else budgets[max(nd,0)])
		for t in range(max(st, 0), 1440):
			budgets[t] = min(budgets[t], cost_if_hire)
	return budgets[0]
```

## Tree Validation

Jon made the alphabet into a tree! At least, that’s what he claims. To prove it, Jon will give you the edges of the tree as a long string. For example, for this tree:

            A

          /    \

         B     C

          |

         D

Jon would give you the string “AB AC BD”. Each pair of letters is a directed edge, and the string is space-delineated. Not all the letters of the alphabet will be included in the tree, just the ones that Jon remembers.

If Jon’s list of edges is a valid tree, return the number of edges. Otherwise, return the size of the largest subset of edges that does form a valid tree. In a valid tree:

- there is only one root
- all nodes beside the root have one parent
- there are no cycles

```python
def largest_valid_tree(edge_string):
	"""
	>>> largest_valid_tree("AB AC BD")
  3
	>>> largest_valid_tree("AB BC CA")
	2
	"""
	pass
```

### Solution

```python
def largest_valid_tree(edge_string):
	graph = {chr(a):[] for a in range(65,65+26)}
	for c1,c2 in edge_string.split():
		graph[c1].append(c2)
	# DFS from every node
	answers = []
	for c in graph.keys():
		reachable = [False]*26
		queue = [c]
		while len(queue) > 0:
			x = queue.pop()
			if not reachable[ord(x)-65]:
				reachable[ord(x)-65] = True
				queue.extend(graph[x])
		answers.append(sum(reachable) - 1)
	return max(answers)

```

## Prune the Tree

Given a BST and BST root, prune the BST such that every path from root to leaf is less than length X. Return in sorted order a list of all values of the nodes that were pruned during this process.

In this problem our tree will be represented by dictionaries. 
For example the BST:

		2
	        / \
	      9   4
              / \
            3   5
                   \ 
                    6

Is given by the dictionary:
{2: [3, 4], 9: [3, 5], 4: [None, None], 3: [None, None], 5: [None, 6], 6: [None, None]}

Input: 

- `bst`: dictionary representation of the tree
- `root`: `root` of the `bst`
- `X`: max length of path from root to leaf

Output:

- value of nodes pruned in sorted order

We have also provided some helper functions. Feel free to use them.

```python
# traverses to the left child of a node
def left(bst: dict, node: dict) -> dict:
	leftBranch = node["left"]
	return {"value": leftBranch, "left": bst[leftBranch][0], "right": bst[leftBranch][1]}

# traverses to the right child of a node
def right(bst: dict, node: dict) -> dict:
	rightBranch = node["right"]
	return {"value": rightBranch, "left": bst[rightBranch][0], "right": bst[rightBranch][1]}

# returns the value of the node
def value(node: dict) -> int:
	return node["value"]

def prune(bst: dict, root: dict, X: int) -> list:

	"""
	for these it might be easier to give them pictures
	"""
	pass
```

### Solution

```python
# traverses to the left child of a node
def left(bst: dict, node: dict) -> dict:
	leftBranch = node["left"]
	return {"value": leftBranch, "left": bst[leftBranch][0], "right": bst[leftBranch][1]}

# traverses to the right child of a node
def right(bst: dict, node: dict) -> dict:
	rightBranch = node["right"]
	return {"value": rightBranch, "left": bst[rightBranch][0], "right": bst[rightBranch][1]}

# returns the value of the node
def value(node: dict) -> int:
	return node["value"]

pruned = []
def prune(bst: dict, root: dict, X: int) -> list:
	helper(bst, root, X, 0)
	return pruned.sort()

def helper(bst, root, X, total):
	if root == None:
		return
	helper(bst, left(root), X, total + value(root))
	helper(bst, right(root), X, total + value(root))
	
	if total + value(root) > X:
		pruned.add(value(root))
```
