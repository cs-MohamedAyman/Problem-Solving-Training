<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="80" src="/logos/hackerrank.png"></img></a>

# HackerRank OJ - CPP Programming Language <br> Introduction `20 problems`

## hello world c
Problem Link: https://www.hackerrank.com/challenges/hello-world-c/problem

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
    char s[100]; 
    fgets(s, sizeof(s), stdin);
    printf("Hello, World!\n");
    printf("%s", s );

```

</details>

## Playing With Characters
Problem Link: https://www.hackerrank.com/challenges/playing-with-characters/problem

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
    char ch;
    char str[100];
    char sentence[100];

    scanf("%c", &ch);
    scanf("\n");
    scanf("%s", str);
    scanf("\n");

    scanf("%[^\n]%*c", sentence);

    printf("%c\n", ch);

    printf("%s\n", str);

    printf("%s\n", sentence);  

```

</details>

## Sum and Difference of Two Numbers
Problem Link: https://www.hackerrank.com/challenges/sum-numbers-c/problem

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
    int num1,num2;
    float num3,num4;
    scanf("%d %d",&num1,&num2);
    scanf("%f %f",&num3,&num4);
    printf("%d %d\n", num1+num2, num1-num2);
    printf("%.1f %.1f\n", num3+num4, num3-num4);

```

</details>

## Functions in C
Problem Link: https://www.hackerrank.com/challenges/functions-in-c/problem

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
    int max(int a, int b) {
        return (a > b) ? a : b;
    }
    int max_of_four(int a,int b,int c,int d){
        int max1 = max(a, b);
        int max2 = max(c, d);
        return max(max1, max2);
    }

```

</details>

## Pointers in C
Problem Link: https://www.hackerrank.com/challenges/pointer-in-c/problem

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
    void update(int *a,int *b) {
        // Complete this function   
        int sum = *a + *b;
        int diff = abs(*a - *b);
    
        *a = sum;
        *b = diff;
    }

```

</details>

## Say "Hello, World!" With C++
Problem Link: https://www.hackerrank.com/challenges/cpp-hello-world/problem

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
    cout<<"Hello, World!";
```

</details>

## Input and Output
Problem Link: https://www.hackerrank.com/challenges/cpp-input-and-output/problem

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
    int a,b,c;
    cin>>a>>b>>c;
    int sum =a+b+c;
    cout<<sum;

```

</details>

## Basic Data Types
Problem Link: https://www.hackerrank.com/challenges/c-tutorial-basic-data-types/problem

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
    int a; long b; char c; float d; double e;
    cin>>a>>b>>c>>d>>e;
    cout<<a<<'\n'<<b<<'\n'<<c<<'\n'<<fixed << setprecision(3)<<d<<'\n'<< fixed <<setprecision(3)<< e <<'\n';

```

</details>

## Conditional Statements
Problem Link: https://www.hackerrank.com/challenges/c-tutorial-conditional-if-else/problem

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
    string n_temp;
    getline(cin, n_temp);

    int n = stoi(ltrim(rtrim(n_temp)));
    if (n == 1) {
        cout << "one" << std::endl;
    } else if (n == 2) {
        cout << "two" << std::endl;
    } else if (n == 3) {
        cout << "three" << std::endl;
    } else if (n == 4) {
        cout << "four" << std::endl;
    } else if (n == 5) {
        cout << "five" << std::endl;
    } else if (n == 6) {
        cout << "six" << std::endl;
    } else if (n == 7) {
        cout << "seven" << std::endl;
    } else if (n == 8) {
        cout << "eight" << std::endl;
    } else if (n == 9) {
        cout << "nine" << std::endl;
    } else {
        cout << "Greater than 9" << std::endl;
    }

```

</details>

## For Loop
Problem Link: https://www.hackerrank.com/challenges/c-tutorial-for-loop/problem

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
    int a, b;
    cin >> a >> b;

    for (int i = a; i <= b; i++) {
        if (i >= 1 && i <= 9) {
            string words[] = {"one", "two", "three", "four", "five", "six", "seven", "eight", "nine"};
            cout << words[i - 1] << endl;
        } else if (i % 2 == 0) {
            cout << "even" << endl;
        } else {
            cout << "odd" << std::endl;
        }
    }

```

</details>

## Functions
Problem Link: https://www.hackerrank.com/challenges/c-tutorial-functions/problem

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
    int max_of_four(int a, int b, int c, int d){
        int max1 = max(a, b);
        int max2 = max(c, d);
        return max(max1, max2);
    }

```

</details>

## Pointer
Problem Link: https://www.hackerrank.com/challenges/c-tutorial-pointer/problem

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
    void update(int *a,int *b) {
        // Complete this function 
        int sum = *a + *b;
        int diff = abs(*a - *b);
    
        *a = sum;
        *b = diff;   
    }

```

</details>

## Arrays Introduction
Problem Link: https://www.hackerrank.com/challenges/arrays-introduction/problem

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
  int n;
    cin>>n;
    int arr[n];
     for(int i=0;i<n;i++){
        cin>>arr[i];
    } 
    for(int i=n-1;i>=0;i--){
        cout<<arr[i]<<" ";
    } 

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## Conditional Statements in C
Problem Link: https://www.hackerrank.com/challenges/conditional-statements-in-c/problem

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
switch(n) {
        case 1:
            printf("one");
            break;
        case 2:
            printf("two");
            break;
        case 3:
            printf("three");
            break;
        case 4:
            printf("four");
            break;
        case 5:
            printf("five");
            break;
        case 6:
            printf("six");
            break;
        case 7:
            printf("seven");
            break;
        case 8:
            printf("eight");
            break;
        case 9:
            printf("nine");
            break;
        default:
            printf("Greater than 9");
            break;
    }

```

</details>

## For Loop in C
Problem Link: https://www.hackerrank.com/challenges/for-loop-in-c/problem

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
 for (int i = a; i <= b; ++i) {
        if (i <= 9) {
            switch(i) {
        case 1:
            printf("one");
            break;
        case 2:
            printf("two");
            break;
        case 3:
            printf("three");
            break;
        case 4:
            printf("four");
            break;
        case 5:
            printf("five");
            break;
        case 6:
            printf("six");
            break;
        case 7:
            printf("seven");
            break;
        case 8:
            printf("eight");
            break;
        case 9:
            printf("nine");
            break;
    }
        } else if (i % 2 == 0) {
            printf("even");
        } else {
            printf("odd");
        }
        printf("\n");
    }


```

</details>

## Sum of Digits of a Five Digit Number
Problem Link: https://www.hackerrank.com/challenges/sum-of-digits-of-a-five-digit-number/problem

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
    int sum = 0;
    while (n > 0) {
        int digit = n % 10; 
        sum += digit;       
        n /= 10;            
    }

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-1/hackerrank/cpp/solutions/introduction.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>
