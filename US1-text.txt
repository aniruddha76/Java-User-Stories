import java.util.*;

class customer {
    int consumerId;
    int billNumber;
    String title;
    String customerName;
    String email;
    String mobileNumber;
    String userId;
    String password;
    String confirmPassword;

    public customer(int consumerId, int billNumber, String title, String customerName, String email, 
    String mobileNumber, String userId, String password, String confirmPassword) {

        this.consumerId = consumerId;
        this.billNumber = billNumber;
        this.title = title;
        this.customerName = customerName;
        this.email = email;
        this.mobileNumber = mobileNumber;
        this.userId = userId;
        this.password = password;
        this.confirmPassword = confirmPassword;
    }

    @Override
    public String toString() {
        return "Customer ID: " + consumerId + "\n" +
        "Bill Number: " + billNumber + "\n" +
        "Title: " + title + "\n" +
        "Customer Name: " + customerName + "\n" +
        "Email: " + email + "\n" +
        "Mobile Number: " + mobileNumber + "\n" +
        "User ID: " + userId;
    }
}

public class CustomerUS1 {
    static List<customer> customers = new ArrayList<>();

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        while (true) {
            System.out.println("1: Add Customer");
            System.out.println("2: Update Customer");
            System.out.println("3: Delete Customer");
            System.out.println("4: Select Customer");
            System.out.println("-------------------");

            System.out.println("Enter Choice: ");

            int choice = sc.nextInt();

            switch (choice) {
                case 1:
                    AddCustomer(sc);
                    break;
                case 2:
                    updateCustomer(sc);
                    break;
                case 3:
                    deleteCustomer(sc);
                    break;
                case 4:
                    selectCustomer(sc);
                    break;

                default:
                    System.out.println("Enter Valid Choice");
                    break;
            }
        }

    }

    public static void AddCustomer(Scanner sc) {
        System.out.print("Enter consumer id: ");
        int consumerId = sc.nextInt();
        sc.nextLine();

        System.out.print("Enter Bill Number: ");
        int billNumber = sc.nextInt();
        sc.nextLine();

        System.out.print("Enter Title: ");
        String title = sc.nextLine();

        System.out.print("Enter Customer Name: ");
        String customerName = sc.nextLine();

        System.out.print("Enter Email: ");
        String email = sc.nextLine();

        System.out.print("Enter Mobile Number: ");
        String mobileNumber = sc.nextLine();

        System.out.print("Enter Password: ");
        String password = sc.nextLine();

        System.out.print("Confirm Password: ");
        String confirmPassword = sc.nextLine();

        String userId = UUID.randomUUID().toString();

        customer newCustomer = new customer(consumerId, billNumber, title, customerName, email, mobileNumber, userId, password,
                confirmPassword);
        System.out.println("Customer Registration is successful.");
        customers.add(newCustomer);
    }

    public static void updateCustomer(Scanner sc) {
        System.out.print("Enter Consumer ID: ");
        int id = sc.nextInt();
        sc.nextLine();

        for (customer customer : customers) {
            if (id == customer.consumerId) {
                System.out.print("Enter Email Address: ");
                String email = sc.nextLine();
                customer.email = email;

                System.out.println("Customer details are updated successfully");
                return;
            }
        }

        System.out.println("customer not found.");
    }

    public static void deleteCustomer(Scanner sc) {
        System.out.print("Enter Consumer ID: ");
        int id = sc.nextInt();
        sc.nextLine();

        for (customer customer : customers) {
            if (id == customer.consumerId) {
                customers.remove(customer);
                System.out.println("Customer details are deleted");
                return;
            }
        }

        System.out.println("customer not found.");
    }

    public static void selectCustomer(Scanner sc) {

        for (customer customer : customers) {
            System.out.println(customer);
            System.out.println("--------------");
        }
    }
}
