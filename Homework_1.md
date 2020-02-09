### Part 1:

#### 1. Fundamentally, what decisions will Jasmine need to make? 

Jasmine will need to decide how much to invest in LendingClub, and how much money to allocate for other options in the investment. After deciding how much to invest in LendingClub, she will then need to decide the amount of loan to invest.


#### 2. What is Jasmine's objective when making these decisions? 

She will have to decide on the objective that would help her make as much money as possible. How will she use the data to help her in deciding which loan to invest to see the best return.
 
#### 3. How will she be able to distinguish 'better' decisions from 'worse' ones? 

Jasmine will make a better decision from taking a look at the actual outcome of the loans and finding how much returns she would get from the investment.

#### 4. Why would Jasmine even think past data might be helpful and how could she use past data to help make her decisions? 

Jasmine should look at past data to get insights into the types of loans that are being sold through LendingClub. By looking at past data, she could hopefully identify how future loans might pan out so that she can make a more educated decision when purchasing loans. When looking at past data, gather data to answer some of the following questions might help her make better decisions:
- Which types of loans might be paid earlier that the life of the loan?
- How soon would that early payment be?
- Which loan is likely to default?
- How fast would the default happen?


#### 5. Take a brief look at the data and the data dictionary, paying attention to the description of the attributes that describe the loans. How would you categorize these attributes? 

The attributes include things such as lender employment status, job title, annual income, loan interest rates, and total loan payment. There are several ways to categorize this data but the first step Jasmine might take would be to seperate categorical and numeric variables. For example, employment status or job title should be thought of as a categorical variable while annual income or FICO would be numerical attributes. From here, numerical values can be further categorized by unit. For example, there are several attributes pertaining to ratios (percentage), dollars, number of months/years, and dates.
   
#### 6. Which attributes do you think are the most important to an investor like Jasmine? 
 
Investors like Jasmine will be most interested in the return on their investments (either actual return or annualized return). Jasmine could calculate the return by using the data available to her. In Jasmine's case, the relevant variables for calculating the return are the loan status, the total payment, the funded amount, the fees generated, and the loan duration.

#### 7. Looking through the data, you might notice some variables seem related. For example, total_pymnt is likely strongly correlated to the loan status. Why are some variables related? 

Many of these variables are redundant in a sense depending on the configuration of the data. For instance, the `total_pymnt` variable is somewhat redundant if the loan_status is 'Fully Paid' since this value could be inferred by looking at the loan amount. Another instance of this is `zip_code` and `addr_state` as `zip_code` describes `addr_state`. And so much of this data is related because these variables are somewhat describing the same thing (either for convience or because there are edge cases which require them). 

#### 8. Why does this matter and how might you check?

This matters because it means some variables are essentially being counted twice and therefore will 'weigh' more in the resulting model. You could check by creating a regression model of these variables and looking for a correlation or just using your own intuition to determine what this data is telling you and which might be telling you the same thing.

#### 9. It is unclear whether the value for some variables is current as of when the data is downloaded or when the loan was issued. Give an example of such a variable and describe why this matters (in general for all variables).

Many of these variables are unclear on this front and most of them are ones that have to do with information about the borrower. For instance, `delinq_2yrs` is a variable that describes 'The number of 30+ days past-due incidences of delinquency in the borrower's credit file for the past 2 years'. It is unclear if this means the past 2 years from when the data was downloaded or then the load was issued. One could probably safely assume this is from when the loan was issued since it is unlikely that this value is kept up to date for all borrowers. However, this matters because if this is not the case, then a value liek `deling_2yrs` could be a data leak so to speak because it would be representing information we might not have at the time of issueing/grading a loan.

#### 10. How might you check to see if this is indeed correct?

Double check to see what the information was when the loan was issued (i.e. from a previous download time) to see if the values are the same.

### Part 2: 

#### 1. Download the datasets from ICON in the ‘Full Dataset’ folder. How many observations and features are in the full dataset?

There are 1763077 observastions in the full dataset.

#### 2. The '1712_download' and '1912_download' folders on ICON contain datasets downloaded in 2017 and 2019 for the same loans. Compare these two datasets, does anything appear amiss?

It looks as thought the 2017 dataset has a column that 2019 does not. This column is 'disbursement_method'. There are also many static columns (meaning the values in the columns did not change). This makes sense since we are looking at the same loan information. However, what's interesting is that where we see an interest rate change we might also expect to see an installment change (i.e. there was a refinance of the loan). There are some cases where this is not the case (35 rows).

#### 3. Remove all instances representing loans that are still current (those not in status 'Fully Paid', 'Charged-Off', or 'Default') and all loans issued before January 1, 2011 from the full dataset. Discuss the appropriateness of these filtering steps.

Removing these rows is appropriate because we don't know the outcome of these loans yet. We don't want to include data for our model where we don't know if our predicted outcome is correct or not.

#### 4. Visualize all the attributes in the file and turn in one visualization for a continuous variable and one visualization for a discrete variable. Are there any outliers? If yes, remove them and report which observations here.

#### 5. Save the resulting dataset including only following attributes: 

```
id, loan amnt, funded amnt, term, int rate, grade, emp length, home ownership, annual inc, verification status, issue_d, loan status, purpose, dti, delinq 2yrs, earliest cr line, open acc, pub rec, fico range high, fico range low, revol bal, revol util, total pymnt, and recoveries.
```

### Part 3:

#### 1. The most important data we will need in determining the return of each loan is the total payments that were received on each loan. There are two variables related to this information: total pymnt and recoveries. Investigate these two variables, and for each loan, determine the total payment made on each loan. Does the total pymnt variable include those recoveries, or do they need to be added on? Briefly describe how you came to your conclusion.

#### 2. A key measure we will need in working out an investment strategy is the return on each loan, defaulted or otherwise. Add these four new variables to the data. 

#### a. There is a ‘Calculating Loan Return’ handout in the Case Study folder on ICON. Refer to this handout for a description of three different return calculations. M3(1.2%) refers to Method 3 using a re-invest rate of 1.2% and M3(3%) refers to Method 3 using a re-invest rate of 3%.

##### b. If you are using python, the provided notebook contains the code to calculate each of the return methods. Add four return variables: M1, M2, M3(1.2%), M3(3%).

##### c. If you are using Rattle, use the formulas for each return calculation in the handout to add a column to your .csv file for each of the four calculations: M1, M2, M3(1.2%), M3(3%).

##### d. What is the mean and median return for each of the four return variables?
 
#### 3. LendingClub assigns a grade to each loan, from A through G. Use the dataset to answer the following questions:

##### a. How many loans are in each grade?

##### b. What is the default rate in each grade?

##### c. What is the average interest rate in each grade?

##### d. What is the average percentage (annual) return for each grade using each of the return calculations?

##### e. Calculate and describe the skewness and kurtosis for the interest rate attribute and each of the return attributes.

##### f. If you had to invest in one grade only, which loans would you invest in and why?