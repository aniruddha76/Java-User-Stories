import java.util.*;

class complaint {
    String complaintType;
    String category;
    String landMark;
    String customerName;
    String problem;
    int consumerNumber;
    String address;
    int mobileNumber;

    public complaint(String complaintType, String category, String landMark, String customerName, String problem,
            int consumerNumber, String address, int mobileNumber) {
        this.complaintType = complaintType;
        this.category = category;
        this.landMark = landMark;
        this.customerName = customerName;
        this.problem = problem;
        this.consumerNumber = consumerNumber;
        this.address = address;
        this.mobileNumber = mobileNumber;
    }

    @Override
    public String toString() {
        return "Complaint Type: " + complaintType + "\n" +
                "Category: " + category + "\n" +
                "Landmark: " + landMark + "\n" +
                "Customer Name: " + customerName + "\n" +
                "Problem: " + problem + "\n" +
                "Consumer Number: " + consumerNumber + "\n" +
                "Address: " + address + "\n" +
                "Mobile Number: " + "\n";
    }
}

public class CustomerUS3 {
    static List<complaint> complaints = new ArrayList<>();

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        while (true) {
            System.out.println("1: Register Complaint");
            System.out.println("2: Delete Complaint");
            System.out.println("--------------------");
            System.out.print("Enter Choice: ");
            int choice = sc.nextInt();
            sc.nextLine();

            switch (choice) {
                case 1:
                    registerComplaint(sc);
                    break;
                case 2:
                    deleteComplaint(sc);
                    break;
                case 3:
                    displayComplaint(sc);
                    break;

                default:
                    System.out.println("Enter valid choice");
                    break;
            }
        }
    }

    public static void registerComplaint(Scanner sc) {
        System.out.print("Complaint Type: ");
        String complaintType = sc.nextLine();

        System.out.print("Category: ");
        String category = sc.nextLine();

        System.out.print("Landmark: ");
        String landMark = sc.nextLine();

        System.out.print("Customer Name: ");
        String customerName = sc.nextLine();

        System.out.print("Problem: ");
        String problem = sc.nextLine();

        System.out.print("Consumer Number: ");
        int consumerNumber = sc.nextInt();
        sc.nextLine();

        System.out.print("Address: ");
        String address = sc.nextLine();

        System.out.print("Mobile Number: ");
        int mobileNumber = sc.nextInt();

        complaint newComplaint = new complaint(complaintType, category, landMark, customerName, problem, consumerNumber,
                address, mobileNumber);
        System.out.println("Successfully registered Complaint");

        complaints.add(newComplaint);
    }

    public static void deleteComplaint(Scanner sc) {
        System.out.print("Enter Customer ID: ");
        int id = sc.nextInt();

        for (complaint complaint : complaints) {
            if (id == complaint.consumerNumber) {
                complaints.remove(complaint);
                System.out.println("Complaint Deleted");
                System.out.println("-------------------");
                return;
            }
        }
        System.out.println("Customer not found");
    }

    public static void displayComplaint(Scanner sc) {
        for (complaint complaint : complaints) {
            System.out.println(complaint);
            System.out.println("--------------");
        }
    }
}
