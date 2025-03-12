PLP 1

The PPLSC is calculated using data from Services Australia and matched to the correct individual, ensuring payment to the appropriate superannuation fund or SHAsa account if no valid fund is found within two years.
Any unpaid PPLSC entitlements not assigned to a superannuation fund within two years will be transferred to the individual's SHAsa account, provided the amount is above the minimum threshold.
The ATO will recalculate PPLSC entitlements when Services Australia updates the PPL data, making additional payments or recovering overpayments as needed.
The ATO automatically generates and sends correspondence to individuals with PPLSC entitlements, including determination letters, unassigned fund notifications, and annual statements, based on client preferences through MyGov or GAC Batch.
The ICP form captures all relevant details of the PPLSC calculation, including total entitlement, payment date, and destination (superannuation fund or SHAsa), and is accessible by ATO staff with updates for any changes.

PLP2
- The system finds newly posted PPLSC forms, creates an Aggregation Request, and processes transactions for the current and previous financial years.  
- It checks for any issues, like suppressed or deceased status, and looks for a valid destination for remittance or recovery.  
- When a valid destination is found, it calculates interest based on PPLSC rules and stores the details in a new form, which will be used to send information to the individual.  
- Aggregation groups amounts by provider, creating remittance or recovery roles for each super fund. It debits the individual’s PPLSC role and credits the super fund’s role accordingly.  
- After aggregation, the system creates and sends correspondence to the individual. For SMSF funds, PPLSC amounts are included in the SG remittance, and amounts are sent to super providers via RBA.

Listo

1. **Cyclical Changes for SEO Tools**: Updates are necessary for various SEO systems and tools to support the super system administration, impacting products like Super Guarantee, Low Income Super Tax Offset, and Co-Contributions.

2. **Superannuation Guarantee (SG) Changes**: Modifications are required for the SG contribution rate across multiple calculators, including the SG contributions calculator, SG charge statement calculator, and SG estimate tool, with CRDR uplifted for testing.

3. **SG Max Super Contributions Base**: Adjustments to the SG max super contributions base, including updates to the SG estimate tool with CRDR uplifted for testing.

4. **Low Income Super Tax Offset (LISTO)**: Changes include the application of LISTO for up to 3 prior years, with updates to the LISTO year on the calculator.

5. **Co-Contribution Updates**: Changes to the Co-Contributions calculator for the current year and up to 3 prior years, including updates to income thresholds and variables in the ICP code table.

CCAPS

1. **Cyclical Changes for SEO Systems**: Various SEO tools and systems need updates to support the administration of the super system, impacting key products like Contribution Caps and Transfer Balance Caps.
  
2. **Contribution Caps (CCAPS) Updates**: Changes are required for the CC Annual Basic Cap, ECC Deminimis, NCC Annual Basic Cap, ENCC Deminimis, and other related tools, effective in June 2025.

3. **Transfer Balance Cap Adjustments**: Updates for Transfer Balance Cap (TBC), including criteria for indexation, ensuring proper calculations and acceptance of related parameters.

4. **Outcome and Configuration Details**: A table details necessary changes for individual calculations, tools, and configurations for the products listed above.

5. **Correct Issue of Determinations**: Ensure accurate issuing of ECC, ENCC, and DIV293 determinations by setting 'In Calculate' and 'In Issue' flags correctly.




Div 296 Noa and Noaa

- A new Div 296 Tax Notice of Assessment (NOA) must be generated for clients with a new tax assessment, except when negative earnings calculations are present. The due date is 84 days from the issue date unless the amount is deferred.
- Amended Div 296 Notice of Assessment (NOAA) is required if there are changes to a previously issued assessment. The new amounts must be included, and the due date for additional payable amounts is 84 days from the NOAA issue date.
- Both the NOA and NOAA will be accompanied by a fund hierarchy listing funds subject to a default release authority.
- An outbound correspondence letter, including a payslip with payment information, will be sent to the individual based on their communication preferences and recorded in the Siebel CCH system.
- A MyGov notification will be sent to the individual's MyGov account when a NOA or NOAA is issued. If the assessment is below $700 for an original assessment, no letter will be sent to the client.

==========

DADL Ras


