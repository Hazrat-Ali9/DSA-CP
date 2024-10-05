I can see the list of programming problems you uploaded in the image. Here are C++ solutions for each of the listed problems:

---

### 1. **Find the minimum and maximum element in an array**

```cpp
#include <iostream>
#include <climits>
using namespace std;

int main() {
    int n;
    cout << "Enter size of array: ";
    cin >> n;
    int arr[n];
    
    cout << "Enter elements: ";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    int minElement = INT_MAX, maxElement = INT_MIN;

    for (int i = 0; i < n; i++) {
        if (arr[i] < minElement) minElement = arr[i];
        if (arr[i] > maxElement) maxElement = arr[i];
    }

    cout << "Minimum: " << minElement << "\nMaximum: " << maxElement << endl;
    return 0;
}
```

---

### 2. **Write a program to reverse the array**

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter size of array: ";
    cin >> n;
    int arr[n];
    
    cout << "Enter elements: ";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    cout << "Reversed Array: ";
    for (int i = n - 1; i >= 0; i--) {
        cout << arr[i] << " ";
    }
    cout << endl;
    return 0;
}
```

---

### 3. **Write a program to sort the given array**

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

int main() {
    int n;
    cout << "Enter size of array: ";
    cin >> n;
    int arr[n];

    cout << "Enter elements: ";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    sort(arr, arr + n);

    cout << "Sorted Array: ";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
    return 0;
}
```

---

### 4. **Reverse a string using a stack**

```cpp
#include <iostream>
#include <stack>
using namespace std;

int main() {
    string id;
    cout << "Enter your ID: ";
    cin >> id;

    stack<char> s;
    for (char ch : id) {
        s.push(ch);
    }

    cout << "Reversed ID: ";
    while (!s.empty()) {
        cout << s.top();
        s.pop();
    }
    cout << endl;
    return 0;
}
```

---

### 5. **Implement a stack using a singly linked list**

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

class Stack {
    Node* top;
public:
    Stack() { top = NULL; }

    void push(int data) {
        Node* newNode = new Node();
        newNode->data = data;
        newNode->next = top;
        top = newNode;
    }

    void pop() {
        if (top == NULL) {
            cout << "Stack is empty!" << endl;
            return;
        }
        Node* temp = top;
        top = top->next;
        delete temp;
    }

    void display() {
        Node* temp = top;
        while (temp != NULL) {
            cout << temp->data << " ";
            temp = temp->next;
        }
        cout << endl;
    }
};

int main() {
    Stack stack;
    stack.push(10);
    stack.push(20);
    stack.push(30);
    cout << "Stack: ";
    stack.display();
    stack.pop();
    cout << "Stack after pop: ";
    stack.display();
    return 0;
}
```

---

### 6. **Implement a queue using an array with a function to remove an element**

```cpp
#include <iostream>
using namespace std;

class Queue {
    int front, rear, size;
    int* arr;
public:
    Queue(int size) {
        this->size = size;
        arr = new int[size];
        front = rear = -1;
    }

    void enqueue(int value) {
        if (rear == size - 1) {
            cout << "Queue is full!" << endl;
            return;
        }
        if (front == -1) front = 0;
        arr[++rear] = value;
    }

    void dequeue() {
        if (front == -1 || front > rear) {
            cout << "Queue is empty!" << endl;
            return;
        }
        cout << "Removed element: " << arr[front++] << endl;
    }

    void display() {
        if (front == -1 || front > rear) {
            cout << "Queue is empty!" << endl;
            return;
        }
        for (int i = front; i <= rear; i++) {
            cout << arr[i] << " ";
        }
        cout << endl;
    }
};

int main() {
    Queue queue(5);
    queue.enqueue(10);
    queue.enqueue(20);
    queue.enqueue(30);
    cout << "Queue: ";
    queue.display();
    queue.dequeue();
    cout << "Queue after dequeue: ";
    queue.display();
    return 0;
}
```

---

### 7. **Create a node in a linked list**

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

int main() {
    Node* head = new Node();
    head->data = 10;
    head->next = NULL;

    cout << "Node created with data: " << head->data << endl;
    return 0;
}
```

---

### 8. **Any one DP problem: Longest Common Subsequence (LCS)**

```cpp
#include <iostream>
#include <vector>
using namespace std;

int lcs(string X, string Y, int m, int n) {
    vector<vector<int>> dp(m+1, vector<int>(n+1));

    for (int i = 0; i <= m; i++) {
        for (int j = 0; j <= n; j++) {
            if (i == 0 || j == 0)
                dp[i][j] = 0;
            else if (X[i - 1] == Y[j - 1])
                dp[i][j] = dp[i - 1][j - 1] + 1;
            else
                dp[i][j] = max(dp[i - 1][j], dp[i][j - 1]);
        }
    }
    return dp[m][n];
}

int main() {
    string X = "AGGTAB";
    string Y = "GXTXAYB";
    int m = X.size();
    int n = Y.size();
    cout << "Length of LCS is " << lcs(X, Y, m, n) << endl;
    return 0;
}
```

---

### 9. **Count the total number of alphabets, digits, and special characters in a string**

```cpp
#include <iostream>
#include <cctype>
using namespace std;

int main() {
    string str;
    cout << "Enter a string: ";
    cin >> str;

    int alphabets = 0, digits = 0, specialChars = 0;

    for (char ch : str) {
        if (isalpha(ch))
            alphabets++;
        else if (isdigit(ch))
            digits++;
        else
            specialChars++;
    }

    cout << "Alphabets: " << alphabets << "\nDigits: " << digits << "\nSpecial Characters: " << specialChars << endl;
    return 0;
}
```

---

### 10. **Binary Search Tree**

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* left, *right;
    Node(int val) {
        data = val;
        left = right = NULL;
    }
};

Node* insert(Node* root, int val) {
    if (root == NULL) return new Node(val);
    if (val < root->data)
        root->left = insert(root->left, val);
    else
        root->right = insert(root->right, val);
    return root;
}

void inorder(Node* root) {
    if (root == NULL) return;
    inorder(root->left);
    cout << root->data << " ";
    inorder(root->right);
}

int main() {
    Node* root = NULL;
    root = insert(root, 50);
    insert(root, 30);
    insert(root, 20);
    insert(root, 40);
    insert(root, 70);
    insert(root, 60);
    insert(root, 80);

    cout << "Inorder traversal of the BST: ";
    inorder(root);
    cout << endl;

    return 0;
}
```

---

These are C++ implementations for each problem listed in the image. Let me know if you need further explanations or modifications!