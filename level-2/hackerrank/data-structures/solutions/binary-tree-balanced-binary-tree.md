<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="80" src="/logos/hackerrank.png"></img></a>

# HackerRank OJ - Data Structures <br> Binary Tree & Balanced Binary Tree `20 problems`

## Tree: Preorder Traversal
Problem Link: https://www.hackerrank.com/challenges/tree-preorder-traversal/problem

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def preOrder(root):
    res = []
    stk = []
    stk.append(root)
    while stk:
        curr = stk.pop()
        if curr.right != None:
            stk.append(curr.right)
        if curr.left != None:
            stk.append(curr.left)
        res.append(curr.info)
    print(*res)
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
void preOrder(Node* root) {
    vector<int> res;
    stack<Node*> stk;
    stk.push(root);
    while (!stk.empty()) {
        Node *curr = stk.top();
        stk.pop();
        if (curr->right != NULL)
            stk.push(curr->right);
        if (curr->left != NULL)
            stk.push(curr->left);
        res.push_back(curr->data);
    }
    for (int &i : res)
        cout << i << ' ';
}
```

</details>

## Tree: Postorder Traversal
Problem Link: https://www.hackerrank.com/challenges/tree-postorder-traversal/problem

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def postOrder(root):
    res = []
    stk = []
    stk.append(root)
    while stk:
        curr = stk.pop()
        if curr.left != None:
            stk.append(curr.left)
        if curr.right != None:
            stk.append(curr.right)
        res.append(curr.info)
    res = res[::-1]
    print(*res)
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
void postOrder(Node* root) {
    vector<int> res;
    stack<Node*> stk;
    stk.push(root);
    while (!stk.empty()) {
        Node *curr = stk.top();
        stk.pop();
        if (curr->left != NULL)
            stk.push(curr->left);
        if (curr->right != NULL)
            stk.push(curr->right);
        res.push_back(curr->data);
    }
    reverse(res.begin(), res.end());
    for (int &i : res)
        cout << i << ' ';
}
```

</details>

## Tree: Inorder Traversal
Problem Link: https://www.hackerrank.com/challenges/tree-inorder-traversal/problem

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def inOrder(root):
    res = []
    stk = []
    curr = root
    while stk or curr:
        if curr:
            stk.append(curr)
            curr = curr.left
        else:
            curr = stk.pop()
            res.append(curr.info)
            curr = curr.right
    print(*res)
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
void inOrder(Node* root) {
    vector<int> res;
    stack<Node*> stk;
    Node *curr = root;
    while (!stk.empty() or curr) {
        if (curr) {
            stk.push(curr);
            curr = curr->left;
        }
        else {
            curr = stk.top();
            stk.pop();
            res.push_back(curr->data);
            curr = curr->right;
        }
    }
    for (int &i : res)
        cout << i << ' ';
}
```

</details>

## Tree: Height of a Binary Tree
Problem Link: https://www.hackerrank.com/challenges/tree-height-of-a-binary-tree/problem

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def height(root):
    res = 0
    stk = []
    height = []
    stk.append(root)
    height.append(0)
    while stk:
        curr = stk.pop()
        curr_height = height.pop()
        if curr.left != None:
            stk.append(curr.left)
            height.append(curr_height+1)
        if curr.right != None:
            stk.append(curr.right)
            height.append(curr_height+1)
        res = max(res, curr_height)
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int height(Node *root) {
    int res = 0;
    stack<Node*> stk;
    stack<int> height;
    stk.push(root);
    height.push(0);
    while (!stk.empty()) {
        Node *curr = stk.top();
        stk.pop();
        int curr_height = height.top();
        height.pop();
        if (curr->left != NULL) {
            stk.push(curr->left);
            height.push(curr_height+1);
        }
        if (curr->right != NULL) {
            stk.push(curr->right);
            height.push(curr_height+1);
        }
        res = max(res, curr_height);
    }
    return res;
}
```

