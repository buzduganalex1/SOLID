```C#
using System;

class Customer
{
    public string Name { get; set; }
    public string Email { get; set; }
}

// Concrete email sending service
class SmtpEmailService
{
    public void SendEmail(string to, string subject, string message)
    {
        // SMTP email sending code
        Console.WriteLine($"SMTP Email sent to: {to}, Subject: {subject}, Message: {message}");
    }
}

class ApiEmailService
{
    public void SendEmail(string to, string subject, string message)
    {
        // Email sending using a third-party API
        Console.WriteLine($"API Email sent to: {to}, Subject: {subject}, Message: {message}");
    }
}

class EmailService
{
    private readonly SmtpEmailService _smtpEmailSender;
    private readonly ApiEmailService _apiEmailSender;

    public EmailService()
    {
        _smtpEmailSender = new SmtpEmailService();
        _apiEmailSender = new ApiEmailService();
    }

    public void SendEmailUsingSmtp(string to, string subject, string message)
    {
        // Business logic for sending an email using SMTP
        Console.WriteLine($"Sending email using SMTP to: {to}");
        _smtpEmailSender.SendEmail(to, subject, message);
    }

    public void SendEmailUsingApi(string to, string subject, string message)
    {
        // Business logic for sending an email using a third-party API
        Console.WriteLine($"Sending email using API to: {to}");
        _apiEmailSender.SendEmail(to, subject, message);
    }

    public void CalculateCustomerDiscount(Customer customer)
    {
        // Business logic for calculating a discount for the customer
        Console.WriteLine($"Calculating discount for customer: {customer.Name}");
    }
}

class Program
{
    static void Main()
    {
        // Create an instance of the EmailService
        EmailService emailService = new EmailService();

        // Sending an email using SMTP
        emailService.SendEmailUsingSmtp("example@example.com", "Welcome!", "Welcome to our website!");

        // Sending an email using API
        emailService.SendEmailUsingApi("user@example.com", "Special Offer", "Check out our special offers!");

        // Calculate a customer discount (Unrelated to email service)
        var customer = new Customer { Name = "John Doe", Email = "john@example.com" };
        emailService.CalculateCustomerDiscount(customer);

        Console.ReadLine();
    }
}
```
