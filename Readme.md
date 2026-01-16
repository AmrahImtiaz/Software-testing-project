Automation Testing Framework (C# + Selenium)

This repository contains a modular and maintainable Selenium Automation Framework built using C#, NUnit/MSTest, Page Object Model (POM), JSON test data, and Extent Reports.

Project Structure
AutomationFramework/
│
├── Pages/               
├── Tests/               
├── Utilities/           
├── Drivers/             
├── Reports/             
├── TestData/            
└── README.md            

Technologies Used

C#

Selenium WebDriver

NUnit or MSTest

ExtentReports

Newtonsoft.Json

ChromeDriver

Features

Page Object Model (POM)

Centralized WebDriver setup

Extent Report generation

Screenshot capture on failure

JSON-based test data

Retry for flaky tests

Category-wise execution

Installation & Setup
Clone the repository
git clone https://github.com/your-repository-name.git

Install required NuGet packages
Selenium.WebDriver
Selenium.Support
ExtentReports
Newtonsoft.Json
NUnit
NUnit3TestAdapter
MSTest.TestFramework (if using MSTest)
MSTest.TestAdapter

Running Tests
Using Visual Studio Test Explorer

Open the solution

Go to Test → Test Explorer

Click Run All

Using CLI
dotnet test

Category-based run (NUnit)
dotnet test --filter TestCategory=Regression

JSON Test Data Example

File: LoginData.json

{
  "validLogin": {
    "username": "testuser",
    "password": "password123"
  }
}


Usage:

var data = ConfigReader.LoadJson("LoginData.json");
string username = data["validLogin"]["username"].ToString();

Extent Reports & Screenshots

Screenshots are stored in:

/Reports/Screenshots/


To save screenshot:

screenshot.GetScreenshot().SaveAsFile($"{path}.png");


To attach:

test.AddScreenCaptureFromPath("screenshot.png");

Sample Test
[Test, Category("Regression"), Retry(2)]
public void AddToCartAndCheckout()
{
    var loginPage = new LoginPage(driver);
    var homePage = new HomePage(driver);

    loginPage.Login("username", "password");
    homePage.AddItemToCart();
}

Contribution

Pull requests are welcome.
For major changes, please open an issue first.

License

This project is free to use for automation learning and development.
