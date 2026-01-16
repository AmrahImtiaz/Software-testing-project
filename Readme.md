# AutomationFramework

This is a Selenium automation framework built with C#, NUnit, Selenium WebDriver, Page Object Model (POM), Extent Reports, and JSON test data.

## Project Structure

```
AutomationFramework/
  Pages/
  Tests/
  Utilities/
  Reports/
  TestData/
  Drivers/
  README.md
```

## Requirements

1. Visual Studio 2022 or later  
2. .NET 6 or .NET 7  
3. Chrome browser  
4. ChromeDriver (auto loaded by Selenium)

## NuGet Packages to Install

```
Selenium.WebDriver
Selenium.Support
Newtonsoft.Json
ExtentReports
NUnit
NUnit3TestAdapter
Microsoft.NET.Test.Sdk
```

## How to Run Tests

### Option 1: Visual Studio
1. Open the solution in Visual Studio  
2. Go to **Test > Test Explorer**  
3. Click **Run All**

### Option 2: CLI
```
dotnet test
```

### Run Only Regression Tests
```
dotnet test --filter "Category=Regression"
```

## Test Data Example

```
{
  "validLogin": {
    "username": "standard_user",
    "password": "secret_sauce"
  }
}
```

## Reports and Screenshots

Reports and screenshots are generated inside:

```
Reports/
Reports/Screenshots/
```

## Sample Test

```
[Test, Category("Regression"), Retry(2)]
public void AddToCartAndCheckout()
{
    var loginPage = new LoginPage(driver);
    loginPage.Login("standard_user", "secret_sauce");
}
``
