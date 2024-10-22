# miniproject-Phone-Book-
this mini project is help to add name and their contact using dsa topic like searching,finding,etc.usingc++
#include <iostream>
#include <string>
#include <vector>

using namespace std;

class Contact {
public:
    string name;
    string phone;

    Contact(string name, string phone) {
        this->name = name;
        this->phone = phone;
    }
};

class PhoneBook {
private:
    vector<Contact> contacts;

public:
    void addContact(string name, string phone) {
        contacts.push_back(Contact(name, phone));
        cout << "Contact added successfully!" << endl;
    }

    void displayContacts() {
        if (contacts.empty()) {
            cout << "Phone book is empty!" << endl;
            return;
        }

        cout << "List of Contacts:" << endl;
        for (size_t i = 0; i < contacts.size(); i++) {
            cout << i + 1 << ". Name: " << contacts[i].name << ", Phone: " << contacts[i].phone << endl;
        }
    }

    void searchContact(string name) {
        bool found = false;
        for (size_t i = 0; i < contacts.size(); i++) {
            if (contacts[i].name == name) {
                cout << "Contact found: Name: " << contacts[i].name << ", Phone: " << contacts[i].phone << endl;
                found = true;
                break;
            }
        }
        if (!found) {
            cout << "Contact not found!" << endl;
        }
    }

    void updateContact(string oldName, string newName, string newPhone) {
        bool found = false;
        for (size_t i = 0; i < contacts.size(); i++) {
            if (contacts[i].name == oldName) {
                contacts[i].name = newName;
                contacts[i].phone = newPhone;
                cout << "Contact updated successfully!" << endl;
                found = true;
                break;
            }
        }
        if (!found) {
            cout << "Contact not found!" << endl;
        }
    }

    void deleteContact(string name) {
        bool found = false;
        for (size_t i = 0; i < contacts.size(); i++) {
            if (contacts[i].name == name) {
                contacts.erase(contacts.begin() + i);
                cout << "Contact deleted successfully!" << endl;
                found = true;
                break;
            }
        }
        if (!found) {
            cout << "Contact not found!" << endl;
        }
    }
};

int main() {
    PhoneBook phoneBook;
    int choice;
    string name, phone, newName, newPhone;

    do {
        cout << "\nPhone Book Menu:\n";
        cout << "1. Add Contact\n";
        cout << "2. Display Contacts\n";
        cout << "3. Search Contact\n";
        cout << "4. Update Contact\n";
        cout << "5. Delete Contact\n";
        cout << "0. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
        case 1:
            cout << "Enter Name: ";
            cin >> name;
            cout << "Enter Phone Number: ";
            cin >> phone;
            phoneBook.addContact(name, phone);
            break;

        case 2:
            phoneBook.displayContacts();
            break;

        case 3:
            cout << "Enter Name to Search: ";
            cin >> name;
            phoneBook.searchContact(name);
            break;

        case 4:
            cout << "Enter Name of Contact to Update: ";
            cin >> name;
            cout << "Enter New Name: ";
            cin >> newName;
            cout << "Enter New Phone Number: ";
            cin >> newPhone;
            phoneBook.updateContact(name, newName, newPhone);
            break;

        case 5:
            cout << "Enter Name of Contact to Delete: ";
            cin >> name;
            phoneBook.deleteContact(name);
            break;

        case 0:
            cout << "Exiting..." << endl;
            break;

        default:
            cout << "Invalid choice! Please try again." << endl;
        }
    } while (choice != 0);

    return 0;
}

