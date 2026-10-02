-- 1. BASIC SQL ANALYSIS (Q1–Q10)
--------------------------------------------------------------

-- Q1: Display all loan records

SELECT *
FROM Loan;



-- Q2: Display customer name, city, loan type, and loan amount

SELECT Customer_Name, City, Loan_Type, Loan_Amount
FROM Loan;



-- Q3: Find all customers who have applied for a Personal Loan

SELECT Customer_ID, Customer_Name, Loan_Type, Loan_Amount
FROM Loan
WHERE Loan_Type = 'Personal Loan';



-- Q4: Find customers whose loan amount is greater than ₹5,00,000

SELECT Customer_ID, Customer_Name, Loan_Amount
FROM Loan
WHERE Loan_Amount > 500000;




-- Q5: Find customers from Lucknow

SELECT Customer_ID, Customer_Name, City
FROM Loan
WHERE City = 'Lucknow';




-- Q6: Display customers whose credit score is greater than 750

SELECT Customer_ID, Customer_Name, Credit_Score
FROM Loan
WHERE Credit_Score > 750;




-- Q7: Find customers whose annual income is between ₹5 lakh and ₹15 lakh

SELECT Customer_ID, Customer_Name, Annual_Income
FROM Loan
WHERE Annual_Income BETWEEN 500000 AND 1500000;




-- Q8: Display all customers whose loan status is Approved

SELECT Customer_ID, Customer_Name, Loan_Status
FROM Loan
WHERE Loan_Status = 'Approved';




-- Q9: Find all customers whose payment status is Overdue

SELECT Customer_ID, Customer_Name, Payment_Status
FROM Loan
WHERE Payment_Status = 'Overdue';




-- Q10: Display loans where outstanding amount is greater than ₹2,00,000

SELECT Customer_ID, Customer_Name, Loan_Type, Outstanding_Amount
FROM Loan
WHERE Outstanding_Amount > 200000;




--------------------------------------------------------------
-- 2. FILTERING & SORTING (Q11–Q20)
--------------------------------------------------------------




-- Q11: Display the 10 largest loans

SELECT Customer_ID, Customer_Name, Loan_Amount
FROM Loan
ORDER BY Loan_Amount DESC
LIMIT 10;




-- Q12: Display customers in descending order of credit score

SELECT Customer_ID, Customer_Name, Credit_Score
FROM Loan
ORDER BY Credit_Score DESC;




-- Q13: Display customers in ascending order of loan amount

SELECT Customer_ID, Customer_Name, Loan_Amount
FROM Loan
ORDER BY Loan_Amount ASC;




-- Q14: Find loans with interest rates greater than 10%

SELECT Customer_ID, Customer_Name, Loan_Type, Interest_Rate
FROM Loan
WHERE Interest_Rate > 10;




-- Q15: Find customers between the ages of 25 and 40

SELECT Customer_ID, Customer_Name, Age
FROM Loan
WHERE Age BETWEEN 25 AND 40;




-- Q16: Find customers whose names start with A

SELECT Customer_ID, Customer_Name
FROM Loan
WHERE Customer_Name LIKE 'A%';




-- Q17: Find customers whose city contains the letter 'a'

SELECT Customer_ID, Customer_Name, City
FROM Loan
WHERE City LIKE '%a%';




-- Q18: Find customers who are not from Uttar Pradesh

SELECT Customer_ID, Customer_Name, State
FROM Loan
WHERE State <> 'Uttar Pradesh';




-- Q19: Find loans that are either Approved or Disbursed

SELECT Customer_ID, Customer_Name, Loan_Status
FROM Loan
WHERE Loan_Status IN ('Approved', 'Disbursed');




-- Q20: Find customers whose payment status is not Paid

SELECT Customer_ID, Customer_Name, Payment_Status
FROM Loan
WHERE Payment_Status <> 'Paid';




--------------------------------------------------------------
-- 3. AGGREGATE ANALYSIS (Q21–Q30)
--------------------------------------------------------------




-- Q21: Total number of loan applications

SELECT COUNT(*) AS TotalApplications
FROM Loan;





-- Q22: Total number of approved loans

SELECT COUNT(*) AS ApprovedLoans
FROM Loan
WHERE Loan_Status = 'Approved';




-- Q23: Total loan amount requested

SELECT SUM(Loan_Amount) AS TotalRequested
FROM Loan;




-- Q24: Total loan amount disbursed

SELECT SUM(Loan_Amount) AS TotalDisbursed
FROM Loan
WHERE Loan_Status = 'Disbursed';




-- Q25: Total outstanding loan amount

SELECT SUM(Outstanding_Amount) AS TotalOutstanding
FROM Loan;




-- Q26: Total overdue amount

