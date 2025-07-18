### Creating OU Directory Structure
1. Navigate to the main Active Directory Users and Computers and extend the domain you are working with. In this case it is testlab.local
2. Right-clicking on the domain allows you to create an OU (Organizational Unit).  
      2. a. New → Organizational Unit
3. Here are some examples ways to organize your domain. This first example is a mixed/hybrid of the ones that proceed. Something like this is more common in real environments.
```
   testlab.local
├── Corporate
│   ├── Users
│   │   ├── Sales
│   │   ├── IT
│   │   └── HR
│   ├── Computers
│   │   ├── Workstations
│   │   └── Servers
│   └── Groups
├── Branch Offices
│   ├── New York
│   ├── Chicago
│   └── Remote
├── Special Accounts
│   ├── Service Accounts
│   ├── Administrative
│   └── Contractors
└── Disabled Objects
    ├── Users
    └── Computers
```
3. a. Functional/Department based: organize by business function or department
```
├── Sales
├── Marketing  
├── IT
├── HR
├── Finance
├── Legal
├── Operations
├── Customer Service
```
3. b. Role-based: orgganized by job function across departments
```
├── Management
├── Executives
├── Contractors
├── Interns
├── Remote Workers
├── Part-Time Staff
```
3. c. Location-based: organize by physical or geographical location
```
├── New York Office
├── Los Angeles Office
├── London Office
├── Remote Employees
├── Building A
├── Building B
├── Floor 1
├── Floor 2
```
3. d. Asset-Type: organize different types of AD objects
```├── User Accounts
├── Computer Accounts
│   ├── Workstations
│   ├── Laptops
│   ├── Servers
│   └── Virtual Machines
├── Groups
│   ├── Security Groups
│   └── Distribution Groups
├── Service Accounts
├── Shared Mailboxes
```
3. e. Security-based: organize by security requirements or access levels
```
├── Standard Users
├── Privileged Users
├── Administrative Accounts
├── Service Accounts
├── Guest Accounts
├── High Security
├── Low Security
```
3. f. Status-based: organize by account status or lifecycle
```
├── Active Accounts
├── Disabled Accounts
│   ├── Terminated
│   ├── Suspended
│   └── On Leave
├── Temporary Accounts
├── Test Accounts
```
3. g. Project-based: organize by temporary projects or initiatives
```
├── Project Alpha Team
├── Migration Project
├── Audit Team
├── Special Projects
```
