# automation-framework-selenium

**Comprehensive_Hybrid** — A hybrid Selenium automation framework (Java + Maven + TestNG) for web UI testing.

## Table of Contents
- [About](#about)  
- [Tech Stack](#tech-stack)  
- [Repository Structure](#repository-structure)  
- [Prerequisites](#prerequisites)  
- [Setup](#setup)  
- [Running Tests](#running-tests)  
- [Reporting & Outputs](#reporting--outputs)  
- [Configuration](#configuration)  
- [Contributing](#contributing)  
- [License & Contact](#license--contact)

---

## About
A Selenium-based hybrid automation framework to create, organize, and run UI automation test suites using Java, Maven and TestNG. It follows a modular layout (configs, drivers, test sources, reports) so tests can be executed locally or in CI.

---

## Tech Stack
- Java 17 (or compatible JDK)  
- Maven (project build & dependency management)  
- Selenium WebDriver  
- TestNG (test runner & suites)  
- Browser drivers (ChromeDriver / GeckoDriver)  
- Optional: Allure/Extent reports, CI (GitHub Actions / Jenkins) — adjust per your pipeline

---

## Repository Structure (based on repo listing)
```
automation-framework-selenium/
├── configs/                # framework configuration (properties, envs)
├── drivers/                # browser driver binaries (or driver helper)
├── reports/                # report snapshots / custom report output
├── src/test/               # test code (page objects, tests, utils)
├── target/                 # maven build output
├── test-output/            # TestNG generated results
├── pom.xml                 # Maven configuration & dependencies
├── testng.xml              # TestNG suites & groups
└── README.md               # (this file)
```

---

## Prerequisites
1. Java JDK 17 installed and `JAVA_HOME` set.  
2. Maven 3.6+ installed.  
3. Browser(s) installed for testing (Chrome / Firefox).  
4. Appropriate browser driver(s) on your `$PATH` or in `drivers/` (e.g., `chromedriver`, `geckodriver`).  
5. Optional: Git, and CI runner configured if you plan to run tests in pipeline.

---

## Setup — clone & build
```bash
# clone repo
git clone https://github.com/nandubangari/automation-framework-selenium.git
cd automation-framework-selenium

# build (download dependencies)
mvn clean test-compile
```

---

## Running Tests

### Run full TestNG suite (default `testng.xml`)
```bash
mvn test
```

### Run a specific TestNG suite file
```bash
mvn -Dtestng.suiteXmlFiles=testng.xml test
```

### Run a single test class or method
```bash
# run a single test class
mvn -Dtest=package.to.ClassName test

# run a single test method
mvn -Dtest=package.to.ClassName#methodName test
```

---

## Test Reports & Artifacts
- TestNG default output: `test-output/` (HTML reports, logs).  
- Maven surefire reports: `target/surefire-reports/`.  
- `reports/` — repository folder intended for custom or archived reports/screenshots.  
- If you use Allure or Extent, configure their Maven plugins in `pom.xml` and collect `target/site` or `allure-results` accordingly.

---

## Configuration
- `configs/` is intended for framework-level configuration files (e.g., `env.properties`, `log4j2.xml`).  
- Common properties to configure:
  - `base.url` — application under test  
  - `browser` — chrome/firefox  
  - `implicit.wait`, `explicit.wait` timeouts  
  - `report.path` — where to save reports/screenshots

---

## Best Practices / Recommendations
- Keep sensitive data out of repo (use environment variables or CI secrets).  
- Use WebDriverManager (or keep drivers in `drivers/` and ensure they match installed browser versions).  
- Structure tests with Page Object Model (POM) to improve maintainability.  
- Hook screenshots on failure (TestNG `Listener` or `@AfterMethod` with `ITestResult`).  
- Integrate with CI (GitHub Actions / Jenkins) to run tests on push/pr.

---

## Contributing
Contributions are welcome — please open issues or PRs. Suggested structure for PRs:
1. Create feature branch `feature/<short-desc>`.  
2. Add tests and update documentation.  
3. Create PR describing change and test results.

---


