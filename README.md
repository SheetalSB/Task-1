# Task-1
*Project Title:* Task Management System  
*Description:* Implemented a simple console-based task management system in Java where users can add, remove, and list tasks. Each task includes a name, description, and due date. Utilized basic data structures such as arrays or ArrayLists for storage and implemented error handling for invalid input.  
*Technologies Used:* Java, basic data structures (arrays or ArrayLists)  
*Skills Demonstrated:* Java programming, data structures, error handling 

code :
import java.util.ArrayList;
import java.util.Scanner;

class Task {
    String name;
    String description;
    String dueDate;

    Task(String name, String description, String dueDate) {
        this.name = name;
        this.description = description;
        this.dueDate = dueDate;
    }
}

public class TaskManagementSystem {
    static ArrayList<Task> tasks = new ArrayList<>();

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("1. Add task");
            System.out.println("2. Remove task");
            System.out.println("3. List tasks");
            System.out.println("4. Exit");
            System.out.print("Choose an option: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline character

            switch (choice) {
                case 1:
                    addTask(scanner);
                    break;
                case 2:
                    removeTask(scanner);
                    break;
                case 3:
                    listTasks();
                    break;
                case 4:
                    System.out.println("Exiting...");
                    return;
                default:
                    System.out.println("Invalid option. Please choose again.");
            }
        }
    }

    private static void addTask(Scanner scanner) {
        System.out.print("Enter task name: ");
        String name = scanner.nextLine();
        System.out.print("Enter task description: ");
        String description = scanner.nextLine();
        System.out.print("Enter due date: ");
        String dueDate = scanner.nextLine();

        Task task = new Task(name, description, dueDate);
        tasks.add(task);
        System.out.println("Task added successfully.");
    }

    private static void removeTask(Scanner scanner) {
        if (tasks.isEmpty()) {
            System.out.println("No tasks to remove.");
            return;
        }
        System.out.println("Enter index of task to remove:");
        for (int i = 0; i < tasks.size(); i++) {
            System.out.println(i + ". " + tasks.get(i).name);
        }
        int index = scanner.nextInt();
        if (index >= 0 && index < tasks.size()) {
            tasks.remove(index);
            System.out.println("Task removed successfully.");
        } else {
            System.out.println("Invalid index.");
        }
    }

    private static void listTasks() {
        if (tasks.isEmpty()) {
            System.out.println("No tasks available.");
            return;
        }
        System.out.println("Tasks:");
        for (int i = 0; i < tasks.size(); i++) {
            Task task = tasks.get(i);
            System.out.println("Name: " + task.name);
            System.out.println("Description: " + task.description);
            System.out.println("Due Date: " + task.dueDate);
            System.out.println();
        }
    }
}
