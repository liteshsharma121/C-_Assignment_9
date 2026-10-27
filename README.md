
#include <iostream>
#include <string>
#include <utility>
using namespace std;

class Employee {
private:
    string name;

public:
    Employee(string n) : name(std::move(n)) {
        cout << "Constructor called." << endl;
    }

    Employee(Employee&& obj) noexcept
        : name(std::move(obj.name)) {
        obj.name.clear();
        cout << "Move constructor called." << endl;
    }

    void display() {
        cout << "Name: " << name << endl;
    }
};

int main() {
    cout << "Creating first object:" << endl;
    Employee e1("Amit");

    cout << "\nFirst object:" << endl;
    e1.display();

    cout << "\nMoving data to second object:" << endl;
    Employee e2(std::move(e1));

    cout << "\nSecond object after move:" << endl;
    e2.display();

    cout << "\nFirst object after move:" << endl;
    e1.display();

    return 0;
}