</details>

## Tree : Top View
Problem Link: https://www.hackerrank.com/challenges/tree-top-view/problem

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## Tree: Level Order Traversal
Problem Link: https://www.hackerrank.com/challenges/tree-level-order-traversal/problem

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def levelOrder(root):
    res = []
    que = []
    que.append(root)
    while que:
        curr = que.pop(0)
        if curr.left:
            que.append(curr.left)
        if curr.right:
            que.append(curr.right)
        res.append(curr.info)
    print(*res)
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
void levelOrder(Node* root) {
    vector<int> res;
    queue<Node*> que;
    que.push(root);
    while (!que.empty()) {
        Node *curr = que.front();
        que.pop();
        if (curr->left != NULL)
            que.push(curr->left);
        if (curr->right != NULL)
            que.push(curr->right);
        res.push_back(curr->data);
    }
    for (int &i : res)
        cout << i << ' ';
}
```

</details>

## Binary Search Tree : Insertion
Problem Link: https://www.hackerrank.com/challenges/binary-search-tree-insertion/problem

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
    def insert(self, val):
        if self.root == None:
            self.root = Node(val)
        else:
            curr = self.root
            while True:
                if val < curr.info:
                    if curr.left:
                        curr = curr.left
                    else:
                        curr.left = Node(val)
                        break
                elif val > curr.info:
                    if curr.right:
                        curr = curr.right
                    else:
                        curr.right = Node(val)
                        break
                else:
                    break
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
    Node* insert(Node *root, int data) {
        if (root == NULL) {
            return new Node(data);
        } 
        else {
            Node *curr = root;
            while (true) {
                if (data < curr->data) {
                    if (curr->left)
                        curr = curr->left;
                    else {
                        curr->left = new Node(data);
                        break;
                    }
                }
                else if (data > curr->data) {
                    if (curr->right)
                        curr = curr->right;
                    else {
                        curr->right = new Node(data);
                        break;
                    }
                }
                else
                    break;
            }
        }
        return root;
    }
```

</details>

## Binary Search Tree : Lowest Common Ancestor
Problem Link: https://www.hackerrank.com/challenges/binary-search-tree-lowest-common-ancestor/problem

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def lca(root, v1, v2):
    if root == None:
        return None
    if v1 > v2:
        v1, v2 = v2, v1
    while root.info < v1 or root.info > v2:
        if root.info < v1:
            root = root.right
        elif root.info > v2:
            root = root.left
    return root
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
Node* lca(Node* root, int v1,int v2) {
    if (root == NULL) 
        return NULL;
    if (v1 > v2) {
        int temp = v2;
        v2 = v1;
        v1 = temp;
    }
    while (root->data < v1 or root->data > v2) {
        if (root->data < v1) 
            root = root->right;
        else if (root->data > v2) 
            root = root->left;
    }
    return root;
}
```

</details>

## Tree: Huffman Decoding
Problem Link: https://www.hackerrank.com/challenges/tree-huffman-decoding/problem

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def decodeHuff(root, s):
    decoded_str = ''
    curr = root
    for c in s:
        if c == '0' and curr.left:
            curr = curr.left
        elif c == '1' and curr.right:
            curr = curr.right
        if not curr.left and not curr.right:
            decoded_str += curr.data
            curr = root
    print(decoded_str)
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
void decode_huff(node* root, string s) {
    string decoded_str = "";
    node *curr = root;
    for (char &c : s) {
        if (c == '0' and curr->left)
            curr = curr->left;
        else if (c == '1' and curr->right)
            curr = curr->right;
        if (not curr->left and not curr->right) {
            decoded_str += curr->data;
            curr = root;
        }
    }
    cout << decoded_str;
}
```

</details>

## Swap Nodes [Algo]
Problem Link: https://www.hackerrank.com/challenges/swap-nodes-algo/problem

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

