import java.util.*;

class bill {
    int consumerNumber;
    double dueAmount;
    double payableAmount;

    public bill (int consumerNumber, double dueAmount, double payableAmount){
        this.consumerNumber = consumerNumber;
        this.dueAmount = dueAmount;
        this.payableAmount = payableAmount;
    }

    @Override
    public String toString() {
        return "Consumer No: " + consumerNumber + "\n" + "Due Amount: " + dueAmount + "\n" + "Payable Amount: " + payableAmount; 
    } 
}

public class CustomerUS2 {
    static List<bill> bills = new ArrayList<>();
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        
        while (true) {
            System.out.println("1: Add Bill");
            System.out.println("2: Update Amount Details");
            System.out.println("3: Delete Bill Details");
            System.out.println("------------------");
            System.out.print("Enter Choice: ");
            int choice = sc.nextInt();

            switch (choice) {
                case 1:
                    addBillDetails(sc);
                    break;
                case 2:
                    updateBillDetails(sc);
                    break;
                case 3:
                    deleteBillDetails(sc);
                    break;
                case 4:
                    displayBillDetails(sc);
                    break;
            
                default:
                    System.out.println("Enter valid choice");
                    break;
            }
        }
    }

    public static void addBillDetails(Scanner sc){
        System.out.print("Enter Consumer Number: ");
        int consumerId = sc.nextInt();
        sc.nextLine();

        System.out.print("Enter Due Amount: ");
        double dueAmount = sc.nextDouble();
        sc.nextLine();

        System.out.print("Enter Payable Amount: ");
        double payableAmount = sc.nextDouble();
        sc.nextLine();

        bill newBill = new bill(consumerId, dueAmount, payableAmount);
        bills.add(newBill);

        System.out.println("Bill details are added successfully");
    }

    public static void updateBillDetails(Scanner sc){
        System.out.print("Enter Consumer ID: ");
        int id = sc.nextInt();

        for(bill bill: bills){
            if(id == bill.consumerNumber){
                System.out.print("Enter Due Amount: ");
                double amount = sc.nextDouble();
                bill.dueAmount = amount;
                bill.payableAmount = amount;

                System.out.println("Bill details are updated successfully");
                return;
            }
        }
        System.out.println("Enter valid id");
    }

    public static void deleteBillDetails(Scanner sc){
        System.out.print("Enter Consumer ID: ");
        int id = sc.nextInt();

        for(bill bill: bills){
            if(id == bill.consumerNumber){
                bills.remove(bill);
                System.out.println("Bill Details are deleted");
                return;
            }
        }
        System.out.println("Enter valid id");
    }

    public static void displayBillDetails(Scanner sc){
        for(bill bill: bills){
            System.out.println(bill);
            System.out.println("--------------");
        }
    }
}
