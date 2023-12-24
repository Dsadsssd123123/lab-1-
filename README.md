#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

class Phone {
private:
    string lastName;
    string firstName;
    string patronymic;
    string address;
    string number;
    int intraCityTime; 
    int interCityTime; 

public:
    
    Phone(string last, string first, string patr, string addr, string num, int intra, int inter) {
        lastName = last;
        firstName = first;
        patronymic = patr;
        address = addr;
        number = num;
        intraCityTime = intra;
        interCityTime = inter;
    }

    
    int getIntraCityTime() const {
        return intraCityTime;
    }

    int getInterCityTime() const {
        return interCityTime;
    }

    
    void displayInfo() const {
        cout << "Прізвище: " << lastName << endl;
        cout << "Ім'я: " << firstName << endl;
        cout << "По-батькові: " << patronymic << endl;
        cout << "Адреса: " << address << endl;
        cout << "Номер: " << number << endl;
        cout << "Час внутрішньоміських розмов: " << intraCityTime << endl;
        cout << "Час міжміських розмов: " << interCityTime << endl;
        cout << "-------------------------------------" << endl;
    }

   
    bool operator<(const Phone &other) const {
        return lastName < other.lastName;
    }
};

int main() {
    const int arraySize = 3; 

    
    Phone phones[arraySize] = {
        Phone("Іванов", "Іван", "Іванович", "Київ", "111-11-11", 50, 20),
        Phone("Петров", "Петро", "Петрович", "Львів", "222-22-22", 30, 40),
        Phone("Сидоров", "Олег", "Васильович", "Одеса", "333-33-33", 10, 60)
    };

    int thresholdIntraCityTime = 20; 

   
    cout << "Абоненти з часом внутрішньоміських розмов більше " << thresholdIntraCityTime << " хвилин:" << endl;
    for (int i = 0; i < arraySize; ++i) {
        if (phones[i].getIntraCityTime() > thresholdIntraCityTime) {
            phones[i].displayInfo();
        }
    }

    
    cout << "Абоненти, які скористалися міжміським зв'язком:" << endl;
    for (int i = 0; i < arraySize; ++i) {
        if (phones[i].getInterCityTime() > 0) {
            phones[i].displayInfo();
        }
    }

    
    cout << "Абоненти, виведені в алфавітному порядку:" << endl;
    sort(phones, phones + arraySize); 
  
    for (int i = 0; i < arraySize; ++i) {
        phones[i].displayInfo();
    }

    return 0;
}
