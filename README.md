```C#
using System;
using System.Collections.Generic;

// Interface for email providers
interface IEmailProvider
{
    void SendEmail(string to, string subject, string message);
}

// Email sender class responsible for sending emails
class EmailSender
{
    private readonly IEmailProvider _emailProvider;

    public EmailSender(IEmailProvider emailProvider)
    {
        _emailProvider = emailProvider;
    }

    public void SendEmail(string to, string subject, string message)
    {
        // Business logic for sending an email
        Console.WriteLine($"Sending email to: {to}");
        _emailProvider.SendEmail(to, subject, message);
    }
}

// Concrete email provider using SMTP
class SmtpEmailProvider : IEmailProvider
{
    public void SendEmail(string to, string subject, string message)
    {
        // Implementation for sending emails via SMTP
        Console.WriteLine($"SMTP Email sent to: {to}, Subject: {subject}, Message: {message}");
    }
}

// Concrete email provider using a third-party API
class ApiEmailProvider : IEmailProvider
{
    public void SendEmail(string to, string subject, string message)
    {
        // Implementation for sending emails using a third-party API
        Console.WriteLine($"API Email sent to: {to}, Subject: {subject}, Message: {message}");
    }
}

class Program
{
    static void Main()
    {
        // Create instances of email providers
        IEmailProvider smtpProvider = new SmtpEmailProvider();
        IEmailProvider apiProvider = new ApiEmailProvider();

        // Create an email sender with SMTP provider
        var emailSenderWithSmtp = new EmailSender(smtpProvider);
        emailSenderWithSmtp.SendEmail("example@example.com", "Welcome!", "Welcome to our website!");

        // Create an email sender with API provider
        var emailSenderWithApi = new EmailSender(apiProvider);
        emailSenderWithApi.SendEmail("user@example.com", "Special Offer", "Check out our special offers!");

        Console.ReadLine();
    }
}
```
