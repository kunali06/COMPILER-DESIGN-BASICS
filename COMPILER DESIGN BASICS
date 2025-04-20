#include <iostream>
#include <string>
#include <cctype>

using namespace std;

string input;
int pos = 0;

// Forward declarations
int expr();

void skipWhitespace() {
    while (isspace(input[pos])) pos++;
}

int number() {
    skipWhitespace();
    int result = 0;
    while (isdigit(input[pos])) {
        result = result * 10 + (input[pos] - '0');
        pos++;
    }
    return result;
}

int factor() {
    skipWhitespace();
    if (input[pos] == '(') {
        pos++; // skip '('
        int result = expr();
        if (input[pos] == ')') {
            pos++; // skip ')'
        } else {
            cout << "Error: Expected ')' at position " << pos << endl;
            exit(1);
        }
        return result;
    } else if (isdigit(input[pos])) {
        return number();
    } else {
        cout << "Error: Unexpected character '" << input[pos] << "' at position " << pos << endl;
        exit(1);
    }
}

int term() {
    int result = factor();
    while (true) {
        skipWhitespace();
        if (input[pos] == '*') {
            pos++;
            result *= factor();
        } else if (input[pos] == '/') {
            pos++;
            int divisor = factor();
            if (divisor == 0) {
                cout << "Error: Division by zero." << endl;
                exit(1);
            }
            result /= divisor;
        } else {
            break;
        }
    }
    return result;
}

int expr() {
    int result = term();
    while (true) {
        skipWhitespace();
        if (input[pos] == '+') {
            pos++;
            result += term();
        } else if (input[pos] == '-') {
            pos++;
            result -= term();
        } else {
            break;
        }
    }
    return result;
}

int main() {
    cout << "Enter an arithmetic expression (e.g., 2 + 3 * (4 - 1)): ";
    getline(cin, input);
    int result = expr();
    skipWhitespace();
    if (pos != input.length()) {
        cout << "Error: Unexpected characters at the end of expression." << endl;
        return 1;
    }
    cout << "Result: " << result << endl;
    return 0;
}
