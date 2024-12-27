#include <stdio.h>
#include <string.h>

#define MAX_STUDENTS 50

// Structure to hold student details
struct Student {
    char name[50];
    int rollNumber;
    int present;  // 1 for present, 0 for absent
};

// Function to mark attendance
void markAttendance(struct Student students[], int n) {
    for (int i = 0; i < n; i++) {
        printf("Is %s (Roll No: %d) present? (1 for Yes, 0 for No): ", students[i].name, students[i].rollNumber);
        scanf("%d", &students[i].present);
    }
}

// Function to display attendance
void displayAttendance(struct Student students[], int n) {
    printf("\nAttendance Report:\n");
    printf("------------------------------------------------\n");
    printf("Name\t\tRoll No\t\tAttendance\n");
    printf("------------------------------------------------\n");
    for (int i = 0; i < n; i++) {
        printf("%s\t\t%d\t\t%s\n", students[i].name, students[i].rollNumber, students[i].present ? "Present" : "Absent");
    }
}

int main() {
    int n;

    // Input number of students
    printf("Enter the number of students: ");
    scanf("%d", &n);

    // Array to hold student details
    struct Student students[MAX_STUDENTS];

    // Input student details
    for (int i = 0; i < n; i++) {
        printf("\nEnter details for student %d\n", i + 1);
        printf("Name: ");
        getchar();  // To consume the newline character left by previous input
        fgets(students[i].name, 50, stdin);
        students[i].name[strcspn(students[i].name, "\n")] = 0;  // Remove trailing newline

        printf("Roll Number: ");
        scanf("%d", &students[i].rollNumber);
    }

    // Mark attendance
    markAttendance(students, n);

    // Display attendance
    displayAttendance(students, n);

    return 0;
}
