package labexam;

import org.hibernate.*;
import org.hibernate.cfg.Configuration;
import org.hibernate.criterion.*;

import java.util.List;

public class ClientDemo {
    public static void main(String[] args) {
        // Initialize SessionFactory
        SessionFactory factory = new Configuration().configure().buildSessionFactory();
        Session session = factory.openSession();
        Transaction transaction = session.beginTransaction();

        // Insert records
        Customer customer1 = new Customer();
        customer1.setName("Alice");
        customer1.setEmail("alice@example.com");
        customer1.setAge(25);
        customer1.setLocation("New York");

        Customer customer2 = new Customer();
        customer2.setName("Bob");
        customer2.setEmail("bob@example.com");
        customer2.setAge(30);
        customer2.setLocation("California");

        session.save(customer1);
        session.save(customer2);

        transaction.commit();

        // Fetch records using Criteria
        Criteria criteria = session.createCriteria(Customer.class);

        System.out.println("Customers aged less than 30:");
        criteria.add(Restrictions.lt("age", 30));
        List<Customer> customers = criteria.list();
        customers.forEach(customer -> System.out.println(customer.getName()));

        System.out.println("Customers located in 'New York':");
        criteria = session.createCriteria(Customer.class);
        criteria.add(Restrictions.like("location", "New York"));
        customers = criteria.list();
        customers.forEach(customer -> System.out.println(customer.getName()));

        // Close resources
        session.close();
        factory.close();
    }
}

