<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="80" src="/logos/hackerrank.png"></img></a>

# HackerRank OJ - Data Structures <br> Binary Tree and Balanced Binary Tree `20 problems`

## Tree: Preorder Traversal
Problem Link: https://hackerrank.com/challenges/tree-preorder-traversal/problem

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
    while (not stk.empty()) {
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
Problem Link: https://hackerrank.com/challenges/tree-postorder-traversal/problem

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
    while (not stk.empty()) {
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
Problem Link: https://hackerrank.com/challenges/tree-inorder-traversal/problem

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
    while (not stk.empty() or curr) {
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
Problem Link: https://hackerrank.com/challenges/tree-height-of-a-binary-tree/problem

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
    while (not stk.empty()) {
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
Problem Link: https://hackerrank.com/challenges/tree-top-view/problem

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
Problem Link: https://hackerrank.com/challenges/tree-level-order-traversal/problem

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
    while (not que.empty()) {
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
Problem Link: https://hackerrank.com/challenges/binary-search-tree-insertion/problem

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def insert(self, val):
    if self.root == None:
        self.root = Node(val)
        return
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
    if (root == NULL)
        return new Node(data);

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
    return root;
}
```

</details>

## Binary Search Tree : Lowest Common Ancestor
Problem Link: https://hackerrank.com/challenges/binary-search-tree-lowest-common-ancestor/problem

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
Problem Link: https://hackerrank.com/challenges/tree-huffman-decoding/problem

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
Problem Link: https://hackerrank.com/challenges/swap-nodes-algo/problem

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

## Is This a Binary Search Tree?
Problem Link: https://hackerrank.com/challenges/is-binary-search-tree/problem

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def checkBst(curr, min, max):
    if curr == None:
        return True

    return min < curr.data and curr.data < max and \
           checkBst(curr.left,  min, curr.data) and \
           checkBst(curr.right, curr.data, max)

def check_binary_search_tree_(root):
    return checkBst(root, -2e9, 2e9)
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
bool checkBst(Node* curr, int min, int max) {
    if (curr == NULL)
        return true;

    return min < curr->data and curr->data < max and
           checkBst(curr->left,  min, curr->data) and
           checkBst(curr->right, curr->data, max);
}
bool checkBST(Node* root) {
    return checkBst(root, -2e9, 2e9);
}
```

</details>

## Self Balancing Tree
Problem Link: https://hackerrank.com/challenges/self-balancing-tree/problem

<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class node:
    def __init__(self, val=0):
        self.val = val
        self.left = None
        self.right = None
        self.ht = 1

def get_height(x):
    if x == None:
        return 0
    return x.ht

def get_balance(x):
    if x == None:
        return 0
    return get_height(x.left) - get_height(x.right)

def rightRotate(y):
    x = y.left
    T2 = x.right

    x.right = y
    y.left = T2

    y.ht = max(get_height(y.left), get_height(y.right)) + 1
    x.ht = max(get_height(x.left), get_height(x.right)) + 1

    return x

def leftRotate(x):
    y = x.right
    T2 = y.left

    y.left = x
    x.right = T2

    x.ht = max(get_height(x.left), get_height(x.right)) + 1
    y.ht = max(get_height(y.left), get_height(y.right)) + 1

    return y

def insert(curr, val):
    if curr == None:
        return node(val)
    if val < curr.val:
        curr.left = insert(curr.left, val)
    elif val > curr.val:
        curr.right = insert(curr.right, val)
    curr.ht = 1 + max(get_height(curr.left), get_height(curr.right))

    balance = get_balance(curr)

    if balance > 1:
        if val < curr.left.val:
            return rightRotate(curr)
        else:
            curr.left = leftRotate(curr.left)
            return rightRotate(curr)

    if balance < -1:
        if val > curr.right.val:
            return leftRotate(curr)
        else:
            curr.right = rightRotate(curr.right)
            return leftRotate(curr)

    return curr

def inorder(curr):
    if curr:
        inorder(curr.left)
        bf = get_balance(curr)
        print("{}(BF={})".format(curr.val, bf), end=" ")
        inorder(curr.right)

def preorder(curr):
    if curr:
        bf = get_balance(curr)
        print("{}(BF={})".format(curr.val, bf), end=" ")
        preorder(curr.left)
        preorder(curr.right)

def postorder(curr):
    if curr:
        postorder(curr.left)
        postorder(curr.right)
        bf = get_balance(curr)
        print("{}(BF={})".format(curr.val, bf), end=" ")
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/binary-tree-balanced-binary-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
struct node {
    int val, ht;
    node *left, *right;

    node(int val=0) {
        this->val = val;
        this->left = NULL;
        this->right = NULL;
        this->ht = 1;
    }
};
int get_height(node* x) {
    if (x == NULL)
        return 0;
    return x->ht;
}
int get_balance(node* x) {
    if (x == NULL)
        return 0;
    return get_height(x->left) - get_height(x->right);
}
node* rightRotate(node* y) {
    node* x = y->left;
    node* T2 = x->right;

    x->right = y;
    y->left = T2;

    y->ht = max(get_height(y->left), get_height(y->right)) + 1;
    x->ht = max(get_height(x->left), get_height(x->right)) + 1;

    return x;
}
node* leftRotate(node* x) {
    node *y = x->right;
    node *T2 = y->left;

    y->left = x;
    x->right = T2;

    x->ht = max(get_height(x->left), get_height(x->right)) + 1;
    y->ht = max(get_height(y->left), get_height(y->right)) + 1;

    return y;
}
node* insert(node* curr, int val) {
    if (curr == NULL)
        return new node(val);
    if (val < curr->val)
        curr->left = insert(curr->left, val);
    else if (val > curr->val)
        curr->right = insert(curr->right, val);
    curr->ht = 1 + max(get_height(curr->left), get_height(curr->right));

    int balance = get_balance(curr);

    if (balance > 1) {
        if (val < curr->left->val)
            return rightRotate(curr);
        else {
            curr->left = leftRotate(curr->left);
            return rightRotate(curr);
        }
    }
    if (balance < -1) {
        if (val > curr->right->val)
            return leftRotate(curr);
        else {
            curr->right = rightRotate(curr->right);
            return leftRotate(curr);
        }
    }
    return curr;
}
void inorder(node* curr) {
    if (curr) {
        inorder(curr->left);
        int bf = get_balance(curr);
        printf("%d(BF=%d) ", curr->val, bf);
        inorder(curr->right);
    }
}
void preorder(node* curr) {
    if (curr) {
        int bf = get_balance(curr);
        printf("%d(BF=%d) ", curr->val, bf);
        preorder(curr->left);
        preorder(curr->right);
    }
}
void postorder(node* curr) {
    if (curr) {
        postorder(curr->left);
        postorder(curr->right);
        int bf = get_balance(curr);
        printf("%d(BF=%d) ", curr->val, bf);
    }
}
```

</details>

## Square-Ten Tree
Problem Link: https://hackerrank.com/challenges/square-ten-tree/problem

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

## Balanced Forest
Problem Link: https://hackerrank.com/challenges/balanced-forest/problem

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

## Jenny's Subtrees
Problem Link: https://hackerrank.com/challenges/jenny-subtrees/problem

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

## Array and simple queries
Problem Link: https://hackerrank.com/challenges/array-and-simple-queries/problem

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

## Median Updates
Problem Link: https://hackerrank.com/challenges/median/problem

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

## Kitty's Calculations on a Tree
Problem Link: https://hackerrank.com/challenges/kittys-calculations-on-a-tree/problem

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

## Array Pairs
Problem Link: https://hackerrank.com/challenges/array-pairs/problem

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
