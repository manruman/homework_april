#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;

int gcd(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

int lcm(int a, int b) {
    return a / gcd(a, b) * b;
}

int main() {
    srand(time(0)); 

    cout << "Welcome to the Brain Games!" << endl;
    cout << "May I have your name? ";
    string name;
    cin >> name;
    cout << "Hello, " << name << "!" << endl;
    cout << "Find the smallest common multiple of given numbers." << endl;

    for (int i = 0; i < 3; ++i) {
        int num1 = rand() % 20 + 1; 
        int num2 = rand() % 20 + 1;
        int num3 = rand() % 20 + 1;

        cout << "Question: " << num1 << " " << num2 << " " << num3 << endl;

        int answer = lcm(lcm(num1, num2), num3);

        int userAnswer;
        cout << "Your answer: ";
        cin >> userAnswer;

        if (userAnswer == answer) {
            cout << "Correct!" << endl;
        } else {
            cout << "'" << userAnswer << "' is wrong answer ;(. Correct answer was '" << answer << "'." << endl;
            cout << "Let's try again, " << name << "!" << endl;
            return 0;
        }
    }

    cout << "Congratulations, " << name << "!" << endl;
    return 0;
}
