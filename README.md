# project_-49
#include <stdio.h>
#include <string.h>

#define MAX_STUDENTS 100

typedef struct {
    int id;
    char name[50];
    int age;
    float grade;
} Student;

Student students[MAX_STUDENTS];
int studentCount = 0;

// Function to add a student
void addStudent() {
    if (studentCount < MAX_STUDENTS) {
        printf("Enter Student ID: ");
        scanf("%d", &students[studentCount].id);
        printf("Enter Student Name: ");
        scanf(" %[^\n]", students[studentCount].name);
        printf("Enter Student Age: ");
        scanf("%d", &students[studentCount].age);
        printf("Enter Student Grade: ");
        scanf("%f", &students[studentCount].grade);

        studentCount++;
        printf("Student added successfully!\n");
    } else {
        printf("Student list is full.\n");
    }
}

// Function to view all students
void viewStudents() {
    if (studentCount == 0) {
        printf("No students available.\n");
    } else {
        printf("\nStudent Records:\n");
        for (int i = 0; i < studentCount; i++) {
            printf("ID: %d, Name: %s, Age: %d, Grade: %.2f\n",
                   students[i].id, students[i].name, students[i].age, students[i].grade);
        }
    }
}

// Function to search for a student by ID
void searchStudent() {
    int searchID;
    printf("Enter Student ID to search: ");
    scanf("%d", &searchID);

    int found = 0;
    for (int i = 0; i < studentCount; i++) {
        if (students[i].id == searchID) {
            printf("\nFound Student:\n");
            printf("ID: %d, Name: %s, Age: %d, Grade: %.2f\n",
                   students[i].id, students[i].name, students[i].age, students[i].grade);
            found = 1;
            break;
        }
    }

    if (!found) {
        printf("Student not found.\n");
    }
}

// Function to delete a student by ID
void deleteStudent() {
    int deleteID;
    printf("Enter Student ID to delete: ");
    scanf("%d", &deleteID);

    int found = 0;
    for (int i = 0; i < studentCount; i++) {
        if (students[i].id == deleteID) {
            for (int j = i; j < studentCount - 1; j++) {
                students[j] = students[j + 1];
            }
            studentCount--;
            printf("Student deleted successfully!\n");
            found = 1;
            break;
        }
    }

    if (!found) {
        printf("Student not found.\n");
    }
}

int main() {
    int choice;
    do {
        printf("\nStudent Management System\n");
        printf("1. Add Student\n");
        printf("2. View Students\n");
        printf("3. Search Student\n");
        printf("4. Delete Student\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
        case 1:
            addStudent();
            break;
        case 2:
            viewStudents();
            break;
        case 3:
            searchStudent();
            break;
        case 4:
            deleteStudent();
            break;
        case 5:
            printf("Exiting Student Management System. Goodbye!\n");
            break;
        default:
            printf("Invalid choice! Please try again.\n");
        }
    } while (choice != 5);

    return 0;
}