- A new DADL RAS form is introduced to capture Div 293 and Div 296 data sent by Superfunds, enabling individuals to release amounts from their Superfund to pay deferred debts.
- Individuals receive a Div 293 DADL letter from the ATO with a Release Authority Statement (RAS), which they can take to their Superfund to request a debt payment.
- The Superfund processes the RAS, sends the payment to the ATO, and mails the completed form back to the ATO, which then scans and stores it in Siebel.
- A new manual procedure requires ATO staff to input the DADL RAS data into the new ICP form, which will eventually be automated in a future release.
- The form includes manually adjustable fields and will trigger errors if mandatory fields are missing or information is keyed incorrectly. It will be accessed through ICP by ATO staff.

========

Div296 SOA

- The ATO processes a **Statement of Account (SOA)** through a batch service, which includes the individual’s Div 296 tax assessment information.
- The **SOA correspondence** is sent to the individual, providing a detailed summary of their Div 296 tax situation.
- Upon receiving the **SOA**, the individual reviews the information provided by the ATO, including their Div 296 tax debt details.
- Individuals can also access and view their **Div 296 information** via ATO Online for Individuals, providing easy access to their tax data.
- The **ATO Online for Individuals** will offer a new **Single Page Application (SPA)**, allowing individuals to conveniently view their Div 296 tax assessment data in one place.

=====

Identify triggers


- The **Div 296 Trigger service** runs on a scheduled basis, checking various ATO data sources to identify new Div 296 candidates or any changes in data since the last assessment.
- The service checks for any **new Superfund memberships** for individuals previously identified as Div 296 candidates and processes them accordingly.
- From the **2025-26 fiscal year onwards**, Div 296 tax assessment triggers must be inserted into a trigger table, and MAACOS will check for new non-SMSF accounts, triggering additional actions like sending an RFI and creating a new candidate form.
- A trigger will only be inserted when **all necessary data** (RFI, balance information, and due date for lodgement) has been received and the required 45-day window has passed.
- Changes to key factors (e.g., **TSB adjustments**, withdrawals, contributions, or verified date of death) will trigger updates in the Div 296 candidate's tax assessment, including recalculating adjusted TSB values.

=====

SAR changes


- **SMSF Annual Return (SAR)** can be lodged electronically or via paper. When lodged electronically, SBR sends the SAR to ICP via EAI for processing; if lodged on paper, the SAR is scanned and sent to ICP.
- Starting from the **2025-26 financial year**, the SAR will be updated to include two new labels: **U (Division 296 tax contributions)** and **V (Division 296 tax withdrawals)**, both of which will accept zero as a valid value.
- For **paper lodgments**, blank fields for labels U or V will be treated as zero, and OCR will capture these labels for processing. 
- During **electronic lodgments**, the system will validate labels U and V, and if left blank, a validation message will prompt the user to enter a value.
- The new labels will be captured in the **SAR form in ICP**, and once processed, the data will be unpacked to **EDW** for reporting purposes.

=========
Deferred account notification

- The **Evaluate Transaction service** identifies new Div 296 Deferred Debt accounts and roles created after a Div 296 Tax Assessment, generating correspondence requests for the **Generate Auto Correspondence** service.
- The **Generate Auto Correspondence** service sends notifications to Superfunds (including SMSFs with a USI) about the creation of a deferred debt account for defined benefit members, with correspondence grouped by **USI** or **ABN**.
- The data is transformed into a **PDF letter** by Outbound, triggering a **Siebel Work Management interaction**, which is recorded in the **Superannuation funds Client Contact History (CCH)** and stored in the Inbound/Outbound document library.
- Superfunds or Providers receive an **email notification** when a new file is available for download, prompting them to access and download the **PDF letter** from OSB.
- The system will be updated to include **new business processing rules** for Div 296 Tax Assessments, along with a **new correspondence template** and enhanced functionality for **file transfer** and **Access Manager permissions** for both APRA and SMSFs.
======

No fund Shasa

- The **ATO** will calculate the **Paid Parental Leave Superannuation Contribution (PPLSC)** based on data from **Services Australia** and match it to the eligible individual, ensuring payment to the correct superannuation fund or to the individual’s **SHAsa** account if no valid fund is identified within two years of the first PPL payment.
  
