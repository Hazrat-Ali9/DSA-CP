Here are the C++ programs for each of the given problems:

1. **Find the minimum and maximum element in an array:**

```cpp
#include<iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter the number of elements: ";
    cin >> n;
    int arr[n];
    
    cout << "Enter elements: ";
    for(int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    int min = arr[0], max = arr[0];
    
    for(int i = 1; i < n; i++) {
        if(arr[i] < min)
            min = arr[i];
        if(arr[i] > max)
            max = arr[i];
    }
    
    cout << "Minimum: " << min << endl;
    cout << "Maximum: " << max << endl;

    return 0;
}
```

2. **Write a program to reverse the array:**

```cpp
#include<iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter the number of elements: ";
    cin >> n;
    int arr[n];
    
    cout << "Enter elements: ";
    for(int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    cout << "Reversed array: ";
    for(int i = n-1; i >= 0; i--) {
        cout << arr[i] << " ";
    }
    
    return 0;
}
```

3. **Write a program to sort the given array:**

```cpp
#include<iostream>
#include<algorithm>
using namespace std;

int main() {
    int n;
    cout << "Enter the number of elements: ";
    cin >> n;
    int arr[n];
    
    cout << "Enter elements: ";
    for(int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    sort(arr, arr+n);
    
    cout << "Sorted array: ";
    for(int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```

4. **Write a program that accepts a string of your ID and reverses it using a stack:**

```cpp
#include<iostream>
#include<stack>
using namespace std;

int main() {
    string id;
    cout << "Enter your ID: ";
    cin >> id;
    
    stack<char> s;
    for(char c : id) {
        s.push(c);
    }
    
    cout << "Reversed ID: ";
    while(!s.empty()) {
        cout << s.top();
        s.pop();
    }
    
    return 0;
}
```

5. **Write a program to implement a stack using a singly linked list:**

```cpp
#include<iostream>
using namespace std;

class Node {
public:
    int data;
    Node* next;
};

class Stack {
    Node* top;
public:
    Stack() { top = nullptr; }
    
    void push(int x) {
        Node* temp = new Node();
        temp->data = x;
        temp->next = top;
        top = temp;
    }
    
    void pop() {
        if(top == nullptr) {
            cout << "Stack Underflow\n";
            return;
        }
        Node* temp = top;
        top = top->next;
        delete temp;
    }
    
    void display() {
        Node* temp = top;
        while(temp != nullptr) {
            cout << temp->data << " ";
            temp = temp->next;
        }
        cout << endl;
    }
};

int main() {
    Stack s;
    s.push(10);
    s.push(20);
    s.push(30);
    
    s.display();
    s.pop();
    s.display();
    
    return 0;
}
```

6. **Write a program to implement a queue using an array. Create a function that removes an element from the queue:**

```cpp
#include<iostream>
using namespace std;

class Queue {
    int front, rear, size;
    int* arr;
public:
    Queue(int s) {
        front = rear = 0;
        size = s;
        arr = new int[s];
    }
    
    void enqueue(int x) {
        if(rear == size) {
            cout << "Queue Overflow\n";
            return;
        }
        arr[rear++] = x;
    }
    
    void dequeue() {
        if(front == rear) {
            cout << "Queue Underflow\n";
            return;
        }
        front++;
    }
    
    void display() {
        if(front == rear) {
            cout << "Queue is Empty\n";
            return;
        }
        for(int i = front; i < rear; i++) {
            cout << arr[i] << " ";
        }
        cout << endl;
    }
};

int main() {
    Queue q(5);
    
    q.enqueue(10);
    q.enqueue(20);
    q.enqueue(30);
    
    q.display();
    q.dequeue();
    q.display();
    
    return 0;
}
```

7. **Write a program to create a node in a linked list:**

```cpp
#include<iostream>
using namespace std;

class Node {
public:
    int data;
    Node* next;
};

int main() {
    Node* head = nullptr;
    Node* first = new Node();
    
    first->data = 10;
    first->next = nullptr;
    head = first;
    
    cout << "Node created with value: " << head->data << endl;
    
    return 0;
}
```

8. **Any one DP problem (Coin Change Problem):**

```cpp
#include<iostream>
using namespace std;

int coinChange(int coins[], int n, int amount) {
    int dp[amount+1];
    dp[0] = 0;
    
    for(int i = 1; i <= amount; i++)
        dp[i] = amount + 1;
    
    for(int i = 1; i <= amount; i++) {
        for(int j = 0; j < n; j++) {
            if(coins[j] <= i) {
                dp[i] = min(dp[i], dp[i - coins[j]] + 1);
            }
        }
    }
    
    return dp[amount] > amount ? -1 : dp[amount];
}

int main() {
    int coins[] = {1, 2, 5};
    int amount = 11;
    
    cout << "Fewest coins needed: " << coinChange(coins, 3, amount) << endl;
    
    return 0;
}
```

9. **Write a program in C to count the total number of alphabets, digits, and special characters in a string:**

```cpp
#include<iostream>
using namespace std;

int main() {
    string s;
    cout << "Enter a string: ";
    getline(cin, s);
    
    int alphabets = 0, digits = 0, special = 0;
    
    for(char c : s) {
        if(isalpha(c))
            alphabets++;
        else if(isdigit(c))
            digits++;
        else
            special++;
    }
    
    cout << "Alphabets: " << alphabets << endl;
    cout << "Digits: " << digits << endl;
    cout << "Special characters: " << special << endl;
    
    return 0;
}
```

10. **Binary Search Tree:**

```cpp
#include<iostream>
using namespace std;

class Node {
public:
    int data;
    Node* left;
    Node* right;
    
    Node(int value) {
        data = value;
        left = right = nullptr;
    }
};

class BST {
    Node* root;
    
    Node* insert(Node* node, int value) {
        if(node == nullptr)
            return new Node(value);
        
        if(value < node->data)
            node->left = insert(node->left, value);
        else if(value > node->data)
            node->right = insert(node->right, value);
        
        return node;
    }
    
public:
    BST() { root = nullptr; }
    
    void insert(int value) {
        root = insert(root, value);
    }
    
    void inorder(Node* node) {
        if(node == nullptr)
            return;
        
        inorder(node->left);
        cout << node->data << " ";
        inorder(node->right);
    }
    
    void display() {
        inorder(root);
    }
};

int main() {
    BST tree;
    tree.insert(50);
    tree.insert(30);
    tree.insert(20);
    tree.insert(40);
    tree.insert(70);
    tree.insert(60);
    tree.insert(80);
    
    cout << "Inorder traversal: ";
    tree.display();
    
    return 0;
}
```

Let me know if you need any further modifications or explanations!