# import java.util.*;

public class linkedlist {

    node head;
    static Scanner sc = new Scanner(System.in);

    class node {

        int data;
        node next;

        node() {
            System.out.println("Enter the data");
            data = sc.nextInt();
            next = null;
        }

    }

    public void insertfirst() {
        node newnode = new node();
        if (head == null) {
            head = newnode;
            return;
        }

        newnode.next = head;
        head = newnode;

    }

    public void insertatlast() {
        node newnode = new node();
        if (head == null) {
            head = newnode;
            return;
        }

        node temp = head;
        while (temp.next != null) {
            temp = temp.next;

        }
        temp.next = newnode;

    }

    public void insertatposition(int index) {

        if (index == 1) {
            insertfirst();
            return;
        }

        node newnode = new node();
        node temp = head;

        for (int i = 1; i < index - 1; i++) {
            temp = temp.next;

        }

        newnode.next = temp.next;
        temp.next = newnode;

    }

    public void insertsort() {
        node newnode = new node();
        if (head == null) {
            head = newnode;
            return;
        }
        if (head.data > newnode.data) {
            newnode.next = head;
            head = newnode;
        } else {
            node temp = head;
            node prev = head;
            while (temp.next != null && temp.data < newnode.data) {
                prev = temp;
                temp = temp.next;

            }

            newnode.next = prev.next;
            prev.next = newnode;

        }
    }

    public void deleteatfirst() {
        if (head == null) {
            System.out.println("no data to show");
            return;
        }

        System.out.println("deleted element is : " + head.data);
        head = head.next;

    }

    public void deleteatlast() {
        if (head == null) {
            System.out.println("no data to show");
            return;
        }

        node temp = head;
        node prev = head;
        while (temp.next != null) {
            prev = temp;
            temp = temp.next;

        }
        System.out.println("Deleted element " + temp.data);
        prev.next = null;

    }

    public void deletenode(int d) {
        if (head == null) {
            System.out.println("no data to show");
            return;
        }
        if (head.data == d) {
            deleteatfirst();
            return;
        }
        node temp = head;
        node prev = head;
        while (temp.next != null && temp.data != d) {
            prev = temp;
            temp = temp.next;
        }
        System.out.println("deleted item is " + temp.data);
        prev.next = temp.next;

    }

    public void display() {
        if (head == null) {
            System.out.println("no data to show");
            return;
        }

        node temp = head;
        while (temp != null) {
            System.out.print(temp.data + "->");
            temp = temp.next;
        }

    }

    public static void main(String[] args) {
        linkedlist ll = new linkedlist();
        int ch, datatodelete, pos;
        do {
            System.out.println();
            System.out.println("Enter 1 for insert at first");
            System.out.println("Enter 2 for display");
            System.out.println("Enter 3 for insert at last");
            System.out.println("Enter 4 for delete at first");
            System.out.println("Enter 5 for delete at last");
            System.out.println("Enter 6 for delete any element");
            System.out.println("Enter 7 for insert at  any pos");
            System.out.println("Enter 8 for insert in ascending order");
            System.out.println("9 for exit");
            ch = sc.nextInt();
            switch (ch) {
                case 1:
                    ll.insertfirst();
                    break;
                case 2:
                    ll.display();
                    break;
                case 3:
                    ll.insertatlast();
                    break;
                case 4:
                    ll.deleteatfirst();
                    break;
                case 5:
                    ll.deleteatlast();
                    break;
                case 6:
                    System.out.println("enter the node to delete");
                    datatodelete = sc.nextInt();
                    ll.deletenode(datatodelete);
                    break;
                case 7:
                    System.out.println("enter the position to insert data");
                    pos = sc.nextInt();
                    ll.insertatposition(pos);
                    break;
                case 8:
                    ll.insertsort();
                    break;

            }

        } while (ch != 9);

    }

}
