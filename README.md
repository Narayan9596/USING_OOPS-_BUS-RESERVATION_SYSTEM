# USING_OOPS-_BUS-RESERVATION_SYSTEM
BUS RESERVATION SYSTEEM USING JAVA AND  OOPS  COONCEPT IT IS ALSO CONSIDER AS A MINI PROJECT FOR SECOND YEAR STUDENT 
import java.io.*;
import java.util.*;

public class BusReservationSystem {
    private static final String[] buses = {
            "janta bus  service ", "hubli bus service", "narayan bus service ", "mateen bus service", "Afnan bus serviceeus"
    };
    private static final String[] locations = {
            "Delhi", "Mumbai", "Kolkata", "Chennai", "Bangalore"
    };
    private static final String[] destinations = {
            "Jaipur", "Pune", "Hyderabad", "Lucknow", "Ahmedabad"
    };
    private static final String[][] passengerNames = new String[5][32];
    private static final boolean[][] seatAvailability = new boolean[5][32];
    private static final Scanner scanner = new Scanner(System.in);

  public static void main(String[] args) {
        login();
        int choice;
        do {
            System.out.println("\n====================================== WELCOME TO BUS RESERVATION SYSTEM ======================================");
            System.out.println("[1] View Bus List");
            System.out.println("[2] Book Tickets");
            System.out.println("[3] Cancel Booking");
            System.out.println("[4] Bus Status Board");
            System.out.println("[5] Exit");
            System.out.print("Enter Your Choice: ");
            choice = scanner.nextInt();
            switch (choice) {
                case 1 -> viewBusList();
                case 2 -> bookTickets();
                case 3 -> cancelBooking();
                case 4 -> busStatusBoard();
                case 5 -> System.out.println("Thank you for using the Bus Reservation System!");
                default -> System.out.println("Invalid choice! Please try again.");
            }
        } while (choice != 5);
    }

   private static void login() {
        String username = "user";
        String password = "pass";
        int attempts = 0;

   while (attempts < 3) {
            System.out.print("Enter username: ");
            String inputUsername = scanner.next();
            System.out.print("Enter password: ");
            String inputPassword = scanner.next();

 if (username.equals(inputUsername) && password.equals(inputPassword)) {
                System.out.println("Login successful!\n");
                return;
            } else {
                System.out.println("Incorrect username or password. Try again.");
                attempts++;
            }
        }

 System.out.println("Too many failed login attempts. Exiting.");
        System.exit(0);
    }

private static void viewBusList() {
        System.out.println("\n==================== BUS LIST ====================");
        for (int i = 0; i < buses.length; i++) {
            System.out.printf("[%d] %s (From: %s, To: %s)\n", i + 1, buses[i], locations[i], destinations[i]);
        }
    }

 private static void bookTickets() {
        viewBusList();
        System.out.print("Enter the bus number: ");
        int busNumber = scanner.nextInt() - 1;

  if (busNumber < 0 || busNumber >= buses.length) {
            System.out.println("Invalid bus number!");
            return;
        }

  System.out.println("You selected: " + buses[busNumber]);
        System.out.println("Route: From " + locations[busNumber] + " To " + destinations[busNumber]);
        System.out.print("Enter the number of tickets: ");
        int tickets = scanner.nextInt();

  if (tickets <= 0 || tickets > availableSeats(busNumber)) {
            System.out.println("Invalid number of tickets or insufficient seats available.");
            return;
        }

  for (int i = 0; i < tickets; i++) {
            System.out.print("Enter seat number (1-32): ");
            int seat = scanner.nextInt() - 1;

   if (seat < 0 || seat >= 32 || seatAvailability[busNumber][seat]) {
                System.out.println("Invalid or already booked seat number. Try again.");
                i--;
                continue;
            }

  System.out.print("Enter passenger name: ");
            scanner.nextLine(); // consume newline
            String name = scanner.nextLine();

   passengerNames[busNumber][seat] = name;
            seatAvailability[busNumber][seat] = true;
        }

 System.out.println("Booking successful! Total amount: " + (tickets * 200));
    }

private static int availableSeats(int busNumber) {
        int count = 0;
        for (boolean seat : seatAvailability[busNumber]) {
            if (!seat) count++;
        }
        return count;
    }

private static void cancelBooking() {
        viewBusList();
        System.out.print("Enter the bus number: ");
        int busNumber = scanner.nextInt() - 1;

  if (busNumber < 0 || busNumber >= buses.length) {
            System.out.println("Invalid bus number!");
            return;
        }

   System.out.print("Enter the seat number to cancel (1-32): ");
        int seat = scanner.nextInt() - 1;

  if (seat < 0 || seat >= 32 || !seatAvailability[busNumber][seat]) {
            System.out.println("Invalid or unbooked seat number.");
            return;
        }

   passengerNames[busNumber][seat] = null;
        seatAvailability[busNumber][seat] = false;

   System.out.println("Booking cancelled. Refund: 200");
    }

private static void busStatusBoard() {
        viewBusList();
        System.out.print("Enter the bus number: ");
        int busNumber = scanner.nextInt() - 1;

  if (busNumber < 0 || busNumber >= buses.length) {
            System.out.println("Invalid bus number!");
            return;
        }

   System.out.println("\nBus Status for " + buses[busNumber]);
        System.out.println("Route: From " + locations[busNumber] + " To " + destinations[busNumber]);
        for (int i = 0; i < 32; i++) {
            System.out.printf("Seat %d: %s\n", i + 1, seatAvailability[busNumber][i] ? passengerNames[busNumber][i] : "Empty");
        }
    }
}
