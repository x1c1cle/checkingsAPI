# checkingsAPI

Endpoints:
1. Create an account. = {in: customer name, person-id, state of residence; out: account_num} person-id must be unique
2. List all accounts (GET) {out: list of objects: {customer name, person-id, account-num, status of account, date account was opened, balance}}
3. Deactivate an account. (no delete!) {in: account_num}
4. List all transactions for a specified account. (GET) {in: account_num; out:transaction_id, transaction-date, transaction amount, transaction-type, comment}
5. Apply debits or credits to an account. {in: account_num, transaction amount, transaction_type, comment; out: transaction_id,current balance}

Designing how to manage and storage application data:
-	Determining data structure needed for application memory
-	Slices
-	Array
-	Matrix
-	HashMaps
-	Etc
-	Establish variables for specified fields in checking account

Converting an account into a struct to store information about the customer:
-	Customer Name: String
-	Person ID: Int (Must be unique, SS could be used or Driver License)
-	State of Residence: Enum
-	Status of the account: Enum
-	Balance: float
-	Date of creation: String
-	Account Number: Int
-	Transactions: slice of transactions struct 	

*Transaction don’t go past the 30 day limit

Create a transaction struct:
-	TransactionAmount: float
-	TransactionType: string (deposit, withdrawal)
-	TransactionID: Int
-	TransactionDate: String or time.Time
-	Comment: String

Storing all checking accounts:
Utilizing slices of struct to hold account structs 
Once program has been close, it will wipe slices clean of previous data
Since we are utilizing slices, if serialization was to be implemented then it would be perfect for creating a parser to save data onto a file.

Handling statuses of accounts:
-   	Utilizing a switch case statement will allow easier handling of activation and deactivation
    -   As well as any future status that will be implemented
-   	Helper function(s) for more readability (Possibly for the future)
 

Future Error Handling:
-   	TransactionDate: Cannot be >30 dats
-   	TransactionAmount: Cannot be < 0
-   	Handle Person ID: Must be unique
    -   Message could be “this ID is already in use” or “this ID is not valid”
    -   Check on person ID length, variable type, etc.
-   	Handling negative transaction amounts
    -   If a transaction amount is negative, add this to the balance as this is a deposit, and declare as such
-   	Handle negative balance
    -   Check funds before processing withdrawal/deposit
    -  Give an no available balance error when attempting a withdrawal 
