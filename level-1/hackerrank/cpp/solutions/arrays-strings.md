<a href="/level-1/hackerrank/cpp/solutions/arrays-strings.md"><img align="right" width="80" src="/logos/hackerrank.png"></img></a>

# HackerRank OJ - CPP Programming Language <br> Arrays and Strings `10 problems`

## 1D Arrays in C
Problem Link: https://www.hackerrank.com/challenges/1d-arrays-in-c/problem

<a href="/level-1/hackerrank/cpp/solutions/arrays-strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/arrays-strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int main() {  
    int n;
    scanf("%d", &n);
    int *arr = (int*)malloc(n * sizeof(int));
    for (int i = 0; i < n; i++) 
        scanf("%d", &arr[i]);
    int sum = 0;
    for (int i = 0; i < n; i++) 
        sum += arr[i];
    printf("%d\n", sum); 
}

```

</details>

## Array Reversal
Problem Link: https://www.hackerrank.com/challenges/reverse-array-c/problem

<a href="/level-1/hackerrank/cpp/solutions/arrays-strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/arrays-strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int main() {
    int num, *arr, i;
    scanf("%d", &num);
    arr = (int*) malloc(num * sizeof(int));
    for(i = 0; i < num; i++) 
        scanf("%d", arr + i);
      for (int i = 0, j = num - 1; i < j; i++, j--) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
    for(i = 0; i < num; i++)
        printf("%d ", *(arr + i));
}

```

</details>

## Printing Tokens
Problem Link: https://www.hackerrank.com/challenges/printing-tokens-/problem

<a href="/level-1/hackerrank/cpp/solutions/arrays-strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/arrays-strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int main() {
    char *s;
    s = malloc(1024 * sizeof(char));
    scanf("%[^\n]", s);
    s = realloc(s, strlen(s) + 1);
       for (int i = 0; s[i] != '\0'; i++) {
        if (s[i] == ' ' || s[i] == '\n') 
            printf("\n");
        else 
            printf("%c", s[i]);   
    }
}

```

</details>

## Digit Frequency
Problem Link: https://www.hackerrank.com/challenges/frequency-of-digits-1/problem

<a href="/level-1/hackerrank/cpp/solutions/arrays-strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/arrays-strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int main() {
    char s;
    int i, freq[10] = {0};
    while(scanf("%c", &s) == 1)
        if(s >= '0' && s <= '9')
            freq[s-'0']++;               
    for(i = 0; i < 10; i++)
        printf("%d ", freq[i]); 
}

```

</details>

## Dynamic Array in C
Problem Link: https://www.hackerrank.com/challenges/dynamic-array-in-c/problem

<a href="/level-1/hackerrank/cpp/solutions/arrays-strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/arrays-strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
total_number_of_books = (int*)malloc(sizeof(int)* total_number_of_shelves );
total_number_of_pages = (int**)malloc(sizeof(int*)*total_number_of_shelves);
for(int i = 0; i < total_number_of_shelves; i++){
    total_number_of_books[i] = 0;
    total_number_of_pages[i] = (int*)malloc(sizeof(int));
}
while (total_number_of_queries--) {
    int type_of_query;
    scanf("%d", &type_of_query);
    if (type_of_query == 1) {
        int x, y;
        scanf("%d %d", &x, &y);
        *(total_number_of_books + x) += 1;
        *(total_number_of_pages + x) = realloc(*(total_number_of_pages+x),
        *(total_number_of_books + x) * sizeof(int));
        *(*(total_number_of_pages + x) + *(total_number_of_books + x)- 1) = y;
}

```

</details>

## StringStream
Problem Link: https://www.hackerrank.com/challenges/c-tutorial-stringstream/problem

<a href="/level-1/hackerrank/cpp/solutions/arrays-strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/arrays-strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<int> parseInts(string str) {
    stringstream ss(str);
    vector <int> ans;
    int num;
    char ch;
    while (ss.good()) {
        ss >> num >> ch;
        ans.push_back(num);
    }
        return ans;  
}

```

</details>

## Strings
Problem Link: https://www.hackerrank.com/challenges/c-tutorial-strings/problem

<a href="/level-1/hackerrank/cpp/solutions/arrays-strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/arrays-strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int main() {
    string s1, s2;
    cin >> s1 >> s2;
    cout << s1.size() << " " << s2.size() << "\n" << s1 + s2<< "\n";
    swap(s1[0], s2[0]);
    cout << s1 << " " << s2;
}

```

</details>

## Attribute Parser
Problem Link: https://www.hackerrank.com/challenges/attribute-parser/problem

<a href="/level-1/hackerrank/cpp/solutions/arrays-strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/arrays-strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

