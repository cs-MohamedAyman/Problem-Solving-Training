<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="80" src="/logos/hackerrank.jpg"></img></a>

# HackerRank OJ - Data Structures - Arrays & Linked Lists

## Arrays - DS
Problem Link: https://hackerrank.com/challenges/arrays-ds/problem

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def reverseArray(a):
    return a[::-1]
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<int> reverseArray(vector<int> a) {
    reverse(a.begin(), a.end());
    return a;
}
```

</details>

## 2D Array - DS
Problem Link: https://hackerrank.com/challenges/2d-array/problem

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def hourglassSum(arr):
    filter_arr = [[1,1,1], [0,1,0], [1,1,1]]
    res = -int(2e9)
    for i in range(4):
        for j in range(4):
            curr_sum = 0
            for k in range(3):
                for w in range(3):
                    curr_sum += arr[i+k][j+w] * filter_arr[k][w]
            res = max(res, curr_sum)
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int hourglassSum(vector<vector<int>> arr) {
    vector<vector<int>> filter_arr = {{1,1,1}, {0,1,0}, {1,1,1}};
    int res = -int(2e9);
    for (int i=0; i<4; i++) {
        for (int j=0; j<4; j++) {
            int curr_sum = 0;
            for (int k=0; k<3; k++)
                for (int w=0; w<3; w++)
                    curr_sum += arr[i+k][j+w] * filter_arr[k][w];
            res = max(res, curr_sum);
        }
    }
    return res;
}
```

</details>

## Dynamic Array
Problem Link: https://hackerrank.com/challenges/dynamic-array/problem

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def dynamicArray(n, queries):
    res = []
    arr = [[] for _ in range(n)]
    last_ans = 0
    for t, x, y in queries:
        if t == 1:
            idx = (x^last_ans) % n
            arr[idx].append(y)
        else:
            idx = (x^last_ans) % n
            last_ans = arr[idx][y % len(arr[idx])]
            res.append(last_ans)
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<int> dynamicArray(int n, vector<vector<int>> queries) {
    vector<int> res;
    vector<vector<int>> arr(n);
    int last_ans = 0;
    for (auto query : queries) {
        int t = query[0], x = query[1], y = query[2];
        if (t == 1) {
            int idx = (x^last_ans) % n;
            arr[idx].push_back(y);
        }
        else {
            int idx = (x^last_ans) % n;
            last_ans = arr[idx][y % size(arr[idx])];
            res.push_back(last_ans);
        }
    }
    return res;
}
```

</details>

## Left Rotation
Problem Link: https://hackerrank.com/challenges/array-left-rotation/problem

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def rotateLeft(d, arr):
    n = len(arr)
    res = [0] * n
    for i in range(n):
        res[i] = arr[(i+d)%n]
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<int> rotateLeft(int d, vector<int> arr) {
    int n = size(arr);
    vector<int> res(n);
    for (int i=0; i<n; i++)
        res[i] = arr[(i+d)%n];
    return res;
}
```

</details>

## Print the Elements of a Linked List
Problem Link: https://hackerrank.com/challenges/print-the-elements-of-a-linked-list/problem

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def printLinkedList(head):
    curr_node = head
    while curr_node:
        print(curr_node.data);
        curr_node = curr_node.next
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
void printLinkedList(SinglyLinkedListNode *head) {
    SinglyLinkedListNode *curr_node = head;
    while (curr_node) {
        cout << curr_node->data << '\n';
        curr_node = curr_node->next;
    }
}
```

</details>

## Insert a Node at the Tail of a Linked List
Problem Link: https://hackerrank.com/challenges/insert-a-node-at-the-tail-of-a-linked-list/problem

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def insertNodeAtTail(head, data):
    if head == None:
        head = SinglyLinkedListNode(data)
        return head
    curr_node = head
    while curr_node.next:
        curr_node = curr_node.next
    curr_node.next = SinglyLinkedListNode(data)
    return head
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
SinglyLinkedListNode* insertNodeAtTail(SinglyLinkedListNode *head, int data) {
    if (head == NULL) {
        head = new SinglyLinkedListNode(data);
        return head;
    }
    SinglyLinkedListNode *curr_node = head;
    while (curr_node->next)
        curr_node = curr_node->next;
    curr_node->next = new SinglyLinkedListNode(data);
    return head;
}
```

</details>

## Insert a node at the head of a linked list
Problem Link: https://hackerrank.com/challenges/insert-a-node-at-the-head-of-a-linked-list/problem

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def insertNodeAtHead(llist, data):
    new_node = SinglyLinkedListNode(data)
    new_node.next = llist
    llist = new_node
    return llist
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
SinglyLinkedListNode* insertNodeAtHead(SinglyLinkedListNode *llist, int data) {
    SinglyLinkedListNode *new_node = new SinglyLinkedListNode(data);
    new_node->next = llist;
    llist = new_node;
    return llist;
}
```

</details>

## Insert a node at a specific position in a linked list
Problem Link: https://hackerrank.com/challenges/insert-a-node-at-a-specific-position-in-a-linked-list/problem

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def insertNodeAtPosition(llist, data, position):
    if position == 0:
        new_node = SinglyLinkedListNode(data)
        new_node.next = llist
        llist = new_node
        return llist
    i = 0
    curr_node = llist
    while curr_node.next and i < position-1:
        curr_node = curr_node.next
        i += 1
    new_node = SinglyLinkedListNode(data)
    new_node.next = curr_node.next
    curr_node.next = new_node
    return llist
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
SinglyLinkedListNode* insertNodeAtPosition(SinglyLinkedListNode *llist, int data, int position) {
    if (position == 0) {
        SinglyLinkedListNode *new_node = new SinglyLinkedListNode(data);
        new_node->next = llist;
        llist = new_node;
        return llist;
    }
    int i = 0;
    SinglyLinkedListNode *curr_node = llist;
    while (curr_node->next and i < position-1) {
        curr_node = curr_node->next;
        i ++;
    }
    SinglyLinkedListNode *new_node = new SinglyLinkedListNode(data);
    new_node->next = curr_node->next;
    curr_node->next = new_node;
    return llist;
}
```

</details>

## Delete a Node
Problem Link: https://hackerrank.com/challenges/delete-a-node-from-a-linked-list/problem

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def deleteNode(llist, position):
    if position == 0:
        deleted_node = llist
        llist = llist.next
        del deleted_node
        return llist
    i = 0
    curr_node = llist
    while curr_node.next and i < position-1:
        curr_node = curr_node.next
        i += 1
    deleted_node = curr_node.next
    curr_node.next = curr_node.next.next
    del deleted_node
    return llist
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
SinglyLinkedListNode* deleteNode(SinglyLinkedListNode *llist, int position) {
    if (position == 0) {
        SinglyLinkedListNode *deleted_node = llist;
        llist = llist->next;
        delete(deleted_node);
        return llist;
    }
    int i = 0;
    SinglyLinkedListNode *curr_node = llist;
    while (curr_node->next and i < position-1) {
        curr_node = curr_node->next;
        i ++;
    }
    SinglyLinkedListNode *deleted_node = curr_node->next;
    curr_node->next = curr_node->next->next;
    delete(deleted_node);
    return llist;
}
```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

