#include <iostream>
using namespace std;
class HospitalFunctions {
public:
  virtual void show_patient() = 0;
  virtual void Patient_condition() = 0;
   
};
class HospitalSystem : public HospitalFunctions {
public:
    string patient_name;
    int patient_age, patient_id;
    string disease;
    string doctor_name;
    int case_type;
    int room_number;
    HospitalSystem(string name, int age, string dis, string dn, int ct, int rn, int id) {
        patient_name = name;
        patient_age = age;
        disease = dis;
        doctor_name = dn;
        case_type = ct;
        room_number = rn;
        patient_id = id;
    }
    void show_patient() {
        cout << "Patient Name: " << patient_name << endl;
        cout << "Patient Age: " << patient_age << endl;
        cout << "Disease: " << disease << endl;
        cout << "Doctor Name: " << doctor_name << endl;
        cout << "Case Type: " << case_type << endl;
        cout << "Room Number: " << room_number << endl;
        cout << "-----------------------------" << endl;
    }
    void Patient_condition() {//100:80 risk  70:50 normal 50:0 Under test
        if (case_type >= 80) {
            cout << "It requires an excision operation." << endl;
            cout << "+++++++++++++++++++++++++++++++++";
        }
        else if (case_type >= 50) {
            cout << "Contact for chemotherapy" << endl;
            cout << "+++++++++++++++++++++++++++++++++";
        }
        else {
            cout << "He needs tests" << endl;
            cout << "+++++++++++++++++++++++++++++++++";
        }
    }
};
int main() {
    HospitalSystem s1 = HospitalSystem("ahmed ali",56,"cancer","omer ahmed",80,40,5);
    HospitalSystem s2 = HospitalSystem("moheed omer",60,"Stomach cancer","assme kheld",70, 41,1);
    HospitalSystem s3 = HospitalSystem("amr youssef",62,"Leukemia","ahmed hassen",40,45,2);
    HospitalSystem s4 = HospitalSystem("amir ahmed",55,"Thyroid cancer","omer ahmed",20,44,3);
    int choice,id_pn;
    do {
        cout << "\n===== Hospital System Menu =====\n";
        cout << "1- information of patient Case\n";
        cout << "2- patient Case\n";
        cout << "3- Exit\n";
        cout << "Choose option: ";
        cin >> choice;
        if (choice == 3) {
            cout << "Exiting system... Stay safe\n";
            break;
        }
        cout << "plese enter id of patient: ";
        cin >> id_pn;
        cout << "_______________________________________________________\n";
        switch (choice) {
        case 1:
            switch (id_pn) {
            case 5:
                s1.show_patient();
                break;
            case 1:
                s2.show_patient();
                break;
            case 2:
                s3.show_patient();
                break;
            case 3:
                s4.show_patient();
                break;
            default:
                cout << "Invalid choice! Try again.\n";
            }
            break;
        case 2:
            switch (id_pn) {
            case 5:
                s1.Patient_condition();
                break;
            case 1:
                s2.Patient_condition();
                break;
            case 2:
                s3.Patient_condition();
                break;
            case 3:
                s4.Patient_condition();
                break;
            default:
                cout << "Invalid choice! Try again.\n";
            }
            break;
        default:
            cout << "Invalid choice! Try again.\n";
        }
    } while (1);
    return 0;
}

