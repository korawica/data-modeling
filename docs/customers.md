# Customer Profile

## Profile

| Field Name     |  Alias   | Data Type | PK | Description                                            |
|----------------|:--------:|-----------|----|--------------------------------------------------------|
| `customer_id`  | cust_id  | STRING    | Y  | Unique identifier for the customer                     |
| `first_name`   |  fname   | STRING    |    | Customer's first name                                  |
| `last_name`    |  lname   | STRING    |    | Customer's last name                                   |
| `email`        |  email   | STRING    |    | Customer's email address                               |
| `phone_number` |  phone   | STRING    |    | Customer's phone number                                |
| `dob`          |   dob    | DATE      |    | Date of birth                                          |
| `gender`       |  gender  | STRING    |    | Customer's gender (e.g., "M", "F", "Other")            |
| `address`      | address  | STRING    |    | Full address (e.g., street, city, state, zip)          |
| `signup_date`  | register | DATE      |    | Date the customer signed up                            |
| `email_opt_in` |          | BOOLEAN   |    | Whether the customer opted in for email communications |
| `sms_opt_in`   |          | BOOLEAN   |    | Whether the customer opted in for SMS communications   |
| `created_at`   | created  | TIMESTAMP |    | Timestamp when the profile was created                 |
| `updated_at`   | updated  | TIMESTAMP |    | Timestamp when the profile was last updated            |
