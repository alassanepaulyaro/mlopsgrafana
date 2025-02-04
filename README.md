# Grafana Data Visualization & Monitoring - Banking Transaction Simulator
This project simulates banking transaction data and inserts records into a PostgreSQL database. The generated data is then ready for visualization and monitoring in tools such as Grafana.

## Overview

The code performs the following functions:

- Data Generation:
    Utilizes the Faker library to generate fake banking data records. Each record includes transaction details such as a unique transaction ID, transaction type, amounts, account holder name, merchant category, card details, and blacklist status.

- Rule Processing:
    A function run_rules() applies simple business rules on each record:
    - Rule1: If the transaction amount is greater than or equal to $100, the account is not blacklisted, and the transaction type is Real_time_transaction, the transaction is rejected with an explanation.
    - Rule2: If the account is blacklisted for a Real_time_transaction, the transaction is rejected.
    - If the transaction type is not Real_time_transaction, no rules are triggered and the transaction is approved.
    - Otherwise, no rules are triggered.

- Database Integration:
    Connects to a PostgreSQL database, creates a table (if it does not already exist), and inserts the generated records along with the rule evaluation results.

- Data Insertion Loop:
    In an infinite loop, the script generates a batch of records every 15 seconds (configurable) and inserts them into the banking_data table. This continuous data generation is ideal for real-time monitoring and visualization with Grafana.