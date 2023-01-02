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

## Print in Reverse
Problem Link: https://hackerrank.com/challenges/print-the-elements-of-a-linked-list-in-reverse/problem

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def reversePrint(llist):
    if llist == None:
        return
    reversePrint(llist.next)
    print(llist.data)
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
void reversePrint(SinglyLinkedListNode *llist) {
    if (llist == NULL)
        return;
    reversePrint(llist->next);
    cout << llist->data << '\n';
}
```

</details>

## Reverse a linked list
Problem Link: https://hackerrank.com/challenges/reverse-a-linked-list/problem

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def reverse(llist):
    if llist == None:
        return llist
    prev_node = None
    curr_node = llist
    next_node = None
    while curr_node:
        next_node = curr_node.next
        curr_node.next = prev_node
        prev_node = curr_node
        curr_node = next_node
    return prev_node
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
SinglyLinkedListNode* reverse(SinglyLinkedListNode *llist) {
    if (llist == NULL)
        return llist;
    SinglyLinkedListNode *prev_node = NULL;
    SinglyLinkedListNode *curr_node = llist;
    SinglyLinkedListNode *next_node = NULL;
    while (curr_node) {
        next_node = curr_node->next;
        curr_node->next = prev_node;
        prev_node = curr_node;
        curr_node = next_node;
    }
    return prev_node;
}
```

</details>

## Compare two linked lists
Problem Link: https://hackerrank.com/challenges/compare-two-linked-lists/problem

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def compare_lists(llist1, llist2):
    curr1 = llist1
    curr2 = llist2
    while curr1 and curr2 and curr1.data == curr2.data:
        curr1 = curr1.next
        curr2 = curr2.next
    return curr1 == curr2
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
bool compare_lists(SinglyLinkedListNode *llist1, SinglyLinkedListNode *llist2) {
    SinglyLinkedListNode *curr1 = llist1;
    SinglyLinkedListNode *curr2 = llist2;
    while (curr1 and curr2 and curr1->data == curr2->data) {
        curr1 = curr1->next;
        curr2 = curr2->next;
    }
    return curr1 == curr2;
}
```

</details>

## Merge two sorted linked lists
Problem Link: https://hackerrank.com/challenges/merge-two-sorted-linked-lists/problem

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def mergeLists(llist1, llist2):
    curr1 = llist1
    curr2 = llist2
    head = SinglyLinkedListNode(0)
    curr = head
    while curr1 and curr2:
        if curr1.data < curr2.data:
            curr.next = curr1
            curr = curr.next
            curr1 = curr1.next
        else:
            curr.next = curr2
            curr = curr.next
            curr2 = curr2.next
    while curr1:
        curr.next = curr1
        curr = curr.next
        curr1 = curr1.next
    while curr2:
        curr.next = curr2
        curr = curr.next
        curr2 = curr2.next
    return head.next
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
SinglyLinkedListNode* mergeLists(SinglyLinkedListNode *llist1, SinglyLinkedListNode *llist2) {
    SinglyLinkedListNode *curr1 = llist1;
    SinglyLinkedListNode *curr2 = llist2;
    SinglyLinkedListNode *head = new SinglyLinkedListNode(0);
    SinglyLinkedListNode *curr = head;
    while (curr1 and curr2) {
        if (curr1->data < curr2->data) {
            curr->next = curr1;
            curr = curr->next;
            curr1 = curr1->next;
        }
        else {
            curr->next = curr2;
            curr = curr->next;
            curr2 = curr2->next;
        }
    }
    while (curr1) {
        curr->next = curr1;
        curr = curr->next;
        curr1 = curr1->next;
    }
    while (curr2) {
        curr->next = curr2;
        curr = curr->next;
        curr2 = curr2->next;
    }
    return head->next;
}
```

</details>

## Get Node Value
Problem Link: https://hackerrank.com/challenges/get-the-value-of-the-node-at-a-specific-position-from-the-tail/problem

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def getNode(llist, positionFromTail):
    n = 0
    curr = llist
    while curr:
        curr = curr.next
        n += 1
    n -= positionFromTail + 1
    curr = llist
    while n:
        curr = curr.next
        n -= 1
    return curr.data
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int getNode(SinglyLinkedListNode *llist, int positionFromTail) {
    int n = 0;
    SinglyLinkedListNode *curr = llist;
    while (curr){
        curr = curr->next;
        n ++;
    }
    n -= positionFromTail + 1;
    curr = llist;
    while (n){
        curr = curr->next;
        n --;
    }
    return curr->data;
}
```

</details>

## Delete duplicate-value nodes from a sorted linked list
Problem Link: https://hackerrank.com/challenges/delete-duplicate-value-nodes-from-a-sorted-linked-list/problem

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def removeDuplicates(llist):
    curr = llist
    while curr.next:
        if curr.data == curr.next.data:
            deleted_node = curr.next
            curr.next = curr.next.next
            del deleted_node
        else:
            curr = curr.next
    return llist
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
SinglyLinkedListNode* removeDuplicates(SinglyLinkedListNode *llist) {
    SinglyLinkedListNode *curr = llist;
    while (curr->next) {
        if (curr->data == curr->next->data) {
            SinglyLinkedListNode *deleted_node = curr->next;
            curr->next = curr->next->next;
            delete(deleted_node);
        }
        else {
            curr = curr->next;
        }
    }
    return llist;
}
```

</details>

## Find Merge Point of Two Lists
Problem Link: https://hackerrank.com/challenges/find-the-merge-point-of-two-joined-linked-lists/problem

<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def findMergeNode(head1, head2):
    curr1 = head1
    curr2 = head2
    len1, len2 = 0, 0
    while curr1:
        curr1 = curr1.next
        len1 += 1
    while curr2:
        curr2 = curr2.next
        len2 +=1
    while len1 > len2:
        head1 = head1.next
        len1 -= 1
    while len2 > len1:
        head2 = head2.next
        len2 -= 1
    curr1 = head1
    curr2 = head2
    while curr1 and curr2 and curr1 != curr2:
        curr1 = curr1.next
        curr2 = curr2.next
    return (curr1.data if curr1 else curr2.data if curr2 else -1)
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/arrays-linkedlists.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int findMergeNode(SinglyLinkedListNode *head1, SinglyLinkedListNode *head2) {
    SinglyLinkedListNode *curr1 = head1;
    SinglyLinkedListNode *curr2 = head2;
    int len1 = 0, len2 = 0;
    while (curr1) {
        curr1 = curr1->next;
        len1 ++;
    }
    while (curr2) {
        curr2 = curr2->next;
        len2 ++;
    }
    while (len1 > len2) {
        head1 = head1->next;
        len1 --;
    }
    while (len2 > len1) {
        head2 = head2->next;
        len2 --;
    }
    curr1 = head1;
    curr2 = head2;
    while (curr1 and curr2 and curr1 != curr2) {
        curr1 = curr1->next;
        curr2 = curr2->next;
    }
    return (curr1? curr1->data : curr2? curr2->data : -1);
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

