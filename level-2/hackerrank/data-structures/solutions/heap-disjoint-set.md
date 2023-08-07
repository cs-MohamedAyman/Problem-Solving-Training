<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="80" src="/logos/hackerrank.png"></img></a>

# HackerRank OJ - Data Structures <br> Heap & Disjoint Set `10 problems`

## QHEAP1
Problem Link: https://hackerrank.com/challenges/qheap1/problem

<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## Jesse and Cookies
Problem Link: https://hackerrank.com/challenges/jesse-and-cookies/problem

<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
import queue

def cookies(k, A):
    min_heap = queue.PriorityQueue()
    for i in A:
        min_heap.put(i)
    res = 0
    while not min_heap.empty():
        a = min_heap.get()
        if a >= k or min_heap.empty():
            min_heap.put(a)
            break
        b = min_heap.get()
        min_heap.put(a + 2 * b)
        res += 1
    if min_heap.queue[0] >= k:
        return res
    else:
        return -1
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int cookies(int k, vector<int> A) {
    auto comp = [](const int &x, const int &y) { return x > y; };
    priority_queue<int, vector<int>, decltype(comp)> min_heap(comp);
    for (int i : A)
        min_heap.push(i);
    int res = 0;
    while (not min_heap.empty()) {
        int a = min_heap.top();
        min_heap.pop();
        if (a >= k or min_heap.empty()) {
            min_heap.push(a);
            break;
        }
        int b = min_heap.top();
        min_heap.pop();
        min_heap.push(a + 2 * b);
        res ++;
    }
    if (min_heap.top() >= k)
        return res;
    else
        return -1;
}
```

</details>

## Components in a graph
Problem Link: https://hackerrank.com/challenges/components-in-graph/problem

<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class disjoint_set:
    class Node:
        def __init__(self, data=0):
            self.data = data
            self.parent = self
            self.rank = 0

    def __init__(self):
        self.items = dict()

    def make_set(self, data):
        if data not in self.items:
            self.items[data] = self.Node(data)

    def find_set(self, data):
        if data not in self.items:
            return None
        node = self.items[data]
        if node.parent == node:
            return node
        node.parent = self.find_set(node.parent.data)
        return node.parent

    def union_set(self, node1, node2):
        parent1 = self.find_set(node1)
        parent2 = self.find_set(node2)
        if parent1 and parent2 and parent1 != parent2:
            if parent1.rank > parent2.rank:
                parent2.parent = parent1
            elif parent1.rank < parent2.rank:
                parent1.parent = parent2
            else:
                parent1.rank += 1
                parent2.parent = parent1

def componentsInGraph(gb):
    n = len(gb)
    res = [0] * (n+1)
    dj_set = disjoint_set()
    dj_set_max = 0
    dj_set_min = n+1
    for a, b in gb:
        dj_set.make_set(a)
        dj_set.make_set(b)
        dj_set.union_set(a, b)
    for i in dj_set.items.keys():
        x = dj_set.find_set(i).data
        res[x] += 1
    for i in dj_set.items.keys():
        x = dj_set.find_set(i).data
        dj_set_max = max(dj_set_max, res[x])
        if res[x] > 1:
            dj_set_min = min(dj_set_min, res[x])
    return [dj_set_min, dj_set_max]
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class disjoint_set {
public:
    class Node {
    public:
        int data, rank;
        Node* parent;
        Node(int data=0) {
            this->data = data;
            this->parent = this;
            this->rank = 0;
        }
    };

    map<int, Node*> items;
    void make_set(int data) {
        if (this->items.find(data) == items.end())
            this->items[data] = new Node(data);
    }
    Node* find_set(int data) {
        if (this->items.find(data) == items.end())
            return NULL;
        Node* node = this->items[data];
        if (node->parent == node)
            return node;
        node->parent = find_set(node->parent->data);
        return node->parent;
    }
    void union_set(int node1, int node2) {
        Node* parent1 = find_set(node1);
        Node* parent2 = find_set(node2);
        if (parent1 and parent2 and parent1 != parent2) {
            if (parent1->rank > parent2->rank)
                parent2->parent = parent1;
            else if (parent1->rank < parent2->rank)
                parent1->parent = parent2;
            else {
                parent1->rank ++;
                parent2->parent = parent1;
            }
        }
    }
};

vector<int> componentsInGraph(vector<vector<int>> gb) {
    int n = size(gb);
    vector<int> res(n+1, 0);
    disjoint_set dj_set;
    int dj_set_max = 0;
    int dj_set_min = n+1;
    for (auto &it : gb) {
        dj_set.make_set(it[0]);
        dj_set.make_set(it[1]);
        dj_set.union_set(it[0], it[1]);
    }
    for (auto &[i, j] : dj_set.items) {
        int x = dj_set.find_set(i)->data;
        res[x] ++;
    }
    for (auto &[i, j] : dj_set.items) {
        int x = dj_set.find_set(i)->data;
        dj_set_max = max(dj_set_max, res[x]);
        if (res[x] > 1)
            dj_set_min = min(dj_set_min, res[x]);
    }
    return {dj_set_min, dj_set_max};
}
```

