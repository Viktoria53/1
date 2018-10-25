#include <iostream>
#include <vector>

using namespace std;

struct Base {
    string from;
    string to;
    string date;
    string time;
    int duration;

    void print() {
        cout << from << "\t" << to << "\t" << date << "\t" << time << "\t" << duration << endl;
    }
};

int main() {
    vector<Base> myList;

    myList.push_back({"Петя", "Вася", "24.10.2018", "13:07", 14});
    myList.push_back({"Маша", "Вася", "24.10.2018", "13:51", 9});
    myList.push_back({"Петя", "Катя", "24.10.2018", "13:56", 26});
    myList.push_back({"Катя", "Маша", "24.10.2018", "14:50", 40});


    //сортировка по длительности
    for (int i = 0; i < myList.size() - 1; i++) {
        for (int j = 0; j < myList.size() - i - 1; j++) {
            if (myList[j].duration > myList[j + 1].duration) std::swap(myList[j], myList[j + 1]);
        }
    }

    //вывод
    for (int i = 0; i < myList.size(); i++)
        myList[i].print();


    //поиск по имени
    string name;
    cout << "Введите имя: ";
    cin >> name;

    for (int i = 0; i < myList.size(); i++) {
        if (myList[i].from == name or myList[i].to == name) {
            myList[i].print();
        }
    }

    //поиск по дате
    string date;
    cout << "Введите дату: ";
    cin >> date;

    for (int i = 0; i < myList.size(); i++) {
        if (myList[i].date == date) {
            myList[i].print();
        }
    }

    //поиск по длительности
    double duration;
    cout << "Введите длительность: ";
    cin >> duration;

    for (int i = 0; i < myList.size(); i++) {
        if (myList[i].duration == duration) {
            myList[i].print();
        }
    }

    return 0;
}
