public class File {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter the number of subjects:");
        int numSubjects = scanner.nextInt();
        scanner.nextLine(); // Consume the newline character

        String[] subjectNames = new String[numSubjects];
        int[] marks = new int[numSubjects];

        for (int i = 0; i < numSubjects; i++) {
            System.out.println("Enter the name of subject " + (i + 1) + ":");
            subjectNames[i] = scanner.nextLine();

            System.out.println("Enter the marks of " + subjectNames[i] + ":");
            marks[i] = scanner.nextInt();
            scanner.nextLine(); // Consume the newline character
        }

        int totalMarks = calculateTotalMarks(marks);
        double averagePercentage = calculateAveragePercentage(totalMarks, numSubjects);
        String grade = calculateGrade(averagePercentage);

        displayResults(totalMarks, averagePercentage, grade, subjectNames, marks);
    }

    private static int calculateTotalMarks(int[] marks) {
        int totalMarks = 0;
        for (int mark : marks) {
            totalMarks += mark;
        }
        return totalMarks;
    }

    private static double calculateAveragePercentage(int totalMarks, int numSubjects) {
        return (double) totalMarks / numSubjects;
    }

    private static String calculateGrade(double averagePercentage) {
        if (averagePercentage >= 90) {
            return "A";
        } else if (averagePercentage >= 80) {
            return "B";
        } else if (averagePercentage >= 70) {
            return "C";
        } else if (averagePercentage >= 60) {
            return "D";
        } else if (averagePercentage >= 40) {
            return "E";
        } else {
            return "F";
        }
    }

    private static void displayResults(int totalMarks, double averagePercentage, String grade, String[] subjectNames, int[] marks) {
        System.out.println("Total Marks: " + totalMarks);
        System.out.println("Average Percentage: " + averagePercentage);
        System.out.println("Grade: " + grade);
        System.out.println("Subject-wise Marks:");
        for (int i = 0; i < subjectNames.length; i++) {
            System.out.println(subjectNames[i] + ": " + marks[i]);
        }
    }
}

