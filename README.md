import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class ReservationSystem {
    private List<Reservation> reservations;
    private Scanner scanner;

    public ReservationSystem() {
        this.reservations = new ArrayList<>();
        this.scanner = new Scanner(System.in);
    }

    public void run() {
        while (true) {
            System.out.println("Reservation System");
            System.out.println("1. Make a reservation");
            System.out.println("2. Cancel a reservation");
            System.out.println("3. View reservations");
            System.out.println("4. Exit");
            System.out.print("Choose an option: ");
            int option = scanner.nextInt();

            switch (option) {
                case 1:
                    makeReservation();
                    break;
                case 2:
                    cancelReservation();
                    break;
                case 3:
                    viewReservations();
                    break;
                case 4:
                    System.out.println("Goodbye!");
                    return;
                default:
                    System.out.println("Invalid option. Please try again.");
            }
        }
    }

    private void makeReservation() {
        System.out.print("Enter your name: ");
        String name = scanner.next();
        System.out.print("Enter the date (yyyy-mm-dd): ");
        String date = scanner.next();
        System.out.print("Enter the time (hh:mm): ");
        String time = scanner.next();

        Reservation reservation = new Reservation(name, date, time);
        reservations.add(reservation);
        System.out.println("Reservation made successfully!");
    }

    private void cancelReservation() {
        System.out.print("Enter the reservation ID: ");
        int id = scanner.nextInt();

        for (Reservation reservation : reservations) {
            if (reservation.getId() == id) {
                reservations.remove(reservation);
                System.out.println("Reservation cancelled successfully!");
                return;
            }
        }

        System.out.println("Reservation not found.");
    }

    private void viewReservations() {
        System.out.println("Reservations:");
        for (Reservation reservation : reservations) {
            System.out.println(reservation.toString());
        }
    }

    public static void main(String[] args) {
        ReservationSystem system = new ReservationSystem();
        system.run();
    }
}

class Reservation {
    private int id;
    private String name;
    private String date;
    private String time;

    public Reservation(String name, String date, String time) {
        this.id = reservations.size() + 1;
        this.name = name;
        this.date = date;
        this.time = time;
    }

    public int getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public String getDate() {
        return date;
    }

    public String getTime() {
        return time;
    }

    @Override
    public String toString() {
        return "Reservation ID: " + id + ", Name: " + name + ", Date: " + date + ", Time: " + time;
    }
}
