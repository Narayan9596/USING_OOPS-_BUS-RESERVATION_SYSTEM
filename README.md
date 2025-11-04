🚌 Bus Reservation System
A simple console-based mini-project in Java that simulates a bus ticket booking system. This project is designed for students (like second-year university students) to practice core Java concepts.
It provides a command-line interface (CLI) for users to log in, view available buses, book seats, cancel bookings, and check the reservation status of any bus.
✨ Features
 * User Login: A basic, hardcoded login system (username: user, password: pass) to access the main menu.
 * View Bus List: Displays a list of all available buses with their respective routes (origin and destination).
 * Book Tickets:
   * Allows a user to select a bus by its number.
   * Displays the route and available seats.
   * Lets the user book one or more seats by specifying the seat number (1-32).
   * Records the passenger's name for each booked seat.
 * Cancel Booking:
   * Allows a user to select a bus and a specific seat number to cancel a booking.
   * The seat is then marked as "Empty" and available again.
 * Bus Status Board:
   * Shows a detailed, seat-by-seat status for any selected bus.
   * Lists all 32 seats, displaying "Empty" for available seats or the passenger's name for booked seats.
 * Menu-Driven Interface: A simple, numbered menu for easy navigation through the application.
🛠️ Technologies Used
 * Language: Java
 * Core Concepts:
   * static methods and variables
   * Arrays (1D and 2D) for data storage
   * User input handling with java.util.Scanner
   * Control flow (loops, switch statements)
   * Basic console I/O (System.out.println)
🚀 How to Run
 * Prerequisites: You must have the Java Development Kit (JDK) installed on your system.
 * Clone the Repository:
   git clone https://github.com/your-username/your-repository-name.git

 * Navigate to the Directory:
   cd your-repository-name

 * Compile the Java File:
   javac BusReservationSystem.java

 * Run the Program:
   java BusReservationSystem

 * Login:
   * Username: user
   * Password: pass
📸 Screenshots
(It is highly recommended to add screenshots of your application in action here. This makes your project look much more complete.)
Example: Main Menu
====================================== WELCOME TO BUS RESERVATION SYSTEM ======================================
[1] View Bus List
[2] Book Tickets
[3] Cancel Booking
[4] Bus Status Board
[5] Exit
Enter Your Choice:

Example: Bus Status Board
Enter the bus number: 1

Bus Status for janta bus service
Route: From Delhi To Jaipur
Seat 1: Empty
Seat 2: Empty
Seat 3: John Doe
Seat 4: Empty
...
Seat 32: Empty

📈 Potential Future Improvements
This project is a great foundation. Here are some ways it could be improved:
 * Refactor to True OOP: Instead of using parallel static arrays, create classes like Bus, Route, Seat, and Passenger. This would make the code much cleaner, more organized, and truly object-oriented.
 * Data Persistence: Save the booking information to a file (e.g., a .txt or .csv file). This way, reservations aren't lost every time the program stops.
 * Database Integration: For a more advanced version, connect the system to a SQL database (like MySQL) using JDBC to store all data.
 * Dynamic Data: Allow an admin to add or remove buses, routes, and destinations instead of having them hardcoded.
 * Improved Error Handling: Add more robust validation for all user inputs (e.g., prevent non-numeric input where numbers are expected).
