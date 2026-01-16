🚀 Selenium C# Automation Framework

A modular, scalable automation testing framework built using:

Selenium WebDriver (C#)

NUnit

Page Object Model (POM)

ExtentReports

NLog

JSON-based Test Data

Reusable Utility Methods

Target Test Website: https://www.saucedemo.com

📁 Project Structure
AutomationFramework/
│
├── Drivers/                     # (Optional) Browser drivers
│
├── Pages/                       # Page Object classes
│     ├── LoginPage.cs
│     ├── ProductsPage.cs
│
├── Tests/                       # Automated test cases
│     ├── LoginTests.cs
│     ├── CheckoutTests.cs
│
├── Utilities/                   # Helper utilities
│     ├── BaseTest.cs
│     ├── Logger.cs
│     ├── ExtentManager.cs
│     ├── ScreenshotHelper.cs
│     ├── ConfigReader.cs
│     ├── WaitHelper.cs
│
├── TestData/
│     └── LoginData.json
│
├── Reports/                     # Auto-generated test reports & screenshots
│     ├── TestReport.html
│     ├── *.png
│
├── Logs/
│     ├── logfile.log
│
└── README.md

🧱 Key Features
✔️ Page Object Model (POM)

Modular page classes with:

Locators

Actions

Assertions

✔️ Data-Driven Testing (JSON)

Load test data from:

/TestData/LoginData.json

✔️ HTML Reporting (ExtentReports)

Includes:

Pass/Fail summary

Steps

Screenshots

Timestamps

Error description

✔️ Automatic Screenshots

Saved for all tests (pass/fail):

/Reports/*.png

✔️ Logging (NLog)

Tracks:

Test execution

Errors

Diagnostics

Saved in:

/Logs/logfile.log

✔️ Reusable Utilities

Includes:

Waits

Screenshots

JSON reader

Logging wrapper

Extent report initializer

🛠️ Prerequisites
Install:
Tool	Version
.NET SDK	6+
Visual Studio or JetBrains Rider	Latest
Chrome Browser	Latest
📦 Required NuGet Packages
Package	Purpose
Selenium.WebDriver	WebDriver API
Selenium.WebDriver.ChromeDriver	Chrome automation
NUnit	Test framework
NUnit3TestAdapter	Enables Test Explorer
Microsoft.NET.Test.Sdk	Required for execution
AventStack.ExtentReports	HTML Reports
NLog	Logging
Newtonsoft.Json	JSON reader

Run via Package Manager Console:

Install-Package Selenium.WebDriver
Install-Package Selenium.WebDriver.ChromeDriver
Install-Package NUnit
Install-Package NUnit3TestAdapter
Install-Package Microsoft.NET.Test.Sdk
Install-Package AventStack.ExtentReports
Install-Package NLog
Install-Package Newtonsoft.Json

▶️ How to Run Tests
1. Open the solution
AutomationFramework.sln

2. Build
Ctrl + Shift + B

3. Open Test Explorer
Test → Test Explorer

4. Run Tests

Click:

Run All


Tests will open Chrome and execute automation steps.

📊 Output & Reports
📌 1. HTML Test Report

Located in:

/Reports/TestReport.html


Open the file → View screenshots, status, logs, duration.

📌 2. Screenshots

Saved automatically:

/Reports/*.png

📌 3. Execution Logs

Stored in:

/Logs/logfile.log


Contains:

Info logs

Errors

Warnings

Step-by-step tracking

🧪 Creating a New Test

Create a new test file:

/Tests/MyNewTest.cs


Example:

[Test]
public void VerifyUserCanLogin()
{
    var login = new LoginPage(driver);
    login.Login("standard_user", "secret_sauce");

    var products = new ProductsPage(driver);
    Assert.IsTrue(products.IsProductsPageDisplayed());
}

🌐 Adding a New Page (POM)

Inside:

/Pages/


Example:

public class LoginPage
{
    private IWebDriver driver;

    public LoginPage(IWebDriver driver)
    {
        this.driver = driver;
    }

    private IWebElement Username => driver.FindElement(By.Id("user-name"));
    private IWebElement Password => driver.FindElement(By.Id("password"));
    private IWebElement LoginBtn => driver.FindElement(By.Id("login-button"));

    public void Login(string user, string pass)
    {
        Username.SendKeys(user);
        Password.SendKeys(pass);
        LoginBtn.Click();
    }
}
