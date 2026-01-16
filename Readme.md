AutomationFramework

This is a Selenium automation framework built with C#, NUnit, Selenium WebDriver, Page Object Model (POM), Extent Reports, and JSON test data.

Project Structure
AutomationFramework/
  Pages/
  Tests/
  Utilities/
  Reports/
  TestData/
  Drivers/
  README.md

Requirements

Visual Studio 2022 or later

.NET 6 or .NET 7

Chrome browser

ChromeDriver (auto loaded by Selenium)

NuGet Packages to Install
Selenium.WebDriver
Selenium.Support
Newtonsoft.Json
ExtentReports
NUnit
NUnit3TestAdapter
Microsoft.NET.Test.Sdk

How to Run Tests
Option 1: Visual Studio

Open the solution in Visual Studio

Go to Test > Test Explorer

Click Run All

Option 2: CLI
dotnet test

Run Only Regression Tests
dotnet test --filter "Category=Regression"

How Test Data Works

Example: LoginData.json

{
  "validLogin": {
    "username": "standard_user",
    "password": "secret_sauce"
  }
}


You load it like this:

var data = ConfigReader.LoadJson("LoginData.json");
string username = data["validLogin"]["username"].ToString();

Reports and Screenshots

After running tests, reports are generated inside:

Reports/
Reports/Screenshots/


Screenshots are created inside the same report folder.

BaseTest Flow

Open browser

Open SauceDemo

Run test

Take screenshot

Add screenshot to report

Save report

Close browser

Sample Test
[Test, Category("Regression"), Retry(2)]
public void AddToCartAndCheckout()
{
    var loginPage = new LoginPage(driver);
    loginPage.Login("standard_user", "secret_sauce");
}

Troubleshooting
Screenshots Not Appearing

Make sure:

Folder Reports exists

You are saving screenshot using a valid path

You are using:

screenshot.SaveAsFile(fullPath);

Report Not Updating

Make sure:

extent.Flush();