</details>

## Contacts
Problem Link: https://hackerrank.com/challenges/contacts/problem

<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Trie:
    class TrieNode:
        def __init__(self):
            self.child = [None] * 26
            self.cnt = 0

    def __init__(self):
        self.root = self.TrieNode()

    def insert(self, word):
        curr = self.root
        for c in word:
            i = ord(c) - ord('a')
            if curr.child[i] == None:
                curr.child[i] = self.TrieNode()
            curr = curr.child[i]
            curr.cnt += 1

    def find(self, word):
        curr = self.root
        res = 0
        for c in word:
            i = ord(c) - ord('a')
            if curr.child[i] != None:
                curr = curr.child[i]
                res = curr.cnt
            else:
                res = 0
                break
        return res

def contacts(queries):
    t = Trie()
    res = []
    for op, w in queries:
        if op == 'add':
            t.insert(w)
        elif op == 'find':
            res.append(t.find(w))
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class TrieNode {
public:
    vector<TrieNode*> child;
    int cnt;
    TrieNode() {
        this->child.assign(26, NULL);
        this->cnt = 0;
    }
};

class Trie {
public:
    TrieNode *root;
    Trie() {
        this->root = new TrieNode();
    }
    void insert(string word) {
        TrieNode *curr = this->root;
        for (char c : word) {
            int i = c - 'a';
            if (curr->child[i] == NULL)
                curr->child[i] = new TrieNode();
            curr = curr->child[i];
            curr->cnt ++;
        }
    }
    int find(string word) {
        TrieNode *curr = this->root;
        int res = 0;
        for (char c : word) {
            int i = c - 'a';
            if (curr->child[i] != NULL) {
                curr = curr->child[i];
                res = curr->cnt;
            }
            else {
                res = 0;
                break;
            }
        }
        return res;
    }
};

