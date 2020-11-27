# py-libs
Custom Python libs and learnings
# Content
1. [Data Structures](https://github.com/kotsky/py-libs#data-structures)
	1. [Hash](https://github.com/kotsky/py-libs#hash)
	2. [String](https://github.com/kotsky/py-libs#string)
	3. [Linked Lists](https://github.com/kotsky/py-libs#linked-lists)
		1. [Singly Linked List](https://github.com/kotsky/py-libs#singly-linked-lists)
		2. [Doubly Linked List](https://github.com/kotsky/py-libs#doubly-linked-lists)
	4. [Memory cells replacement structures](https://github.com/kotsky/py-libs#memory-cells-replacement-structures)
		1. [FIFO](https://github.com/kotsky/py-libs#fifo)
		2. [FILO](https://github.com/kotsky/py-libs#filo)
	5. [Cache Strategies](https://github.com/kotsky/py-libs#cache-strategies)
	6. [Trees](https://github.com/kotsky/py-libs#trees)
		1. [Binary Search Tree](https://github.com/kotsky/py-libs#binary-search-tree)
		2. [Binary Heaps](https://github.com/kotsky/py-libs#binary-heaps)
			1. [Min-Heap](https://github.com/kotsky/py-libs#min-heap)
			2. [Max-Heap](https://github.com/kotsky/py-libs#max-heap)
			3. [Continuous Median Handler](https://github.com/kotsky/py-libs#continuous-median-handler)
		3. [Tries](https://github.com/kotsky/py-libs#tries)
	7. [Graphs](https://github.com/kotsky/py-libs#graphs)
		1. Common Graphs
		2. [Fancy Graphs](https://github.com/kotsky/py-libs#fancy-graphs)
###
2. [Algorithms](https://github.com/kotsky/py-libs#algorithms)
	1. [Sort](https://github.com/kotsky/py-libs#sort)
		1. Array Sort
		2. Linked List Sort
	2. [Search](https://github.com/kotsky/py-libs#search)
		1. Array Search Algorithms
		2. String Search
	3. [Transformation](https://github.com/kotsky/py-libs#transformation)
		1. Create BST from a sorted array
		2. Create DLL from BT: from left to right with flatten_binary_tree()
		3. Invert BT with invert_binary_tree()
	4. [Traversal](https://github.com/kotsky/py-libs#traversal)
		1. Create BST from a sorted array
		2. Create DLL from BT: from left to right
		3. Invert BT
	5. [Validation](https://github.com/kotsky/py-libs#validation)
		1. Binary Tree Traversal
	6. [Merge](https://github.com/kotsky/py-libs#merge)
		1. Array Merge Algorithms
	7. [Fancy Algorithms](https://github.com/kotsky/py-libs#fancy-algorithms)
		1. Topological Sort

###



# Data Structures
The following data structures are described and implemented:
###
## Hash
Python implementation: `hash_table = {}`
Argument: `key: value`
```
table = {1: 2}
table[5] = 4
for key in table:
    print(key)
for value in table.values():
    print(value)
```

### Complexity
- Create - Time: O(N) / Space: O(N)
- Insert/Delete/Search - Time: O(1) - avg, O(N) - worst (hash collidion) / Space: O(1)
Take a note, that hash table has to read input (key) first, and then it will do search in O(1) time. That's why, true search with hash table is in O(K) Time, where K - size of input.
#### Nuances
O(N) time takes memory resizing of cache once we exceed its limit (like a dynamic array), for that, we do O(N) hashing.

### Usage
Great to use when you need fast search/insert/delete in data massive.
There is no order in hash table, but you can add additional attribute as `'index'` to assign it. Or to create LinkedList style by creating `'next_node'`.
Nice to use when need to count letters in strings, search if second string contains permutations of first one and so one in different variosity.

###
## String
Python implementation: `word = 'some_string'` or to convert int `10` to string is `str(10)`.
Strings are immutable in py.
```
sentence = 'Just be a ranger in your soul'
splitted_sentence = sentence.split(' ')  # create list of words
symbol = '%20'
  
# splitted_sentence has to contain only string for .join method
print(symbol.join(splitted_sentence))  # insert symbol between strings

print(sentence.find('be'))  # find first appearance of 'be',
                            # if there is no, then return -1
```

### Complexity
- Create - Time: O(N) / Space: O(N)
- Insert/Delete - Time: O(N) / Space: O(N) - We create brand new string once we insert or delete any letter there.
- Search - Time: O(k) (k - index of letter) / Space: O(1)


### Algorithms / Usage / Problems
Hold in your mind follows:
- Hash tables can be your friends in problems of unique letters.
- 2 pointers to check letters from different indexes.
- Prefix and suffix - how you can use them to solve your problem?
- Use tries data structure in problems of searching/matching + prefix /suffix.
- Majority of usage is Ascii table.

#### Number conversion
- [Roman to Integer](https://github.com/kotsky/programming-exercises/blob/master/String/Roman%20To%20Integer.py): create LUT for pattern searching. If there is no respective number in LUT, then we deal with new part of the number.

#### Search in string

- [Knuth Morris Pratt Algorithm](https://github.com/kotsky/py-libs/blob/master/algorithms/search/knuth_morris_pratt.py)
Find if `substring` is in `string` in O(M + N) Time and O(M) space, where M is length of substring, and N is length of string.

- Aho-Corasick Algorithm	[TBD]
Find if `substring` is in `vocablary`, where `vocablary = [string_one, string_two, ...]` in O(M + N + Z) Time / ??? Space.

- With Tries
Find if `strings` are in `big_string` in O(NS + BS) Time and O(NS) space, where N - number of substrings in small_strings, S - largest len element in small_strings, B - len of big_string.
Tries are in the use for certain searching problems.
[Multi String Search](https://github.com/kotsky/py-libs/blob/master/algorithms/search/string_search_algorithms.py)


#### Unique letters
There are huge variety of tasks to compare letters in strings. Hash table are used widely for such topics:
- Find duplicates in a string.
- Compare uniques of strings.
- [Smallest Substring Containing](https://github.com/kotsky/programming-exercises/blob/master/String/Smallest%20Substring%20Containing.py) - to find the smallest range in a big string, which contains all symbols of a small string. Here we use hash table to track symbols and 2 pointers for range adjustments ("window" method).

#### Edits in strings
- How many edits needs to perform to get same anagrama of string2 from string1? [One Edit Or Less](https://github.com/kotsky/programming-exercises/blob/master/String/One%20Edit%20Or%20Less.py)
  - Some anagramma tasks can be solved by sort all strings into alphabet order.
- Find min number of operation to be done to get string2 from string1. DP method. [Min Number Of Edits](https://github.com/kotsky/programming-exercises/blob/master/Dynamic%20Programming/Min%20Number%20Of%20Edits.py)

#### Compression / Matching
Main idea here is often to split string, and then to build back with certain modification using .join method.
- Convert 'Have a power in your soul' into 'Have%20a%20power%20in%20your%20soul'.
- Compress sequence of same letters into shorter format like 'aaabb' to 'a3b2'. [Word Compression](https://github.com/kotsky/programming-exercises/blob/master/String/Word%20Compression.py)

##### [Patter Match](https://github.com/kotsky/programming-exercises/blob/master/String/Pattern%20Matcher.py)
Here we try to replace certain substrings with predeterminded patterns like `"xxyxxy", "gogopowerrangergogopowerranger" => [x, y] = ["go", "powerranger"]`. Here, we split string onto letters and store it in arrays, and then with pure math we calculate if it's possible to have that pattern for `y` if we have that range size of `x`.

Another example of patterns might be to find out special key word in a string, and to mark it with a special symbol like `_`. 
Example: [Underscorify Substring](https://github.com/kotsky/programming-exercises/blob/master/String/Underscorify%20Substring.py): `['test is in testest this'], 'test' => '_test_ is in _testest_ this'`.
To solve this, simply find each appearance of the special word in the string, merge intervals if needed and create new string.

#### Rotation
- [String Rotation](https://github.com/kotsky/programming-exercises/blob/master/String/String%20Rotation.py) - check if string2 contains preffix of string1. And then check other letters per origin order.

#### Palindromes
Palindrome - a string which reads the same backwards.
To check, is string is a palindrome, traverse with 2 pointers from the start and from the end and check if these letters are equivalent.

In case you need to find the [longest palindrome is string](https://github.com/kotsky/programming-exercises/blob/master/String/Longest%20Palindromic%20Substring.py), go through string and at each index explore in 2 directions if that substring is a palindome.

#### Permutation
Permutation - when you can change order of string. To solve those problems, Unique Letters topic comes to play.
- [Find all permutation](https://github.com/kotsky/programming-exercises/blob/master/String/Find%20All%20Permutation.py)

#### Anagrams
If you need to work with anagrams like `['flop', 'olfp']`, then you might want at first sort strings in alphabet order, and then compare strings and check, if they are anagrams.
- [Group Anagrams](https://github.com/kotsky/programming-exercises/blob/master/String/Group%20Anagrams.py)


###
## Linked Lists
Python implementation:
```
class LLNode:
    def __init__(self, value):
        self.value = value
        #self.prev = None	# optional: for Doubly LL
        self.next = None
```
###Visualisation: 
Singly LL (SLL): `None->1->2->3->4->5->None`
Doubly LL (DLL): `None<->1<->2<->3<->4<->5<->None`
### Singly Linked List
[Singly Linked List implementation](https://github.com/kotsky/py-libs/blob/master/data_structures/linked_lists/singly_linked_list.py)

Methods:
- add value
- generate random SLL
- SLL sorts: merge sort and bubble sort.
- print SLL out
### Doubly Linked List
[Doubly Linked List implementation](https://github.com/kotsky/py-libs/blob/master/data_structures/linked_lists/doubly_linked_list.py)

Methods:
- add node
- set head/tail
- insert node after/before/at idx
- remove node / remove with value
- print SLL out
There is an advice to keep track a LL head and LL tail no matter with LL you are using.
The tail (tail.next) gives instant node appending in the end of LL.

### Complexity
- Create/Copy - Time: O(N) / Space: O(N)
- Get/Insert/Delete/Search (GIDS) - Time: O(i) / Space: O(1), where i - node index
The beauty of LL is that you just need to reassign node before and node after to complete GIDS operation in O(1) Time.
But at first you need to traverse LL to find that node.

### Algorithms / Usage / Problems
LL is great to use when you have to track certain order of values/nodes, and you need to keep tracking head (start node) and tail (end node) of LL. For instance, LL is used to implement queues: FIFO, etc.
A lot of problems can be solved by traversing and counting LL nodes.
For instance, to delete K node from the end - count node to the end, find total number of nodes and then subtract K from it to define the node, which you have to delete/modify.
For other problems, you might use 2-3 (3 for [reversing](https://github.com/kotsky/programming-exercises/blob/master/LinkedList/Reverse%20LL.py)) pointers with different node's steps at each iteration of traversing.
The biggest difficulties are to assign previous and next nodes and handle head & tail properly.

Tips: 
- Try to visualize nodes and their relations. Then, draw a solution with arrows.
- Remember about null pointer.
- Update Head and Tail if needed.
- A lot of problems can be solved in place (no extra memory use).

#### Sort
There are 2 implemented sort methods:
- bubble sort: Time O(N^2) / Space (1)
- merge sort: Time O(N*log(N)) / Space (log(N))
Refer to [singly_linked_list.py](https://github.com/kotsky/py-libs/blob/master/data_structures/linked_lists/singly_linked_list.py)

#### LRU Cahce
Implementation of a [Least Recently Used Cache](https://github.com/kotsky/py-libs/blob/master/data_structures/cache_strategies/lru_cache.py), which was implemented with a DLL.

#### Runner technique
You iterate LL with 2 pointers simultaneously, with one ahead other (fast and slow pointers).

##### Find loop
In your LL you might have a loop:
![Picture](https://github.com/kotsky/py-libs/blob/master/additional_data/pictures/ll_internal_loop.png)
To define it, start traversing with 2 pointers, where every 1 iteration 1st one has step 1 (slow pointer) and 2nd one has step 2 (fast pointer).
If pointers meet at certain point (at node 2*N), then you will have a loop. Better to drawn it by yourself.
Example: [Find a loop](https://github.com/kotsky/programming-exercises/blob/master/LinkedList/Find%20Loop.py)

##### Factorial replacement
`a1->a2->...->an->b1->..->bn` transform to `a1->b1->..->an->bn` - traverse with 2 pointers as in Find Loop above. When fast pointer hits the end point, slow pointer is at the middle. Then, return back fast pointer and do reassigning between slow and fast pointers.

#### Rearrange LL
Sometimes, when you need to rebuild LL based on some K value, it's nice to split LL onto 3 parts, build each separated LL (node.value < k), (node.value = k) and (node.value > k). Then, combine 3 parts into one finale LL.
Be aware, that there might be duplicates or no existing of k value node.
Example: [Rearrange LL](https://github.com/kotsky/py-libs/blob/master/linked_list/Rearrange%20Linked%20List.py)
#### Palindrome
Split linked list on 2 parts and check node by node. Example: [SLL Palindrome Check](https://github.com/kotsky/programming-exercises/blob/master/LinkedList/Linked%20List%20Palindrome.py)


###
## Memory cells replacement structures
The Last-In, First-Out (FILO) method assumes that the last unit to arrive in inventory or more recent is sold first. The First-In, First-Out (FIFO) method assumes that the oldest unit of inventory is the sold first.
Complexity:
- Create - Time: O(N) / Space: O(N)
- Insert/Delete/Search - Time: O(k) / Space: O(+1)
- Add (append) - Time: O(1) / Space: O(+1)
- Pop last element - Time: O(1) / Space: O(-1)

### FIFO
Or Stack works in FILO and simply can be implemented with an array.

#### Stack variations
There might be different types of stacks, except having common methods like `add()`, `pop()`, `peek()` and `is_empty()`.
- Simple [Stack](https://github.com/kotsky/py-libs/blob/master/data_structures/memo_repacement_strategies/filo.py)
- [MinMax Stack](https://github.com/kotsky/py-libs/blob/master/data_structures/memo_repacement_strategies/filo.py) - to track min and max values -> to do that, we have additional min and max stacks, where we track min and max values at each index along common stack array.

#### Usage
Stacks are often useful in certain recursive algorithms. Sometimes you need to push some data in your memory, but then remove by returning back recursively.
Also, stacks can be used to implement recursive algorithm iteratively.
Another usage of stacks is to save elements in its initial order, and then delete them in backward. It can be used for [Tracking Close & Open Brackets](https://github.com/kotsky/programming-exercises/blob/master/Stacks%20And%20Queues/Balanced%20Brackets.py).
Or, when you need to simplify something (like long path) into shorter version, like [Shorter Path](https://github.com/kotsky/programming-exercises/blob/master/Stacks%20And%20Queues/Shorten%20Path.py).

[FIFO: queue implementation](https://github.com/kotsky/py-libs/blob/master/data_structures/memo_repacement_strategies/fifo.py)

Methods: `add()`, `pop()`, `peek()` and `is_empty()`
###
### FILO
Or Queue works in FIFO and simply can be implemented with a Singly Linked List.
Be aware that it's too easy to mess up the first and last nodes, so check them twice.
Queue is used in Breadth-first search or other technics, where at first you append other nodes to explore, and then explore  those nodes in order of adding them to queue.

[FILO: stack implementation](https://github.com/kotsky/py-libs/blob/master/data_structures/memo_repacement_strategies/filo.py)

Methods: `add()`, `pop()`, `peek()` and `is_empty()`
###

## Cache Strategies
### LRU Cache
[LRU Cache implementation](https://github.com/kotsky/py-libs/blob/master/data_structures/cache_strategies/lru_cache.py)

Methods:
- create with user's desired size
- insert key-value pair
- get value from key
- get most recent key
###
## Trees
### Binary Search Tree
In this tree each node has max 2 childs. More in BST.
#### BT Algorithms / Problems / Usage
- [Traversal methods](https://github.com/kotsky/py-libs/blob/master/algorithms/binary_tree_traversal.py)
- When you explore some path, you might try to represent it as a LL or an array. This might be helpful it problems of sum tracking in BT.
- To defined if bt_one is a subtree of bt_two 
	- do pre-order traversal (with includidng NULL nodes as some symbol `X`), which gives same result for the subtree and the tree if they are same by structure and values -> then do array matching.
	- alternative: call at each node match function. There is trade off between space and time complexities in v1 and v2. Discuss it.

###
### Binary Search Tree
Binary Search Tree (BST) has the following condition: 
`node.left.value < node.value <= node.right.value`.

[Binary Search Tree implementation](https://github.com/kotsky/py-libs/data_structures/bst.py)
```
class Node:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None
		
class Tree:
    def __init__(self, value):
		self.root = Node(value)
```
![Picture](https://github.com/kotsky/py-libs/blob/master/additional_data/pictures/bst_vs_not_bst.png)

Besides that, Balanced Binary Tree has log(N) depth, and not-balanced tree might reach full N depth.

![Picture](https://github.com/kotsky/py-libs/blob/master/additional_data/pictures/complete_binary_tree.png)
![Picture](https://github.com/kotsky/py-libs/blob/master/additional_data/pictures/full_binary_tree.png)
![Picture](https://github.com/kotsky/py-libs/blob/master/additional_data/pictures/perfect_binary_tree.png)

#### BST Algorithms / Problems
There are the follows:
- [BST validation](https://github.com/kotsky/py-libs/blob/master/algorithms/validation/bst_validation.py)
- Find out the min depth from a sorted array - or build a balanced BST or check it's depth by number of recursive calls.
There are several things to keep tracking: 1) return root node as your output; 2) track parent node and how did you come to the current node (from the left or from the right?).
In majority, recursion helps to solve GST problems.
- Convert BST to all possible arrays - recursive call at each node to merge in different ways arrays from child nodes with parent node.
- Return Random Node - track how many each node has childs, total size of BST and from that calculate probability of returning certain node.


###
### Binary Heaps
Min-Heap and Max-Heap are a complete Binary Tree.
In Min-Heap parent node has lower value than its child nodes. But in Max-Heap child nodes has bigger value then their parent node.
Its implementation done by using an array structure.
#### Min-Heap
[Min-Heap implementation](https://github.com/kotsky/py-libs/blob/master/data_structures/heaps.py)
Methods: `insert()`, `pop()`, `peek()` and `is_empty()`
#### Max-Heap
[Min-Heap implementation](https://github.com/kotsky/py-libs/blob/master/data_structures/heaps.py)
Methods: `insert()`, `pop()`, `peek()` and `is_empty()`
#### Continuous Median Handler
The point is to track a median during adding more elements to the array.

[Continuous Median Handler implementation](https://github.com/kotsky/py-libs/blob/master/data_structures/continuous_median_handler.py)

#### Complexity
- Create - Time: O(N) - math reason / Space: O(N)
- Insert/Delete/Search - Time: O(log(N)) / Space: O(1)

The attitude between children and parent nodes with array implementation are as follows:
- `parent_index = (child_index - 1) // 2`
- `child_one_index = 2 * parent_index + 1` and `child_two_index = 2 * parent_index + 2`
	
The picture below shows attitude on Max-Heap example:
![Picture](https://github.com/kotsky/py-libs/blob/master/additional_data/pictures/heap_representing.png)


#### Heaps Algorithms / Problems / Usage
Heaps can be used in various problems, where we have to track min and/or max values per some data structure like an array efficiently in log(N) time.
There are listed few examples:
1. When we need track a median value of some array, we can create 2 heaps: min and max, each of which give max value from the 1st part of the array and min value from the 2nd part of the array accordingly. Avaraging of these values gives the median value of the array. [Continuous Median Handler](https://github.com/kotsky/py-libs/blob/master/data_structures/continuous_median_handler.py)
2. [Merge Sorted Arrays](https://github.com/kotsky/py-libs/blob/master/algorithms/merge/array_merge_algorithms.py) - Great usage of Min-Heap -> use min heap as a buffer exchange and comparison of smallest numbers from each subarray. It allows you to improve a speed of searching min value between subarrays from K to log(K), where K is a number of subarrays.


###
### Tries
Trie is a tree data structure to store characters at each node. Trie has one root node, multiple child nodes and might have end node, which can be presented as some special symbol, like `*`, and can indicate complete words.
![Picture](https://github.com/kotsky/py-libs/blob/master/additional_data/pictures/trie.png)

There are:
- Prefix Trie (build Trie from the beggining of the string)
- Suffix Trie (build Trie from the end of the string)
	root->	babc
			 abc
			  bc
			   c
Find its implementation here [Tries](https://github.com/kotsky/py-libs/blob/master/data_structures/tries.py)

#### Tries Algorithms / Problems / Usage
Trie is often used to store vocabulary in one place with further easy accessing and searching in linear time.
One classic problem is to find out if the given words are in some text

###
## Graphs
A graph is a collection nodes with edges.

![Picture](https://github.com/kotsky/py-libs/blob/master/additional_data/pictures/graphs_example.png)

There are 2 types of graph representation:
- Adjacency List (common representation)
- Adjacency Matrix NxN 

![Picture](https://github.com/kotsky/py-libs/blob/master/additional_data/pictures/graphs_adjacency_matrix.png)
	
### Graphs Search
The most common ways of searching in graphs are:
- depth first search (DFS) - explore each branch before changing to other branch
- breadth first search (BFS) - explore neighbours before their childs
BSF is great to find the shortest path, but DFS is easier to implement.
DFS is implemented recursively, and BFS uses Queue.
Take a note, that in graphs we have to track which nodes we already visited before. In some problems, we might need track nodes as visited before and visiting right now.
- bidirectional search - BFS from 2 graphs source to define node of their collision. 
Bidirectional search is faster rather normal BFS, because we don't traverse through all nodes around our target nodes. Mathematically, time complexity for traditional BFS search is O(k^(d)) time, where k - nodes, d - shortest path from target nodes 1 to 2. But there is O(k^(d/2)) time for bidirectional search.

[Simple Graph implementation](https://github.com/kotsky/py-libs/blob/master/data_structures/graph.py)

Methods:
- create graph from vertices and edges
- add nodes/dependencies to graph
- depth first search (DFS) from the start node
- breadth first search (BFS) from the start node

#### Algorithms / Usage / Problems
Graphs are in the use widely in problems, where different nodes are combined into system of dependencies (social network relations).
Also, it can be useful to explore how nodes relate to each others to build certain sequences to complete certain tasks. 
For instance, [Topological Sort](https://github.com/kotsky/py-libs/blob/master/algorithms/topological_sort.py) solves the problem, where we have to understand in which order we have to complete jobs, assuming that some jobs can be completed only after others.

Another usage can be found in matrices. You can imagine it as maps problems - find a path from something to somethings, or explore a path and define if this path is what you are looking for.
For instance, 

### Fancy Graphs
#### [Airport Connections](https://github.com/kotsky/programming-exercises/blob/master/Graph/Airport%20Connections.py)


# Algorithms
## Sort
### [Array Sort](https://github.com/kotsky/py-libs/blob/master/algorithms/sort/array_sort_algorithms.py)
- Merge Sort
- Heap Sort
- Quick Sort
- Selection Sort
- Insertion Sort
- Bubble Sort
### Linked Lists Sort 
Refer to [Singly Linked List](https://github.com/kotsky/py-libs/blob/master/data_structures/linked_lists/singly_linked_list.py) and [Doubly  Linked List](https://github.com/kotsky/py-libs/blob/master/data_structures/linked_lists/doubly_linked_list.py) to find sort methods out.

## Search
### [Array Search Algorithms](https://github.com/kotsky/py-libs/blob/master/algorithms/search/array_search_algorithms.py)
- Binary Search -> to find an element in a sorted array
- Quick Select -> to find kth smallest element in the array
- Search In Sorted Matrix -> to find an element in a sorted matrix
### String Search
- [Knuth Morris Pratt](https://github.com/kotsky/py-libs/blob/master/algorithms/search/knuth_morris_pratt.py) -> to define if "string" contains "substring" in O(N + M) time and O(M) space complexity.
- [Multi String Search](https://github.com/kotsky/py-libs/blob/master/algorithms/search/string_search_algorithms.py) -> find if `strings` are in `big_string` in O(NS + BS) Time and O(NS) Space, where N - number of substrings in small_strings, S - largest len element in small_strings, B - len of big_string.
- Aho-Corasick Algorithm	[TBD]

## Transformation
### [Create BST from a sorted array](https://github.com/kotsky/py-libs/blob/master/algorithms/transformation/array_transformation_functions.py)
### [Create DLL from BT: from left to right](https://github.com/kotsky/py-libs/blob/master/algorithms/transformation/bt_transformation_functions.py) with flatten_binary_tree()
### [Invert BT](https://github.com/kotsky/py-libs/blob/master/algorithms/transformation/bt_transformation_functions.py) with invert_binary_tree()

## Traversal
### [Binary Tree Traversal](https://github.com/kotsky/py-libs/blob/master/algorithms/binary_tree_traversal.py)
- in_order_traverse -> add left branch, then current node and then right branch
- pre_order_traverse -> add node to order before its child nodes
- post_order_traverse -> add node after its child nodes

## Validation
### [Binary Search Tree Validation](https://github.com/kotsky/py-libs/blob/master/algorithms/validation/bst_validation.py)

## Merge
### [Array Merge Algorithms](https://github.com/kotsky/py-libs/blob/master/algorithms/merge/array_merge_algorithms.py)
- Merge Sorted Arrays in O(N*log(K) + K) Time / O(N + K) Time, where N - total number of elements and K - number of subarrays.

## Fancy Algorithms
- [Topological Sort](https://github.com/kotsky/py-libs/blob/master/algorithms/topological_sort.py)

