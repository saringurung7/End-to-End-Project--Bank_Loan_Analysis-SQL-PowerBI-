
# Bank Loan Analysis

## Problem Statement

The dashboard provided stakeholders with actionable insights into the bank's loan portfolio by tracking key performance indicators (KPIs) and analyzing loan quality, repayment trends, and borrower demographics. It helped identify monthly trends in loan demand, funding, and repayment consistency, allowing for improved cash flow and risk management. By differentiating between "Good" and "Bad" loans, stakeholders could assess overall loan quality and make informed decisions to enhance portfolio health. Additionally, regional and demographic breakdowns, such as loan distribution by state, loan purpose, and borrower profiles, enabled targeted strategies for high-potential regions and borrower segments. 


### Steps followed 

- Step 1 : Load Data into SQL: The initial step involved importing the CSV dataset into SQL, preparing it for structured analysis and enabling efficient data handling.
- Step 2 : Create Database: A dedicated database was created to store loan data, ensuring organized storage for streamlined querying and analysis.
- Step 3 : SQL Analysis: Using SQL, specific queries were designed as per the problem statement to extract required KPIs and insights. The output was stored and documented, establishing a clear basis for loan metrics and trends.
- Step 4 : Connect SQL to Power BI: The final step was to connect Power BI to the SQL database, allowing the visual dashboard to be directly compared with SQL output for accuracy. This integration enabled real-time data visualization, showcasing insights through interactive graphs and charts in Power BI.

### SQL analysis 

