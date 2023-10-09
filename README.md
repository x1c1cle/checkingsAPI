# checkingsAPI

Endpoints:
1. Create an account. = {in: customer name, person-id, state of residence; out: account_num} person-id must be unique
2. List all accounts (GET) {out: list of objects: {customer name, person-id, account-num, status of account, date account was opened, balance}}
3. Deactivate an account. (no delete!) {in: account_num}
4. List all transactions for a specified account. (GET) {in: account_num; out:transaction_id, transaction-date, transaction amount, transaction-type, comment}
5. Apply debits or credits to an account. {in: account_num, transaction amount, transaction_type, comment; out: transaction_id,current balance}

Designing how to manage and storage application data:
•	Determining data structure needed for application memory
o	Slices
o	Array
o	Matrix
o	HashMaps
o	Etc
•	Establish variables for specified fields in checking account

Converting an account into a struct to store information about the customer:
•	Customer Name: String
•	Person ID: Int (Must be unique, SS could be used or Driver License)
•	State of Residence: Enum
•	Status of the account: Enum
•	Balance: float
•	Date of creation: String
•	Account Number: Int
•	Transactions: slice of transactions struct 	

*Transaction don’t go past the 30 day limit

Create a transaction struct:
•	TransactionAmount: float
•	TransactionType: string (deposit, withdrawal)
•	TransactionCard: string (Credit/debit)
•	TransactionID: Int
•	TransactionDate: String or time.Time
•	TransactionStatus: String (pending, processed)
•	Comment: String

Storing all checking accounts:
Utilizing slices of struct to hold account structs 
Once program has been close, it will wipe slices clean of previous data
Since we are utilizing slices, if serialization was to be implemented then it would be perfect for creating a parser to save data onto a file.

Future Error Handling: 
•	TransactionDate: Cannot be >30 dats
•	TransactionAmount: Cannot be < 0
•	Person ID: Must be unique

Future versioning:
•	Changes and updates to the software can be used as versions in order to not disrupt consumer processes, such as transactions, history, etc.