- **PPLSC entitlements** that have not been paid to an eligible fund within two years will automatically be transferred to the individual’s **SHAsa account** by the ATO, provided the entitlement is above the de minimis threshold.

- When **Services Australia amends** the PPL data, the ATO recalculates the **PPLSC entitlement**, and if necessary, will make additional payments or recover overpayments from superannuation funds or the SHAsa account.

- **Correspondence** is generated automatically by the ATO for individuals with PPLSC entitlements, including **PPLSC Determination** letters, notifications about unassigned funds, and annual statements, which will be sent based on client preferences via **MyGov** or **GAC Batch**.

- The **ICP form** will capture all relevant details of the PPLSC calculation, including the **total entitlement**, payment date, and destination (either superannuation fund or SHAsa), which will be viewable by ATO staff and updated with any amendments or cancellations.
===========

PPL Calculation

- **Transaction Evaluation and Aggregation**: The system identifies newly posted PPLSC forms, creates an Aggregation Request transaction, and processes transactions for the current and prior financial years. Aggregation checks for any suppressions or deceased status and proceeds to find a valid destination for remittance or recovery.

- **Credit Interest Calculation**: Once a valid destination is found, credit interest is calculated according to PPLSC rules. Details of the destination fund and credit interest calculations are stored in a new PPL Payment Details form, which will be used to generate correspondence for the individual.

- **Collation and Creation of Roles**: Aggregation collates amounts by provider, creating new PPLSC remittance or recovery roles for each super fund (USI or Superannuation account). It will debit the individual's PPLSC role and credit the super fund’s remittance or recovery role based on whether it’s for remittance or recovery.

- **Credit Balance Request and Approval**: Aggregation creates a pending credit balance request, which is approved by the Evaluate Transaction process. New rules will create a correspondence request transaction for remittance or recovery amounts, including those for early payments, and send them to APRA funds.

- **Correspondence and Disbursement**: Once aggregation is complete, the system triggers the creation of correspondence for the individual, and the details are sent to outbound services for delivery. For SMSF funds, PPLSC amounts are included in the SG remittance, and aggregated amounts are sent to super providers via RBA following existing processes.
========

SEO cyclical

- **Individual Income Tax Return (IITR) Updates**: Updates and configurations are required for the 2024-25 Individual Income Tax Return (IITR), including validation and new configurations for various tax calculations.

- **Defined Benefit Income Cap (DBIC) Tool**: The 2024-25 financial year needs to be added for selection in the DBIC tool, along with confirming the DBIC validation rule for Tax Offset T2 returns for accurate results.

- **Tax Offset Validation**: PLS (Personal Lump Sum) and ICP (Individual Contribution Payment) systems require validation of tax offset amounts to ensure correct processing.

- **Super Lump Sum Caps**: Validation and updates are necessary for superannuation lump sum caps, including the lifetime and death benefit low rate caps and the untaxed plan cap.

- **ETP Cap Adjustments**: Adjustments and validations are needed for the ETP (Eligible Termination Payment) cap regarding life benefit and death benefit term payments.
=======

Exclude DASP


- **Manual Intervention for Cheque Claims**: When processing direct claims for cheques of $6,000 or less from ATO-held super, an aggregation rule prevents automatic cheque issuance, requiring manual intervention to create a credit balance request (CBR).

- **Aggregation Rule Implementation**: The aggregation rule was introduced as part of the Inactive Low Balance Accounts (ILBA) initiative in 2019/20 to reduce stale cheques and provide additional time for ATO to update Financial Institution Details (FID).

- **Challenges for Former Temporary Residents (FTRs)**: FTRs, who may have left Australia and closed their accounts, often do not provide updated FID details, causing delays in processing their claims and payments.

- **Payment Delays for FTRs**: The current aggregation rule delays cheque payments while waiting for updated FID details, which is highly unlikely to be obtained for FTRs.

- **Proposed Change to Aggregation Rule**: A mandatory change to the aggregation rule is required to allow automatic cheque issuance for FTR claims, provided the client is a FTR, the disbursement method is a cheque, and the credit balance is $6,000 or less.
======