KPI's:

    1. Total Loan Applications:
    select count(id) as total_loan_application from bank_loan_data;

 ![image](https://github.com/user-attachments/assets/d10eac22-2101-4c01-a9cb-daf1540ade01)

    2. MTD Loan application:
    select count(id) as MTD_total_loan_application from bank_loan_data  
    where month(str_to_date(trim(issue_date),'%d-%m-%Y')) = 12 
    and year(str_to_date(trim(issue_date),'%d-%m-%Y'))= 2021;

![image](https://github.com/user-attachments/assets/3c52c49b-9f48-4ed9-8861-7a8610eb16d2)

    3. Previous MTD (PMTD) Loan Application
    select count(id) as PMTD_total_loan_application from bank_loan_data
    where month(str_to_date(trim(issue_date),'%d-%m-%Y')) = 11 
    and year(str_to_date(trim(issue_date),'%d-%m-%Y'))= 2021;

![image](https://github.com/user-attachments/assets/da3a3699-6624-4dd2-96a3-88a0f8f13dc4)

    4. Total Funded Amount
    select sum(loan_amount) as total_funded_amount from bank_loan_data;

![image](https://github.com/user-attachments/assets/df6b819e-b29f-4845-aa3e-1b8e6c88f43f)

    5. MTD Funded Amount
    select sum(loan_amount) as MTD_total_funded_amount from bank_loan_data
    where month(str_to_date(trim(issue_date),'%d-%m-%Y')) = 12 
    and year(str_to_date(trim(issue_date),'%d-%m-%Y'))= 2021;

![image](https://github.com/user-attachments/assets/a06df2c3-6937-4355-846c-6e24aa604f96)

    6. Previous MTD (PMTD) Funded Amount
    select sum(loan_amount) as PMTD_total_funded_amount from bank_loan_data
    where month(str_to_date(trim(issue_date),'%d-%m-%Y')) = 11 
    and year(str_to_date(trim(issue_date),'%d-%m-%Y'))= 2021;

![image](https://github.com/user-attachments/assets/3a3e41a7-3ef1-429d-a7af-14f83c1a0c84)

    7. Total Amount Received
    select sum(total_payment) as total_received_amount from bank_loan_data;

![image](https://github.com/user-attachments/assets/fad7ffd7-71ef-4d95-87f0-91c10b323050)

    8.  MTD Amount Received
    select sum(total_payment) as MTD_total_received_amount from bank_loan_data
    where month(str_to_date(trim(issue_date),'%d-%m-%Y')) = 12 
    and year(str_to_date(trim(issue_date),'%d-%m-%Y'))= 2021;

![image](https://github.com/user-attachments/assets/4e7eba0b-23e2-404d-b854-232c2f9ac9a4)

    9. Previous MTD (PMTD) Amount Received
    select sum(total_payment) as PMTD_total_received_amount from bank_loan_data
    where month(str_to_date(trim(issue_date),'%d-%m-%Y')) = 11 
    and year(str_to_date(trim(issue_date),'%d-%m-%Y'))= 2021;

![image](https://github.com/user-attachments/assets/1bb682e9-b551-49fa-b7bb-c1dd5335caf4)

    10. Average Interest Rate
    select avg(int_rate) * 100 as avg_int_rate from bank_loan_data;

![image](https://github.com/user-attachments/assets/86ef4c3a-e178-4be7-9b8c-03a39ca8eb47)

    11. MTD Average Interest Rate
    select avg(int_rate) * 100 as MTD_avg_int_rate from bank_loan_data
    where month(str_to_date(trim(issue_date),'%d-%m-%Y')) = 12 
    and year(str_to_date(trim(issue_date),'%d-%m-%Y'))= 2021;

![image](https://github.com/user-attachments/assets/ed2bfd39-367b-4021-9d1e-c2457b5497aa)

    12. PMTD Average Interest Rate
    select avg(int_rate) * 100 as PMTD_avg_int_rate from bank_loan_data
    where month(str_to_date(trim(issue_date),'%d-%m-%Y')) = 11 
    and year(str_to_date(trim(issue_date),'%d-%m-%Y'))= 2021;

![image](https://github.com/user-attachments/assets/11d55a08-f8d9-4ea3-96eb-63b706f858a1)

    13. Average Debt to Income Ratio DTI
    select avg(dti) * 100 as avg_dti from bank_loan_data;

![image](https://github.com/user-attachments/assets/3ee191d6-bc89-4a18-b6cf-2486cf29eb49)

    14. MTD Average Debt to Income Ratio DTI
    select avg(dti) * 100 as avg_dti from bank_loan_data
    where month(str_to_date(trim(issue_date),'%d-%m-%Y')) = 12 
    and year(str_to_date(trim(issue_date),'%d-%m-%Y'))= 2021;

![image](https://github.com/user-attachments/assets/708d2656-aeba-45e9-b828-fcfb0327c416)

    15. PMTD Average Debt to Income Ratio DTI
    select avg(dti) * 100 as PMTD_avg_dti from bank_loan_data
    where month(str_to_date(trim(issue_date),'%d-%m-%Y')) = 11 
    and year(str_to_date(trim(issue_date),'%d-%m-%Y'))= 2021;

![image](https://github.com/user-attachments/assets/691a8d94-023d-46cb-a798-729190bbc9eb)

    GOOD LOAN ISSUED
    1. Good loan percentage
    select 
    (count(case when loan_status = 'Fully Paid' or loan_status='Current' then id end) / count(id) *100)  as good_loan_percentage
    from bank_loan_data;

![image](https://github.com/user-attachments/assets/7514b9d6-9a13-4d3d-bbd2-837c5acb8add)

    2. Good loan application
    select count(id) as good_loan_application from bank_loan_data
    where loan_status in ('Current','Fully Paid');

![image](https://github.com/user-attachments/assets/62bdba97-f1c0-458e-8324-511fc7e7862a)

    3. Good loan funded amount
    select sum(loan_amount) as good_loan_funded_amount from bank_loan_data
    where loan_status in ('Current','Fully Paid');

![image](https://github.com/user-attachments/assets/ac1fd6f3-8f7e-4f2a-824a-a38240890131)

    4. Good loan total received amount
    select sum(total_payment) as good_loan_received_amount from bank_loan_data
    where loan_status in ('Current','Fully Paid');

![image](https://github.com/user-attachments/assets/b7907601-e5e2-49f3-8cbf-cd4589654df3)

    BAD LAON ISSUED
    1. Bad laon percentage
    select
    (count(case when loan_status = 'Charged Off' then id end) / count(id) *100) as bad_loan_percentage
    from bank_loan_data;

![image](https://github.com/user-attachments/assets/e700abbe-f81c-4710-9837-1cfeb9eced15)

    2. Bad loan application
    select count(id) as bad_loan_application from bank_loan_data
    where loan_status = 'Charged Off';

![image](https://github.com/user-attachments/assets/e3f4f0c1-4b30-4266-8d21-18bb7ede4197)

    3. Bad loan funded amount
    select sum(loan_amount) as bad_loan_funded_amount from bank_loan_data
    where loan_status = 'Charged Off';

![image](https://github.com/user-attachments/assets/5724048d-f680-47c4-b8ee-4f6c2bd214da)

    4. Bad loan total received amount
    select sum(total_payment) as bad_loan_received_amount from bank_loan_data
    where loan_status = 'Charged Off';

![image](https://github.com/user-attachments/assets/74c046e5-4402-46d1-a883-6fe315f3e9ad)

    LOAN STATUS
    select loan_status
    , count(id) as loan_count
    , sum(total_payment) as total_amt_received
    , sum(loan_amount) as total_funded_amt
    , avg(int_rate) *100 as int_Rate
    , avg(dti) *100 as dti
    from bank_loan_data
    group by loan_status
    order by loan_count desc;

![image](https://github.com/user-attachments/assets/c8917a38-44be-4c0b-828e-56e37fa53860)

    LOAN STATUS MTD wise
    select loan_status
    , sum(total_payment) as MTD_total_amt_received
    , sum(loan_amount) as MTD_total_funded_amt
    from bank_loan_data
    where month(str_to_date(trim(issue_date),'%d-%m-%Y')) = 12
    group by loan_status;

![image](https://github.com/user-attachments/assets/57c4c4bb-ffe0-4b2c-b6b7-1a02bf87e880)

    METRICS of Total loan application, Total Funded Amount, Total Amount Received
    1. Monthly trends analysis by issue date
    select month(str_to_date(trim(issue_date),'%d-%m-%Y')) as month_number
    , monthname(str_to_date(trim(issue_date),'%d-%m-%Y')) as month_name
    , count(id) as total_loan_application
    , sum(loan_amount) as total_funded_amt
    , sum(total_payment) as total_amt_received
    from bank_loan_data
    group by month(str_to_date(trim(issue_date),'%d-%m-%Y'))
    , monthname(str_to_date(trim(issue_date),'%d-%m-%Y'))
    order by month(str_to_date(trim(issue_date),'%d-%m-%Y'));

![image](https://github.com/user-attachments/assets/6775c602-eb0b-4ee9-861b-c929f7bcbe70)

    2. Regional analysis by state
    select address_state as state
    , count(id) as total_loan_application
    , sum(loan_amount) as total_funded_amt
    , sum(total_payment) as total_amt_received
    from bank_loan_data
    group by state
    order by state;

![image](https://github.com/user-attachments/assets/c545e645-ede7-4bcb-bf21-2d015eba0168)

    3. Loan term analysis
    select term
    , count(id) as total_loan_application
    , sum(loan_amount) as total_funded_amt
    , sum(total_payment) as total_amt_received
    from bank_loan_data
    group by term
    order by term;

![image](https://github.com/user-attachments/assets/eab2aace-a22f-4499-bae1-d1a3817080e7)

    4. Employee length analysis
    select emp_length
    , count(id) as total_loan_application
    , sum(loan_amount) as total_funded_amt
    , sum(total_payment) as total_amt_received
    from bank_loan_data
    group by emp_length
    order by emp_length;

![image](https://github.com/user-attachments/assets/fd9c4114-ad47-4eaa-af8b-6007787aad3e)

    5. Loan purpose breakdown analysis
    select purpose as loan_purpose
    , count(id) as total_loan_application
    , sum(loan_amount) as total_funded_amt
    , sum(total_payment) as total_amt_received
    from bank_loan_data
    group by purpose
    order by purpose;

![image](https://github.com/user-attachments/assets/d0612644-b99e-4b80-9b38-73716a39ce73)

    6. Home Ownership analysis
    select home_ownership
    , count(id) as total_loan_application
    , sum(loan_amount) as total_funded_amt
    , sum(total_payment) as total_amt_received
    from bank_loan_data
    group by home_ownership
    order by home_ownership;
 
![image](https://github.com/user-attachments/assets/6d289fb2-d95b-469b-963d-fe8718f5f059)
 
 # Report Snapshot (Power BI DESKTOP)

 ![image](https://github.com/user-attachments/assets/752bfdba-5024-4669-a6be-c9e6f19f6217)


