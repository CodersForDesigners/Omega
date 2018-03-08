# Ω

> **An web based real-estate platform for displaying accurate project inventory, unit details and capturing leads.** The platform is a CMS for an spreadsheet document that contains all values and logic. The platform itself has no project specific data hard-coded in it; therefore making it entirely reusable.

# Sub-Repos

[Omega-FrontEnd](https://github.com/TeamLazaro/Omega-FrontEnd)

[Omega-Server](https://github.com/TeamLazaro/Omega-Server)

[Omega-EndPoint](https://github.com/TeamLazaro/Omega-EndPoint)

## Research Backlog
- Figure out TrueCaller's API
- How is static apartment data going to be queried on the Pricing Engine front-end? From memory? From a database on the server?
- Making AJAX request to cross-domain endpoints. For example, retrieving the Spreadsheet or an AWS Lambda endpoint
- If using AWS Lambda, where are static assets stored?
- How to store all the versions of the spreadsheet on AWS and how to update Lambda to use the latest version?

---

## Structure

#### Website Server (weekly maintenance)
- Website Code
- Front-end Boilerplate
	- Pricing Engine Code
	- pricing_spreadsheet.xlsx
	- sheets.js ( a.k.a. xlsx.js )
	- xlsx-calc.js
- Form Validation
	- PHP: Checks with TrueCaller and the CRM and returns

#### Omega Server (yearly maintenance)
- Node: Build a Queue ( Concurrency )
- Node: Log Enquirers ( File vs SQL vs MongoDB )
- PHP: pass data through the HTML Template
- PHP: pass the template through domPDF
- PHP: Save File
- PHP: return a response to Node ( success / failure )
- if success:: Node: Hands off the File and Form Data to Endpoints Server
- if failure:: Node: Communicate the failed Log ID with the Form data to us so that we may resolve it manually. Next we go about fixing the omega server and submit the customer data manually on their behalf on a bare-bones manual form.

#### Endpoints Server (monthly maintenance)
- Exposes single endpoint (eg: endpointserver.com/)
- PHP: Sends out email(s)
- PHP: Ingests lead to the CRM
- PHP: Other Miscellaneous endpoint actions

---

## Implementation Time-line

#### Phase 1
- **Front-end Boilerplate v1**
	- Pricing Engine Code
	- pricing_spreadsheet.xlsx
	- sheets.js ( a.k.a. xlsx.js )
	- xlsx-calc.js
- **Omega Server v1**
	- Node: Queue + Log	
	- PHP: PDF Generator
- **Form Validation v1**
	- True Caller API
	- ZOHO CRM API
- **Endpoint Server v1**
	- PHP eMailer
	- ZOHO CRM

#### Phase 2
- **Front-end Boilerplate v2**
	- Pricing Engine Code
- **AWS Lambda v1**
	- pricing_spreadsheet.xlsx
	- sheets.js ( a.k.a. xlsx.js )
- **Omega Server v2**
	- Log Monitor
	- xlsx-calc.js (Version Control File Manager)
	- PDF File (File Manager)
- **Endpoints v2**
	- ZOHO Campaigns
	- SMS


