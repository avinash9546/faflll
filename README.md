# faflll


#include <iostream> 
#include <string> 
using namespace std; 
 
enum State { 
    S0, S1, S2, S3 
}; 
 
bool acceptsString(const string& input) { 
    State currentState = S0; 
 
    for (char c : input) { 
        switch (currentState) { 
            case S0: 
                if (c == '1') { 
                    currentState = S1; 
                } // else stay in S0 (on '0') 
                break; 
            case S1: 
                if (c == '1') { 
                    currentState = S2; 
                } else { 
                    currentState = S0; // on '0', go back to S0 
                } 
                break; 
            case S2: 
                if (c == '1') { 
                    currentState = S3; 
                } else { 
                    currentState = S0; // on '0', go back to S0 
                } 
                break; 
            case S3: 
                // Once we reach S3, we stay in S3 (accepting state) 
                break; 
        } 
    } 
    return currentState == S3; 
} 
 
int main() { 
    string input; 
    cout << "Enter a binary string: "; 
    cin >> input; 
 
    if (acceptsString(input)) { 
        cout << "Accepted (contains 111)" << endl; 
    } else { 
cout << "Rejected (does not contain 111)" << endl; 
} 
return 0; 
} 





#include <iostream> 
#include <string> 
using namespace std; 
enum State { 
S0, S1, S2 
}; 
bool isDivisibleBy3(const string& input) { 
State currentState = S0; // Start in state S0 (remainder = 0) 
for (char c : input) { 
switch (currentState) { 
case S0: 
if (c == '0') { 
currentState = S0; // Stay in S0 (remainder 0) 
} else if (c == '1') { 
currentState = S1; // Move to S1 (remainder 1) 
} 
break; 
case S1: 
if (c == '0') { 
currentState = S2; // Move to S2 (remainder 2) 
} else if (c == '1') { 
currentState = S0; // Move to S0 (remainder 0) 
} 
break; 
case S2: 
if (c == '0') { 
currentState = S1; // Move to S1 (remainder 1) 
} else if (c == '1') { 
currentState = S2; // Stay in S2 (remainder 2) 
} 
break; 
} 
} 
// Accept if the FSM ends in state S0 (remainder 0, divisible by 3) 
return currentState == S0; 
} 
int main() { 
string input; 
cout << "Enter a binary string: "; 
cin >> input; 
if (isDivisibleBy3(input)) { 
cout << "Accepted (the number is divisible by 3)" << endl; 
} else { 
cout << "Rejected (the number is not divisible by 3)" << endl; 
} 
return 0; 
}






#include <iostream> 
#include <string> 
using namespace std; 
enum State { 
S0, S1, S2 
}; 
bool isDivisibleBy3(const string& input) { 
State currentState = S0; // Start in state S0 (remainder = 0) 
for (char c : input) { 
if (c < '0' || c > '9') { 
cout << "Invalid input: Non-decimal character encountered!" << endl; 
            return false; 
        } 
 
        int digit = c - '0'; // Convert char to int (e.g., '3' -> 3) 
 
        switch (currentState) { 
            case S0: 
                currentState = static_cast<State>((0 * 10 + digit) % 3); 
                break; 
            case S1: 
                currentState = static_cast<State>((1 * 10 + digit) % 3); 
                break; 
            case S2: 
                currentState = static_cast<State>((2 * 10 + digit) % 3); 
                break; 
        } 
    } 
 
    // Accept if the FSM ends in state S0 (remainder 0, divisible by 3) 
    return currentState == S0; 
} 
 
int main() { 
    string input; 
    cout << "Enter a decimal string: "; 
    cin >> input; 
 
    if (isDivisibleBy3(input)) { 
        cout << "Accepted (the number is divisible by 3)" << endl; 
    } else { 
        cout << "Rejected (the number is not divisible by 3)" << endl; 
    } 
 
    return 0; 
}
