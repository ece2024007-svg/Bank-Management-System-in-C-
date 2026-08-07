#include <iostream>
#include <fstream>
#include <string>
using namespace std;

class BankAccount
{
private:
    int accountNo;
    string name;
    float balance;

public:
    void createAccount()
    {
        cout << "\nEnter Account Number: ";
        cin >> accountNo;
        cin.ignore();

        cout << "Enter Customer Name: ";
        getline(cin, name);

        cout << "Enter Initial Balance: ";
        cin >> balance;

        saveToFile();
        cout << "\nAccount Created Successfully!\n";
    }

    void saveToFile()
    {
        ofstream file("bank.txt", ios::app);
        file << accountNo << endl;
        file << name << endl;
        file << balance << endl;
        file.close();
    }

    void searchAccount(int acc)
    {
        ifstream file("bank.txt");

        int accNo;
        string customerName;
        float bal;

        bool found = false;

        while (file >> accNo)
        {
            file.ignore();
            getline(file, customerName);
            file >> bal;

            if (accNo == acc)
            {
                cout << "\nAccount Found\n";
                cout << "Name: " << customerName << endl;
                cout << "Balance: Rs. " << bal << endl;
                found = true;
                break;
            }
        }

        if (!found)
            cout << "\nAccount Not Found!\n";

        file.close();
    }

    void deposit(int acc, float amount)
    {
        ifstream file("bank.txt");
        ofstream temp("temp.txt");

        int accNo;
        string customerName;
        float bal;

        while (file >> accNo)
        {
            file.ignore();
            getline(file, customerName);
            file >> bal;

            if (accNo == acc)
                bal += amount;

            temp << accNo << endl;
            temp << customerName << endl;
            temp << bal << endl;
        }

        file.close();
        temp.close();

        remove("bank.txt");
        rename("temp.txt", "bank.txt");

        cout << "\nDeposit Successful!\n";
    }

    void withdraw(int acc, float amount)
    {
        ifstream file("bank.txt");
        ofstream temp("temp.txt");

        int accNo;
        string customerName;
        float bal;

        while (file >> accNo)
        {
            file.ignore();
            getline(file, customerName);
            file >> bal;

            if (accNo == acc)
            {
                if (bal >= amount)
                    bal -= amount;
                else
                    cout << "\nInsufficient Balance!\n";
            }

            temp << accNo << endl;
            temp << customerName << endl;
            temp << bal << endl;
        }

        file.close();
        temp.close();

        remove("bank.txt");
        rename("temp.txt", "bank.txt");

        cout << "\nWithdrawal Completed!\n";
    }
};

int main()
{
    BankAccount bank;

    int choice, acc;
    float amount;

    do
    {
        cout << "\n====== BANK MANAGEMENT SYSTEM ======\n";
        cout << "1. Create Account\n";
        cout << "2. Deposit Money\n";
        cout << "3. Withdraw Money\n";
        cout << "4. Balance Check\n";
        cout << "5. Exit\n";

        cout << "Enter Choice: ";
        cin >> choice;

        switch (choice)
        {
        case 1:
            bank.createAccount();
            break;

        case 2:
            cout << "Enter Account Number: ";
            cin >> acc;
            cout << "Enter Amount: ";
            cin >> amount;
            bank.deposit(acc, amount);
            break;

        case 3:
            cout << "Enter Account Number: ";
            cin >> acc;
            cout << "Enter Amount: ";
            cin >> amount;
            bank.withdraw(acc, amount);
            break;

        case 4:
            cout << "Enter Account Number: ";
            cin >> acc;
            bank.searchAccount(acc);
            break;

        case 5:
            cout << "Thank You!\n";
            break;

        default:
            cout << "Invalid Choice!\n";
        }

    } while (choice != 5);

    return 0;
}
