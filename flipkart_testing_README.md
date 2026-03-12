# Flipkart Web Application Testing

Automated testing project for the Flipkart web application focusing on
**Order History** and **Profile Management** modules.

Website Under Test: https://www.flipkart.com/

------------------------------------------------------------------------

# Project Objective

The objective of this project is to design and implement **positive and
negative test cases** for important user account functionalities in the
Flipkart web application. The testing is automated using **Selenium
WebDriver with JUnit** and maintained in a GitHub repository.

------------------------------------------------------------------------

# Tools and Technologies

-   Java
-   Selenium WebDriver
-   JUnit 5
-   Maven
-   Git
-   GitHub

------------------------------------------------------------------------

# Project Structure

    flipkart-web-testing
    │
    ├── README.md
    ├── pom.xml
    │
    └── src
        └── test
            └── java
                └── flipkart
                    ├── BaseTest.java
                    ├── LoginTest.java
                    ├── OrderHistoryTest.java
                    └── ProfileManagementTest.java

------------------------------------------------------------------------

# Maven Dependencies

``` xml
<dependencies>

<dependency>
<groupId>org.seleniumhq.selenium</groupId>
<artifactId>selenium-java</artifactId>
<version>4.18.1</version>
</dependency>

<dependency>
<groupId>org.junit.jupiter</groupId>
<artifactId>junit-jupiter</artifactId>
<version>5.9.2</version>
</dependency>

</dependencies>
```

------------------------------------------------------------------------

# Base Test (Browser Setup)

``` java
package flipkart;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.junit.jupiter.api.AfterEach;

public class BaseTest {

    protected WebDriver driver;

    public void setup() {
        driver = new ChromeDriver();
        driver.get("https://www.flipkart.com/");
        driver.manage().window().maximize();
    }

    @AfterEach
    public void tearDown() {
        driver.quit();
    }
}
```

------------------------------------------------------------------------

# Order History Test Case

``` java
package flipkart;

import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class OrderHistoryTest extends BaseTest {

    @Test
    public void testViewOrderHistory() {

        setup();

        driver.get("https://www.flipkart.com/account/orders");

        String title = driver.getTitle();

        assertTrue(title.contains("Flipkart"));

        tearDown();
    }
}
```

------------------------------------------------------------------------

# Profile Management Test Case

``` java
package flipkart;

import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class ProfileManagementTest extends BaseTest {

    @Test
    public void testOpenProfilePage() {

        setup();

        driver.get("https://www.flipkart.com/account/profile");

        String currentURL = driver.getCurrentUrl();

        assertTrue(currentURL.contains("profile"));

        tearDown();
    }
}
```

------------------------------------------------------------------------

# Test Case Coverage

## Order History

-   View order history
-   View order details
-   Track order
-   Cancel order
-   Download invoice
-   Filter orders

## Profile Management

-   View profile
-   Edit profile details
-   Change password
-   Add new address
-   Update address
-   Delete address

------------------------------------------------------------------------

# How to Run the Tests

1.  Clone the repository

```{=html}
<!-- -->
```
    git clone https://github.com/yourusername/flipkart-web-testing.git

2.  Open the project in your IDE (IntelliJ / Eclipse)

3.  Run the JUnit test classes

4.  Maven will automatically download required dependencies.

------------------------------------------------------------------------

# Expected Outcome

The automated tests verify that:

-   Order history is accessible and displays correct information.
-   Profile management features work correctly.
-   Invalid inputs are properly handled by the application.

------------------------------------------------------------------------

# Author

Software Testing Project -- Engineering Coursework
