# Smart Lost & Found Management System

## ServiceNow-Based Workflow Automation Application

The **Smart Lost & Found Management System** is a ServiceNow-based application designed to digitize and automate the complete lifecycle of lost and found items.

The system provides a centralized platform for reporting lost and found items, identifying potential matches, managing claims, processing returns, and automatically notifying users about important status changes.

---

## Project Overview

Traditional lost-and-found processes are often managed using registers, spreadsheets, or informal communication. This makes it difficult to track items, identify potential matches, verify claims, and manage returns efficiently.

This project addresses these challenges by implementing a centralized workflow-driven solution using the **ServiceNow platform**.

The application manages the complete process:

**Report → Match → Claim → Verify → Approve → Return → Notify**

---

## Key Features

- Lost item reporting
- Found item reporting
- Centralized item management
- Potential lost/found item matching
- Claim submission and verification
- Automated claim status processing
- Automatic return record creation
- Return status management
- Automated email notifications
- Role-based access control
- Custom Service Portal interface
- Workflow automation using Flow Designer

---

## Technology Stack

| Technology | Purpose |
|---|---|
| ServiceNow | Application platform |
| App Engine Studio | Application development |
| Flow Designer | Workflow automation |
| UI Builder | Custom user interface |
| Service Portal | User-facing portal |
| ServiceNow Tables | Data management |
| Reference Fields | Table relationships |
| Email Notifications | Automated communication |
| ServiceNow PDI | Development and testing |

---

## Application Modules

### 1. Lost Items

Stores information about items reported as lost.

Key information includes:

- Item Name
- Category
- Description
- Color
- Brand
- Lost Date
- Lost Location
- Reported By
- Status
- Priority
- Contact Information

---

### 2. Found Items

Stores information about items that have been found.

Key information includes:

- Item Name
- Category
- Description
- Color
- Brand
- Found Date
- Found Location
- Found By
- Storage Location
- Status

---

### 3. Claims

Manages claims submitted by users for found items.

Key information includes:

- Lost Item
- Found Item
- Claimant
- Claim Description
- Proof Description
- Claim Status
- Verification Notes
- Claim Date

---

### 4. Item Returns

Manages the final return of an item to the verified claimant.

Key information includes:

- Claim
- Lost Item
- Found Item
- Returned To
- Return Date
- Return Status
- Handover Notes

---

## Workflow Automation

The application contains six major automated workflows developed using ServiceNow Flow Designer.

### Process New Lost Item Claim

Automatically moves a newly created claim into:

**Submitted → Under Verification**

### Find Potential Lost Item Match

Matches newly reported found items against lost items using:

- Category
- Color
- Brand

Potential matches are updated with the **Potential Match** status.

### Process Item Return

Automatically updates a newly created return record to:

**Ready for Pickup**

### Create Return for Approved Claim

When a claim is approved, the system automatically creates an Item Return record.

### Notify Claimant When Claim Approved

Automatically sends an email to the claimant when the claim is approved.

### Notify User When Item Is Returned

Automatically sends an email when the item return status becomes:

**Returned**

---

## Complete System Workflow

```text
                USER
                  |
          +-------+-------+
          |               |
          v               v
   Report Lost Item   Report Found Item
          |               |
          +-------+-------+
                  |
                  v
          Potential Match
                  |
                  v
            Submit Claim
                  |
                  v
          Claim Verification
                  |
          +-------+-------+
          |               |
       Rejected        Approved
                          |
                          v
                Return Record Created
                          |
                          v
                   Ready for Pickup
                          |
                          v
                    Item Returned
                          |
                          v
                  Email Notification
                          |
                          v
                    PROCESS COMPLETE