SELECT SUM(Overdue_Amount) AS TotalOverdue
FROM Loan;




-- Q27: Average loan amount

SELECT AVG(Loan_Amount) AS AvgLoanAmount
FROM Loan;




-- Q28: Average interest rate

SELECT AVG(Interest_Rate) AS AvgInterestRate
FROM Loan;




-- Q29: Maximum loan amount

SELECT MAX(Loan_Amount) AS MaxLoanAmount
FROM Loan;




-- Q30: Minimum loan amount

SELECT MIN(Loan_Amount) AS MinLoanAmount
FROM Loan;




--------------------------------------------------------------
-- 4. AGGREGATE ANALYSIS (continued)
--------------------------------------------------------------




-- Q31: Average credit score

SELECT AVG(Credit_Score) AS AvgCreditScore
FROM Loan;




-- Q32: Average annual income of borrowers

SELECT AVG(Annual_Income) AS AvgAnnualIncome
FROM Loan;




--------------------------------------------------------------
-- 5. GROUP BY ANALYSIS (Q33–Q42)
--------------------------------------------------------------




-- Q33: Number of loans for each loan type

SELECT Loan_Type, COUNT(*) AS NumberOfLoans
FROM Loan
GROUP BY Loan_Type;




-- Q34: Total loan amount for each loan type

SELECT Loan_Type, SUM(Loan_Amount) AS TotalLoanAmount
FROM Loan
GROUP BY Loan_Type;




-- Q35: Average loan amount for each loan type

SELECT Loan_Type, AVG(Loan_Amount) AS AvgLoanAmount
FROM Loan
GROUP BY Loan_Type;




-- Q36: Total loan amount by city

SELECT City, SUM(Loan_Amount) AS TotalLoanAmount
FROM Loan
GROUP BY City;




-- Q37: Number of customers by state

SELECT State, COUNT(Customer_ID) AS NumberOfCustomers
FROM Loan
GROUP BY State;




-- Q38: Average credit score by loan type

SELECT Loan_Type, AVG(Credit_Score) AS AvgCreditScore
FROM Loan
GROUP BY Loan_Type;




-- Q39: Total outstanding amount by loan type

SELECT Loan_Type, SUM(Outstanding_Amount) AS TotalOutstanding
FROM Loan
GROUP BY Loan_Type;




-- Q40: Total overdue amount by city

SELECT City, SUM(Overdue_Amount) AS TotalOverdue
FROM Loan
GROUP BY City;




-- Q41: Number of loans by payment status

SELECT Payment_Status, COUNT(*) AS NumberOfLoans
FROM Loan
GROUP BY Payment_Status;




-- Q42: Number of loans by employment type

SELECT Employment_Type, COUNT(*) AS NumberOfLoans
FROM Loan
GROUP BY Employment_Type;




--------------------------------------------------------------
-- 6. HAVING CLAUSE (Q43–Q47)
--------------------------------------------------------------




-- Q43: Loan types having more than 5 loans

SELECT Loan_Type, COUNT(*) AS NumberOfLoans
FROM Loan
GROUP BY Loan_Type
HAVING COUNT(*) > 5;




-- Q44: Cities where total loan disbursement is greater than ₹50 lakh

SELECT City, SUM(Loan_Amount) AS TotalDisbursement
FROM Loan
GROUP BY City
HAVING SUM(Loan_Amount) > 5000000;




-- Q45: Loan types whose average loan amount is greater than ₹3 lakh

SELECT Loan_Type, AVG(Loan_Amount) AS AvgLoanAmount
FROM Loan
GROUP BY Loan_Type
HAVING AVG(Loan_Amount) > 300000;




-- Q46: Cities having total overdue amount greater than ₹1 lakh

SELECT City, SUM(Overdue_Amount) AS TotalOverdue
FROM Loan
GROUP BY City
HAVING SUM(Overdue_Amount) > 100000;




-- Q47: Employment types having more than 10 borrowers

SELECT Employment_Type, COUNT(Customer_ID) AS NumberOfBorrowers
FROM Loan
GROUP BY Employment_Type
HAVING COUNT(Customer_ID) > 10;




--------------------------------------------------------------
-- 7. CASE STATEMENT — RISK CLASSIFICATION (Q48–Q51)
--------------------------------------------------------------




-- Q48: Display customer name, credit score, and risk category

SELECT Customer_Name, Credit_Score,
CASE
    WHEN Credit_Score >= 750 THEN 'Low Risk'
    WHEN Credit_Score BETWEEN 650 AND 749 THEN 'Medium Risk'
    WHEN Credit_Score BETWEEN 550 AND 649 THEN 'High Risk'
    ELSE 'Very High Risk'
END AS RiskCategory
FROM Loan;




-- Q49: Count customers in each risk category

