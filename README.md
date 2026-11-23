# ..PortSwigger Web Security Academy..

My learning portfolio for web application security topics covered in [PortSwigger Web Security Academy](https://portswigger.net/web-security). Learning progress and hands-on lab results are tracked separately; only labs listed as completed below are marked solved.

## SQL injection

Learning path: [SQL injection](https://portswigger.net/web-security/sql-injection) | [SQL injection labs](https://portswigger.net/web-security/all-labs#sql-injection)

### Completed learning topics

- [x] [What is SQL injection?](https://portswigger.net/web-security/sql-injection#what-is-sql-injection-sqli)
- [x] [How to detect SQL injection vulnerabilities](https://portswigger.net/web-security/sql-injection#how-to-detect-sql-injection-vulnerabilities)
- [x] [Retrieving hidden data](https://portswigger.net/web-security/sql-injection#retrieving-hidden-data)
- [x] [Subverting application logic](https://portswigger.net/web-security/sql-injection#subverting-application-logic)
- [x] [SQL injection UNION attacks](https://portswigger.net/web-security/sql-injection/union-attacks)
- [x] [Determining the number of columns required](https://portswigger.net/web-security/sql-injection/union-attacks#determining-the-number-of-columns-required)
- [x] [Finding columns with a useful data type](https://portswigger.net/web-security/sql-injection/union-attacks#finding-columns-with-a-useful-data-type)
- [x] [Using a SQL injection UNION attack to retrieve interesting data](https://portswigger.net/web-security/sql-injection/union-attacks#using-a-sql-injection-union-attack-to-retrieve-interesting-data)
- [x] [Retrieving multiple values within a single column](https://portswigger.net/web-security/sql-injection/union-attacks#retrieving-multiple-values-within-a-single-column)
- [x] [Examining the database](https://portswigger.net/web-security/sql-injection/examining-the-database)
- [x] [Blind SQL injection](https://portswigger.net/web-security/sql-injection/blind)
- [x] [Exploiting blind SQL injection by triggering conditional responses](https://portswigger.net/web-security/sql-injection/blind#exploiting-blind-sql-injection-by-triggering-conditional-responses)

### In progress

- [ ] [Error-based SQL injection](https://portswigger.net/web-security/sql-injection/blind#error-based-sql-injection) - 4 of 7

### Next up

- [ ] [Exploiting blind SQL injection by triggering time delays](https://portswigger.net/web-security/sql-injection/blind#exploiting-blind-sql-injection-by-triggering-time-delays) - not started

## My Burp Suite workflow

For these Academy labs, I used Burp Suite to inspect the relevant application requests, work with them in Repeater, and compare responses after changing one input at a time. Depending on the lab, I looked for differences in returned content, status, errors, or response behavior, then checked the Academy lab status to confirm completion. The notes below summarize concepts rather than recording payloads or step-by-step solutions.

### Completed hands-on labs

- [x] [Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data](https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data) - Apprentice
  - **Learning:** A vulnerable filter can expose records the application meant to hide.
  - **Defensive note:** Use parameterized queries and enforce visibility rules on the server.
- [x] [Lab: SQL injection vulnerability allowing login bypass](https://portswigger.net/web-security/sql-injection/lab-login-bypass) - Apprentice
  - **Learning:** Unsafe query construction can undermine authentication checks.
  - **Defensive note:** Use parameterized authentication queries and verify credentials through the intended authentication flow.
- [x] [Lab: SQL injection UNION attack, determining the number of columns returned by the query](https://portswigger.net/web-security/sql-injection/union-attacks/lab-determine-number-of-columns) - Practitioner
  - **Learning:** Combined query results must have compatible shapes.
  - **Defensive note:** Avoid building queries from untrusted input; keep query structure fixed.
- [x] [Lab: SQL injection UNION attack, finding a column containing text](https://portswigger.net/web-security/sql-injection/union-attacks/lab-find-column-containing-text) - Practitioner
  - **Learning:** Columns have data types that constrain which values can appear in the result.
  - **Defensive note:** Parameterization prevents input from changing the query's structure.
- [x] [Lab: SQL injection UNION attack, retrieving data from other tables](https://portswigger.net/web-security/sql-injection/union-attacks/lab-retrieve-data-from-other-tables) - Practitioner
  - **Learning:** A vulnerable query may expose data beyond the feature's intended results.
  - **Defensive note:** Combine parameterized queries with least-privilege database permissions.
- [x] [Lab: SQL injection UNION attack, retrieving multiple values in a single column](https://portswigger.net/web-security/sql-injection/union-attacks/lab-retrieve-multiple-values-in-single-column) - Practitioner
  - **Learning:** Databases differ in how they combine values into one result.
  - **Defensive note:** Keep SQL structure in trusted code and account for database-specific behavior when reviewing queries.
- [x] [Lab: SQL injection attack, querying the database type and version on MySQL and Microsoft](https://portswigger.net/web-security/all-labs#sql-injection) - Practitioner
  - **Learning:** Database syntax and version-identification methods vary by platform.
  - **Defensive note:** Restrict database permissions and avoid exposing unnecessary database metadata.
- [x] [Lab: SQL injection attack, listing the database contents on non-Oracle databases](https://portswigger.net/web-security/sql-injection/examining-the-database/lab-listing-database-contents-non-oracle) - Practitioner
  - **Learning:** Database metadata can reveal tables and columns when queries are injectable.
  - **Defensive note:** Apply least privilege and prevent untrusted input from being interpreted as SQL.
- [x] [Lab: Blind SQL injection with conditional responses](https://portswigger.net/web-security/sql-injection/blind/lab-conditional-responses) - Practitioner
  - **Learning:** Response differences can reveal query behavior even when query results are not displayed.
  - **Defensive note:** Parameterized queries address the root cause; consistent responses alone are not a substitute.

### In-progress hands-on lab

- [ ] [Lab: Blind SQL injection with conditional errors](https://portswigger.net/web-security/sql-injection/blind/lab-conditional-errors) - Practitioner
  - **Learning focus:** Understanding how database errors can influence observable application behavior.
  - **Defensive note:** Use parameterized queries and return generic errors without exposing database details.

## Defensive takeaway

Use parameterized queries instead of building SQL with string concatenation, apply least privilege to database accounts, and avoid exposing detailed database errors to users.
