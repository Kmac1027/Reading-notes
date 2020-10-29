# Reading 14: Access Control (ACL)

## RBAC tutorial

[Link to Video](https://www.youtube.com/watch?v=C4NP8Eon3cA&ab_channel=Udacity)

## 5 steps to RBAC

- RBAC is nothing more than the idea of assigning system access to users based on their role within an organization. The system needs of a given workforce are analyzed, with users grouped into roles based on common job responsibilities and system access needs. Access is then assigned to each person based strictly on their role assignment. With tight adherence to access requirements established for each role, access management becomes much easier.

### RBAC implementation 

1. Inventory your systems

Figure out what resources you have for which you need to control access, if you don't already have them listed. Examples would include an email system, customer database, contact management system, major folders on a file server, etc. 

2. Analyze your workforce and create roles

You need to group your workforce members into roles with common access needs.  Avoid the temptation to have too many roles defined. Keep them as simple and stratified as possible.

For example, you might have a basic user role, which includes the access any employee would need, such as email and the intranet site. Another role might be a customer service rep, that would have read/write access to the customer database, and a customer database administrator, that would have full control of the customer database. 

3. Assign people to roles

Now that you have a list of roles and their access rights, figure out which role(s) each employee belongs in, and set their access accordingly. 

4. Never make one-off changes

Resist any temptation to make a one-off change for an employee with unusual needs. If you begin doing this, your RBAC system will quickly begin to unravel. Change the roles as required or add new ones when really necessary. 

5. Audit

Periodically review your roles, the employees assigned to them, and the access permitted for each. If you discover, for example, that a role has unnecessary access to a particular system, change the role and adjust the access level for all employees in that role. 

As an example, many healthcare organizations, given the need for regulatory compliance in controlling access to medical records, use RBAC to define exactly what access to medical records each type of clinician may need.  While a doctor might have almost unlimited access to the records of patients he/she manages, a receptionist might be limited to basic contact information needed to manage appointments.  Given the large number of staff members in well stratified roles, RBAC is an efficient way to control record access in compliance with HIPAA, and other regulations.

There are tools that can help with setting up RBAC. Many systems, such as Microsoft Active Directory, have built in roles that you can use as a starting point, which you can extend to fit your unique situation. You can also use an identity management system to automate the assignment of privileges based on role. 

## wiki - RBAC

[link to Wikepedia](https://en.wikipedia.org/wiki/Role-based_access_control)

[Back to code 401 notes](../401-Javascript.md)