SELECT
CASE
    WHEN Credit_Score >= 750 THEN 'Low Risk'
    WHEN Credit_Score BETWEEN 650 AND 749 THEN 'Medium Risk'
    WHEN Credit_Score BETWEEN 550 AND 649 THEN 'High Risk'
    ELSE 'Very High Risk'
END AS RiskCategory,
COUNT(*) AS CustomerCount
FROM Loan
GROUP BY
CASE
    WHEN Credit_Score >= 750 THEN 'Low Risk'
    WHEN Credit_Score BETWEEN 650 AND 749 THEN 'Medium Risk'
    WHEN Credit_Score BETWEEN 550 AND 649 THEN 'High Risk'
    ELSE 'Very High Risk'
END;




-- Q50: Find the total outstanding amount for each risk category

SELECT
CASE
    WHEN Credit_Score >= 750 THEN 'Low Risk'
    WHEN Credit_Score BETWEEN 650 AND 749 THEN 'Medium Risk'
    WHEN Credit_Score BETWEEN 550 AND 649 THEN 'High Risk'
    ELSE 'Very High Risk'
END AS RiskCategory,
SUM(Outstanding_Amount) AS TotalOutstanding
FROM Loan
GROUP BY
CASE
    WHEN Credit_Score >= 750 THEN 'Low Risk'
    WHEN Credit_Score BETWEEN 650 AND 749 THEN 'Medium Risk'
    WHEN Credit_Score BETWEEN 550 AND 649 THEN 'High Risk'
    ELSE 'Very High Risk'
END;




--------------------------------------------------------------
-- 7. CASE STATEMENT — RISK CLASSIFICATION (continued)
--------------------------------------------------------------




-- Q51: Find the total overdue amount for each risk category

SELECT
CASE
    WHEN Credit_Score >= 750 THEN 'Low Risk'
    WHEN Credit_Score BETWEEN 650 AND 749 THEN 'Medium Risk'
    WHEN Credit_Score BETWEEN 550 AND 649 THEN 'High Risk'
    ELSE 'Very High Risk'
END AS RiskCategory,
SUM(Overdue_Amount) AS TotalOverdue
FROM Loan
GROUP BY
CASE
    WHEN Credit_Score >= 750 THEN 'Low Risk'
    WHEN Credit_Score BETWEEN 650 AND 749 THEN 'Medium Risk'
    WHEN Credit_Score BETWEEN 550 AND 649 THEN 'High Risk'
    ELSE 'Very High Risk'
END;




--------------------------------------------------------------
-- 8. BUSINESS KPI ANALYSIS (Q52–Q60)
--------------------------------------------------------------




-- Q52: Loan Approval Rate

SELECT
(SUM(CASE WHEN Loan_Status = 'Approved' THEN 1 ELSE 0 END) * 100.0 / COUNT(*)) AS ApprovalRate
FROM Loan;




-- Q53: Loan Rejection Rate

SELECT
(SUM(CASE WHEN Loan_Status = 'Rejected' THEN 1 ELSE 0 END) * 100.0 / COUNT(*)) AS RejectionRate
FROM Loan;




-- Q54: Average Loan Amount

SELECT AVG(Loan_Amount) AS AverageLoanAmount
FROM Loan;




-- Q55: Total Disbursed Amount

SELECT SUM(Loan_Amount) AS TotalDisbursedAmount
FROM Loan
WHERE Loan_Status = 'Approved';




-- Q56: Total Outstanding Amount

SELECT SUM(Outstanding_Amount) AS TotalOutstandingAmount
FROM Loan;




-- Q57: Total Overdue Amount

SELECT SUM(Overdue_Amount) AS TotalOverdueAmount
FROM Loan;




-- Q58: Average Credit Score

SELECT AVG(Credit_Score) AS AverageCreditScore
FROM Loan;




-- Q59: Default Customer Count

SELECT COUNT(*) AS DefaultCustomerCount
FROM Loan
WHERE Payment_Status = 'Default';




-- Q60: Percentage of Overdue Loans

SELECT
(SUM(CASE WHEN Overdue_Amount > 0 THEN 1 ELSE 0 END) * 100.0 / COUNT(*)) AS OverdueLoanPercentage
FROM Loan;




--------------------------------------------------------------
-- 9. DATE ANALYSIS (Q61–Q67)
--------------------------------------------------------------




-- Q61: Find loans applied for in a particular year

SELECT Customer_Name, Application_Date
FROM Loan
WHERE YEAR(Application_Date) = 2025;




-- Q62: Find loans approved during a particular month

SELECT Customer_Name, Approval_Date
FROM Loan
WHERE Loan_Status = 'Approved'
  AND MONTH(Approval_Date) = 2;




