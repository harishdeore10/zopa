# Zopa Technical Test  

## To Run:

- Clone repo: https://github.com/harishdeore10/ZopaQuoteApplication.git
- Ensure you have Maven installed
- To run the program, run use the following command:
`java -jar target/quote-1.0-SNAPSHOT.jar [path_to_csv_file] [requested_loan_amount]`

e.g. `java -jar target/quote-1.0-SNAPSHOT.jar src/main/resources/market_data.csv 1000`

## Approach
- I built the app using a fully Test-Driven approach, writing tests in JUnit for functionality before writing the implementation code. This helped me plan out what each service/model was responsible for and allows for easy re-factoring, as tests can be run every time a piece of code is changed.
- Most calculations use the BigDecimal class. This was my first experience using the class, and although it is less readable than using doubles in terms of method calls etc, it is much more accurate.

## Notes
- I have built the app to calculate values based on the amortization calculator found at https://www.bankrate.com/calculators/mortgages/amortization-calculator.aspx (tested with a value of 1000). The values are therefore slightly different to those specified in Test Instructions below.
- There is a known issue with the method used to calculate the total rate in the CalculatorService. It currently calculates the loan details based on an average of all lenders' rates, which is not accurate enough. I would like to figure out how to calculate this more precisely, as it is obviously not precise enough. However, the way I have structured the program means that it is one method that needs fixing - once this single method is fixed, the app will need no other changes.    

## Test Instructions

There is a need for a rate calculation system allowing prospective borrowers to  obtain a quote from our pool of lenders for 36 month loans. This system will  take the form of a command-line application.  

You will be provided with a file containing a list of all the offers being made  by the lenders within the system in CSV format, see the example market.csv file  provided alongside this specification.

  You should strive to provide as low a rate to the borrower as is possible to  ensure that Zopa's quotes are as competitive as they can be against our  competitors'. 

You should also provide the borrower with the details of the  monthly repayment amount and the total repayment amount. 

 Repayment amounts should be displayed to 2 decimal places and the rate of the  loan should be displayed to one decimal place. 
  
Borrowers should be able to request a loan of any £100 increment between £1000  and £15000 inclusive.

If the market does not have sufficient offers from  lenders to satisfy the loan then the system should inform the borrower that it  is not possible to provide a quote at that time.
 
   The application should take arguments in the form:  
 ```
     cmd> [application] [market_file] [loan_amount]  
 ```    
 Example: 
 ```     
     cmd> quote.exe market.csv 1500  
 ```
 The application should produce output in the form: 
 ```     
     cmd> [application] [market_file] [loan_amount]     
     Requested amount: £XXXX 
     Rate: X.X%     
     Monthly repayment: £XXXX.XX     
     Total repayment: £XXXX.XX  
 ```
 Example:  	
 ```
     cmd> quote.exe market.csv 1000 	
     Requested amount: £1000 	
     Rate: 7.0% 	
     Monthly repayment: £30.78 	
     Total repayment: £1108.10  
 ```
## Remarks    
- We do not mind what language you chose for your implementation  
- The monthly and total repayment should use monthly compounding interest  
- We will review your code and run it against some other test cases to see how  it handles them 
- If you have any questions then don't hesitate to contact us
