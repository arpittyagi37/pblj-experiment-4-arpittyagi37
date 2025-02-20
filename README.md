
QUE 1 write a java program to implement an array list that store employee details (ID,name,Salary). Allow user to (add,update,remove and search) employee

import java.util.ArrayList;
import java.util.Scanner;

class Employee {
    int id;
    String name;
    double salary;

   Employee(int id, String name, double salary) {
        this.id = id;
        this.name = name;
        this.salary = salary;
    }

  @Override
    public String toString() {
        return id + " " + name + " " + salary;
    }
}

public class EmployeeManager {
    static ArrayList<Employee> employees = new ArrayList<>();
    static Scanner scanner = new Scanner(System.in);

  public static void main(String[] args) {
        while (true) {
            System.out.println("1. Add 2. Update 3. Remove 4. Search 5. Exit");
            int choice = scanner.nextInt();
            switch (choice) {
                case 1: addEmployee(); break;
                case 2: updateEmployee(); break;
                case 3: removeEmployee(); break;
                case 4: searchEmployee(); break;
                case 5: System.exit(0);
            }
        }
    }

   static void addEmployee() {
        System.out.println("Enter ID, Name, Salary:");
        employees.add(new Employee(scanner.nextInt(), scanner.next(), scanner.nextDouble()));
    }

   static void updateEmployee() {
        System.out.println("Enter ID to update:");
        int id = scanner.nextInt();
        for (Employee emp : employees) {
            if (emp.id == id) {
                System.out.println("Enter new Name, Salary:");
                emp.name = scanner.next();
                emp.salary = scanner.nextDouble();
                return;
            }
        }
        System.out.println("Employee not found.");
    }
    
  static void removeEmployee() {
        System.out.println("Enter ID to remove:");
        int id = scanner.nextInt();
        employees.removeIf(emp -> emp.id == id);
    }

   static void searchEmployee() {
        System.out.println("Enter ID to search:");
        int id = scanner.nextInt();
        for (Employee emp : employees) {
            if (emp.id == id) {
                System.out.println(emp);
                return;
            }
        }
        System.out.println("Employee not found.");
    }
}


QUE 2  create a java program to collect and store all the cards to assist the user in finding all the cards in a given symbol using collection interface

import java.util.ArrayList;
import java.util.Collection;
import java.util.Scanner;

class Card {
    String symbol;
    String value;

   Card(String symbol, String value) {
        this.symbol = symbol;
        this.value = value;
    }

  @Override
    public String toString() {
        return value + " of " + symbol;
    }
}

public class CardCollection {
    static Collection<Card> cards = new ArrayList<>();
    static Scanner scanner = new Scanner(System.in);

  public static void main(String[] args) {
        addCards();
        System.out.println("Enter symbol to search:");
        String symbol = scanner.next();
        searchCardsBySymbol(symbol);
    }

   static void addCards() {
        cards.add(new Card("Hearts", "A"));
        cards.add(new Card("Spades", "K"));
        cards.add(new Card("Diamonds", "Q"));
        cards.add(new Card("Clubs", "J"));
        
    }

   static void searchCardsBySymbol(String symbol) {
        for (Card card : cards) {
            if (card.symbol.equalsIgnoreCase(symbol)) {
                System.out.println(card);
            }
        }
    }
}