-- Q63: Find the number of loans applied for each year

SELECT YEAR(Application_Date) AS YearApplied,
       COUNT(*) AS LoanCount
FROM Loan
GROUP BY YEAR(Application_Date)
ORDER BY YearApplied;




-- Q64: Find the total loan amount disbursed each year

SELECT YEAR(Disbursement_Date) AS YearDisbursed,
       SUM(Loan_Amount) AS TotalDisbursed
FROM Loan
WHERE Loan_Status = 'Approved'
GROUP BY YEAR(Disbursement_Date)
ORDER BY YearDisbursed;




-- Q65: Find customers whose loan was approved but not yet disbursed

SELECT Customer_Name, Loan_ID, Loan_Amount
FROM Loan
WHERE Loan_Status = 'Approved'
  AND Disbursement_Date IS NULL;




-- Q66: Find the number of loans approved in each month

SELECT MONTH(Approval_Date) AS MonthApproved,
       COUNT(*) AS ApprovedLoanCount
FROM Loan
WHERE Loan_Status = 'Approved'
GROUP BY MONTH(Approval_Date)
ORDER BY MonthApproved;





-- Q67: Find the average number of days between application and approval

SELECT AVG(DATEDIFF(DAY, Application_Date, Approval_Date)) AS AvgDaysBetween
FROM Loan
WHERE Loan_Status = 'Approved';




--------------------------------------------------------------
-- 10. SUBQUERY CHALLENGES (Q68–Q73)
--------------------------------------------------------------



-- Q68: Find customers whose loan amount is greater than the average loan amount

SELECT Customer_Name, Loan_Amount
FROM Loan
WHERE Loan_Amount > (SELECT AVG(Loan_Amount) FROM Loan);




-- Q69: Find customers whose credit score is greater than the average credit score

SELECT Customer_Name, Credit_Score
FROM Loan
WHERE Credit_Score > (SELECT AVG(Credit_Score) FROM Loan);




-- Q70: Find the customer who has taken the highest loan amount

SELECT Customer_Name, Loan_Amount
FROM Loan
ORDER BY Loan_Amount DESC
LIMIT 1;




-- Q71: Find customers who have outstanding amounts greater than the average outstanding amount

SELECT Customer_Name, Outstanding_Amount
FROM Loan
WHERE Outstanding_Amount > (SELECT AVG(Outstanding_Amount) FROM Loan);




-- Q72: Find the loan type having the highest total loan amount

SELECT Loan_Type, SUM(Loan_Amount) AS TotalLoanAmount
FROM Loan
GROUP BY Loan_Type
ORDER BY TotalLoanAmount DESC
LIMIT 1;




-- Q73: Find customers whose annual income is greater than the average annual income

SELECT Customer_Name, Annual_Income
FROM Loan
WHERE Annual_Income > (SELECT AVG(Annual_Income) FROM Loan);




--------------------------------------------------------------
-- 11. ADVANCED SQL ANALYSIS (Q74–Q80)
--------------------------------------------------------------




-- Q74: Find the top 5 customers by total loan amount

SELECT Customer_Name, SUM(Loan_Amount) AS TotalLoan
FROM Loan
GROUP BY Customer_Name
ORDER BY TotalLoan DESC
LIMIT 5;




-- Q75: Find the top 3 cities by total loan disbursement

SELECT City, SUM(Loan_Amount) AS TotalDisbursement
FROM Loan
GROUP BY City
ORDER BY TotalDisbursement DESC
LIMIT 3;




-- Q76: Find the top 3 loan types by outstanding amount

SELECT Loan_Type, SUM(Outstanding_Amount) AS TotalOutstanding
FROM Loan
GROUP BY Loan_Type
ORDER BY TotalOutstanding DESC
LIMIT 3;




-- Q77: Find customers who have both credit score below 650 and overdue amount greater than ₹50,000

SELECT Customer_Name, Credit_Score, Overdue_Amount
FROM Loan
WHERE Credit_Score < 650
  AND Overdue_Amount > 50000;




-- Q78: Identify customers whose loan amount is high compared with their annual income

SELECT Customer_Name, Loan_Amount, Annual_Income
FROM Loan
WHERE Loan_Amount > Annual_Income;




-- Q79: Identify customers who have multiple loans

SELECT Customer_Name, COUNT(*) AS LoanCount
FROM Loan
GROUP BY Customer_Name
HAVING COUNT(*) > 1;




-- Q80: Find customers whose previous loan is closed but who have another active loan

SELECT DISTINCT l1.Customer_ID, l1.Customer_Name
FROM Loan l1
JOIN Loan l2 ON l1.Customer_ID = l2.Customer_ID
WHERE l1.Loan_Status = 'Closed'
  AND l2.Loan_Status = 'Active';


