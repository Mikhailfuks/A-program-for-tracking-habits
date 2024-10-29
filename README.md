import java.time.LocalDate;

public class Habit {
    private String name;
    private boolean isCompleted;
    private LocalDate completionDate;

    public Habit(String name) {
        this.name = name;
        this.isCompleted = false;
    }

    public String getName() {
        return name;
    }

    public boolean isCompleted() {
        return isCompleted;
    }

    public void markAsCompleted() {
        this.isCompleted = true;
        this.completionDate = LocalDate.now(); // Sets the completion date to today
    }

    @Override
    public String toString() {
        return "Habit{" +
                "name='" + name + '\'' +
                ", isCompleted=" + isCompleted +
                ", completionDate=" + (isCompleted ? completionDate : "Not completed") +
                '}';
    }
}

import java.util.ArrayList;
import java.util.List;

public class HabitTracker {
    private List<Habit> habits;

    public HabitTracker() {
        habits = new ArrayList<>();
    }

    public void addHabit(String name) {
        habits.add(new Habit(name));
        System.out.println("Habit added: " + name);
    }

    public void completeHabit(String name) {
        for (Habit habit : habits) {
            if (habit.getName().equalsIgnoreCase(name)) {
                habit.markAsCompleted();
                System.out.println("Habit marked as completed: " + habit);
                return;
            }
        }
        System.out.println("Habit not found: " + name);
    }

    public void removeHabit(String name) {
        habits.removeIf(habit -> habit.getName().equalsIgnoreCase(name));
        System.out.println("Habit removed: " + name);
    }

    public void displayHabits() {
        System.out.println("Habit Tracker:");
        for (Habit habit : habits) {
            System.out.println(habit);
        }
    }
}


                    System.out.print("Enter habit name to mark as completed: ");
                    String habitNameToComplete = scanner.nextLine();
                    habitTracker.completeHabit(habitNameToComplete);
                    break;

                case 3:
                    System.out.print("Enter habit name to remove: ");
                    String habitNameToRemove = scanner.nextLine();
                    habitTracker.removeHabit(habitNameToRemove);
                    break;

                case 4:
                    habitTracker.displayHabits();
                    break;

                case 5:
                    System.out.println("Exiting...");
                    scanner.close();
                    return;

                default:
                    System.out.println("Invalid choice. Please choose again.");
            }
        }
    }
}