vector<int> contacts(vector<vector<string>> queries) {
    Trie t = Trie();
    vector<int> res;
    for (auto &it : queries) {
        string op = it[0], w = it[1];
        if (op == "add")
            t.insert(w);
        else if (op == "find")
            res.push_back(t.find(w));
    }
    return res;
}
```

</details>

## Merging Communities
Problem Link: https://hackerrank.com/challenges/merging-communities/problem

<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class disjoint_set:
    class Node:
        def __init__(self, data=0):
            self.data = data
            self.parent = self
            self.rank = 0
            self.size = 1

    def __init__(self):
        self.items = dict()

    def make_set(self, data):
        if data not in self.items:
            self.items[data] = self.Node(data)

    def find_set(self, data):
        if data not in self.items:
            return None
        node = self.items[data]
        if node.parent == node:
            return node
        node.parent = self.find_set(node.parent.data)
        return node.parent

    def union_set(self, node1, node2):
        parent1 = self.find_set(node1)
        parent2 = self.find_set(node2)
        if parent1 and parent2 and parent1 != parent2:
            if parent1.rank > parent2.rank:
                parent2.parent = parent1
                parent1.size += parent2.size
            elif parent1.rank < parent2.rank:
                parent1.parent = parent2
                parent2.size += parent1.size
            else:
                parent1.rank += 1
                parent2.parent = parent1
                parent1.size += parent2.size
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class disjoint_set {
public:
    class Node {
    public:
        int data, rank, size;
        Node* parent;
        Node(int data=0) {
            this->data = data;
            this->parent = this;
            this->rank = 0;
            this->size = 1;
        }
    };

    map<int, Node*> items;
    void make_set(int data) {
        if (this->items.find(data) == items.end())
            this->items[data] = new Node(data);
    }
    Node* find_set(int data) {
        if (this->items.find(data) == items.end())
            return NULL;
        Node* node = this->items[data];
        if (node->parent == node)
            return node;
        node->parent = find_set(node->parent->data);
        return node->parent;
    }
    void union_set(int node1, int node2) {
        Node* parent1 = find_set(node1);
        Node* parent2 = find_set(node2);
        if (parent1 and parent2 and parent1 != parent2) {
            if (parent1->rank > parent2->rank) {
                parent2->parent = parent1;
                parent1->size += parent2->size;
            }
            else if (parent1->rank < parent2->rank) {
                parent1->parent = parent2;
                parent2->size += parent1->size;
            }
            else {
                parent1->rank ++;
                parent2->parent = parent1;
                parent1->size += parent2->size;
            }
        }
    }
};
```

</details>

## Kundu and Tree
Problem Link: https://hackerrank.com/challenges/kundu-and-tree/problem

<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## Find the Running Median
Problem Link: https://hackerrank.com/challenges/find-the-running-median/problem

<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
import queue

def runningMedian(a):
    res = []
    median = a[0]
    min_heap = queue.PriorityQueue()
    max_heap = queue.PriorityQueue()
    max_heap.put(-median)
    res.append(median)

    for i in range(1, len(a)):
        if a[i] >= median:
            min_heap.put(a[i])
        else:
            max_heap.put(-a[i])

        if min_heap.qsize() - max_heap.qsize() > 1:
            max_heap.put(-min_heap.get())
        elif max_heap.qsize() - min_heap.qsize() > 1:
            min_heap.put(-max_heap.get())

        if max_heap.qsize() == min_heap.qsize():
            x = min_heap.queue[0]
            y = -max_heap.queue[0]
            median = (x + y) / 2
        else:
            if min_heap.qsize() > max_heap.qsize():
                median = min_heap.queue[0]
            else:
                median = -max_heap.queue[0]
        res.append(median)
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<double> runningMedian(vector<int> a) {
    vector<double> res;
    double median = a[0];
    auto comp = [](const int &x, const int &y) { return x > y; };
    priority_queue<int, vector<int>, decltype(comp)> min_heap(comp);
    priority_queue<int> max_heap;
    max_heap.push(median);
    res.push_back(median);

    for (int i=1; i<size(a); i++) {
        if (a[i] >= median)
            min_heap.push(a[i]);
        else
            max_heap.push(a[i]);

        if (int(size(min_heap)) - int(size(max_heap)) > 1) {
            max_heap.push(min_heap.top());
            min_heap.pop();
        }
        else if (int(size(max_heap)) - int(size(min_heap)) > 1) {
            min_heap.push(max_heap.top());
            max_heap.pop();
        }

        if (int(size(max_heap)) == int(size(min_heap))) {
            int x = min_heap.top();
            int y = max_heap.top();
            median = (x + y) / 2.0;
        }
        else {
            if (int(size(min_heap)) > int(size(max_heap)))
                median = min_heap.top();
            else
                median = max_heap.top();
        }
        res.push_back(median);
    }
    return res;
}
```

</details>

## Minimum Average Waiting Time
Problem Link: https://hackerrank.com/challenges/minimum-average-waiting-time/problem

<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## Super Maximum Cost Queries
Problem Link: https://hackerrank.com/challenges/maximum-cost-queries/problem

<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## No Prefix Set
Problem Link: https://hackerrank.com/challenges/no-prefix-set/problem

<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/heap-disjoint-set.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>
