# ServiceNow Script-Controlled ACL Project

## Project Title
**Script-Controlled ACL – Restrict Record Access Based on Field Value**

## Description
This project demonstrates how to implement a script-controlled Access Control List (ACL) in ServiceNow to restrict record access based on user roles and the value of a record field.

In this project, users with the required role can view records for the **EEE branch**, while administrators retain full access.

## Technologies
- ServiceNow
- Access Control Lists (ACL)
- User Roles
- Server-side ACL Script

## User and Roles
Test user:
- User ID: `EEE User`

Custom roles:
- `bb1` – Read access
- `bb2` – Create access
- `bb3` – Write access
- `bb4` – Delete access

## Custom Table
**Label:** Institution Details  
**Name:** `u_institution_details`

### Fields
- Student Roll Number – Auto Number
- Student Name – Reference (User)
- Faculty Name – Reference (User)
- Branch – Choice (ECE, EEE, CSE)
- Email – String
- Phone Number – String
- Description – Multi String

## ACL Implementation

### Read ACL
- Type: Record
- Operation: Read
- Table: `u_institution_details`
- Active: True
- Requires role: `bb1`
- Data condition: Branch is EEE
- Advanced: True

The ACL script allows administrators full access and allows users with the `bb1` role to access the required records.

### Create ACL
- Type: Record
- Operation: Create
- Table: `u_institution_details`
- Active: True
- Requires role: `bb2`

### Write ACL
- Type: Record
- Operation: Write
- Table: `u_institution_details`
- Active: True
- Requires role: `bb3`

### Delete ACL
- Type: Record
- Operation: Delete
- Table: `u_institution_details`
- Active: True
- Requires role: `bb4`

## Verification
- `bb1` users can view the EEE branch records.
- Users without the required role cannot access the protected records.
- Administrators can view all records.
- Users with `bb1` and `bb2` can view EEE records and use the New button.
- Users with `bb1`, `bb2`, and `bb3` can view and edit EEE records.
- Users with `bb1`, `bb2`, `bb3`, and `bb4` can view, create, edit, and delete EEE records.

## Project Outcome
This project provides an understanding of how READ, CREATE, WRITE, and DELETE ACLs enforce record-level security in ServiceNow. It demonstrates how user roles and record field values can be evaluated together to control access to sensitive data.

## Documentation
The complete project documentation is available in the PDF included in this repository.
