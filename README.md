# Visitor Management System (ServiceNow)

A ServiceNow application for managing visitor registration, host approvals, and receptionist-led check-in/check-out operations through a unified portal.

**Platform:** ServiceNow Personal Developer Instance (PDI)  
**Application:** Visitor Management System  
**Scope:** Custom scoped application

## Problem Statement

Manual visitor handling can make it difficult to maintain accurate visitor records, coordinate host approvals, and track who has entered or left an organization. A centralized process is needed to capture visitor details, route requests to the appropriate host, and maintain a clear visit-status history.

## Solution

Link - https://saigautam3.github.io/Visitor-Management-System/

The Visitor Management System provides a centralized ServiceNow portal with three main areas:

- **Dashboard & Reports** – summary of visitor activity and visit statuses.
- **Visitor Registration** – captures visitor information, visit purpose, host employee, and scheduled visit date/time.
- **Receptionist** – allows reception staff to review visits and perform permitted check-in/check-out actions.

New visitor requests are submitted for host approval. The approval flow updates the visit status based on the host's decision. Reception staff can then manage the visit lifecycle from the portal.

## Key Features

- Visitor registration with contact, company, visitor type, purpose, host, and visit date/time details.
- Host employee selection using active ServiceNow users.
- Host approval workflow using Flow Designer.
- Dashboard statistics for total visits, pending approvals, today's visits, checked-in visitors, completed visits, and rejected requests.
- Receptionist view of visitor records and visit details.
- Check-in and check-out status updates from the portal.
- Automatic check-in and check-out timestamps through Business Rules.
- Business Rule safeguards to prevent invalid check-in/check-out and reopening of completed or rejected visits.

## Application Modules

| Module | Description |
|---|---|
| Dashboard & Reports | Displays visitor activity and status summaries. |
| Visitor Registration | Collects visitor details and submits requests for approval. |
| Receptionist | Supports operational visit management, including check-in and check-out. |
| Host Approval | Routes requests to the selected host and processes the approval outcome. |

## Workflow

1. A user enters visitor and visit details.
2. The application creates a visitor record with **Pending Approval** status.
3. Flow Designer sends an approval request to the selected host employee.
4. If approved, the visit status becomes **Scheduled**; if rejected, it becomes **Rejected**.
5. Reception staff checks in a scheduled visitor.
6. When the visit ends, reception staff checks out the visitor.
7. Business Rules populate the corresponding timestamps and enforce visit lifecycle safeguards.

## Technology Stack

- **ServiceNow Platform** – application platform and data layer.
- **Service Portal** – portal interface and widgets.
- **HTML** – widget structure.
- **CSS** – responsive styling and interface presentation.
- **AngularJS (Service Portal client controller)** – client-side interactions and widget behavior.
- **JavaScript (server-side ServiceNow scripting)** – server logic and record operations.
- **GlideRecord** – visitor and host record operations.
- **GlideAggregate** – dashboard count calculations.
- **Flow Designer** – host approval workflow.
- **Business Rules** – timestamp automation and status-transition safeguards.
- **sys_user** – host employee reference data.

## Data Model

The application uses a custom Visitor Visit table:

`x_2061288_visito_0_visitor_visit`

Key fields include visitor name, visitor type, visitor email, contact number, company, host employee (reference to `sys_user`), visit purpose, purpose category, visit date/time, visit status, check-in time, and check-out time.

## Visit Statuses

- Pending Approval
- Scheduled
- Checked In
- Checked Out
- Cancelled
- Rejected

## Business Rules

The application includes Business Rules for:

- Setting check-in time when a visitor is checked in.
- Setting check-out time when a visitor is checked out.
- Preventing check-in/check-out for cancelled or rejected visits.
- Preventing re-check-in after check-out.
- Preventing reopening of completed visits.
- Preventing reopening of rejected visits.

## Screenshots

Add screenshots of the Dashboard, Visitor Registration, Receptionist interface, and approval workflow to the `assets/` folder. The project webpage can then display the actual implementation images.

## Project Structure

```text
Visitor-Management-System/
├── assets/
│   └── (project screenshots)
├── index.html
└── README.md
```

## Running the Project

This project is implemented inside a ServiceNow Personal Developer Instance. It is not a standalone application that can be run locally with Node.js.

To explore the implementation, access to the configured ServiceNow instance and appropriate roles is required. The `index.html` file in this repository is a project showcase page, not an export of the ServiceNow application itself.

## Future Enhancements

- Role-based access refinements for employees, hosts, and reception staff.
- Visitor notifications and reminders.
- Visitor badge or QR-code generation.
- More detailed analytics and downloadable reports.
- Calendar-based visit scheduling.

## Author

**Sai Gautam**  

