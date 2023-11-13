import java.util.Scanner;

class FitnessApp {
    public static void main(String[] args) {
        // Initialize the fitness app
        AI ai = new AI();
        CalorieTracker calorieTracker = new CalorieTracker();
        MovementTracker movementTracker = new MovementTracker();
        GymMap gymMap = new GymMap();

        Scanner scanner = new Scanner(System.in);

        // Main app loop
        boolean running = true;
        while (running) {
            System.out.println("Welcome to FitnessApp! How can I assist you?");
            System.out.println("1. Ask a fitness-related question");
            System.out.println("2. Track calorie intake");
            System.out.println("3. Track movement");
            System.out.println("4. Find nearby gyms");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // Clear the newline character

            switch (choice) {
                case 1:
                    System.out.print("Question: ");
                    String question = scanner.nextLine();
                    String answer = ai.answerQuestion(question);
                    System.out.println("AI: " + answer);
                    break;
                case 2:
                    System.out.print("Enter the calorie intake: ");
                    int calories = scanner.nextInt();
                    scanner.nextLine(); // Clear the newline character
                    calorieTracker.trackCalories(calories);
                    break;
                case 3:
                    System.out.print("Enter the number of steps: ");
                    int steps = scanner.nextInt();
                    scanner.nextLine(); // Clear the newline character
                    movementTracker.trackMovement(steps);
                    break;
                case 4:
                    System.out.println("Nearby gyms: ");
                    gymMap.displayGyms();
                    break;
                case 5:
                    running = false;
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
                    break;
            }
            System.out.println(); // Add an empty line for clarity
        }

        scanner.close();
    }
}

class AI {
    public String answerQuestion(String question) {
        // Perform logic to answer fitness-related questions
        // Example: You can provide a pre-defined set of answers based on common questions
        if (question.equalsIgnoreCase("What is the best exercise for weight loss?")) {
            return "Cardio exercises like running, cycling, or swimming are effective for weight loss.";
        } else if (question.equalsIgnoreCase("How many days a week should I workout?")) {
            return "For optimal results, aim for at least 3-4 days of exercise per week.";
        } else {
            return "I'm sorry, I don't have an answer for that question.";
        }
    }
}

class CalorieTracker {
    private int totalCalories;

    public void trackCalories(int calories) {
        totalCalories += calories;
        System.out.println("Calorie intake tracked: " + calories + " calories");
        System.out.println("Total calories: " + totalCalories + " calories");
    }
}

class MovementTracker {
    private int totalSteps;

    public void trackMovement(int steps) {
        totalSteps += steps;
        System.out.println("Movement tracked: " + steps + " steps");
        System.out.println("Total steps: " + totalSteps + " steps");
    }
}

class GymMap {
    public void displayGyms() {
        // Fetch and display nearby gyms using the map API
        // Example: You can use Google Maps API or any other map service

        // Dummy gyms for demonstration purposes
        String[] gyms = { "Gym A", "Gym B", "Gym C" };

        for (String gym : gyms) {
            System.out.println(gym);
        }
    }
}
