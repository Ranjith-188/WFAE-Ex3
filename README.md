# Employee Leave Request Approval System

## Task 1 – BPMN 2.0 Process Model

<img width="1342" height="648" alt="image" src="https://github.com/user-attachments/assets/d913fe6a-71c8-46bb-932f-e59e387619c5" />


```text
## Flow Logic

Start
  ↓
Fetch Leave Balance
  ↓
Evaluate Leave Request (DMN)
  ↓
Routing Outcome
  ├── Insufficient Balance
  │       ↓
  │   Notify Employee
  │       ↓
  │      Reject
  │
  ├── Auto-Approve
  │       ↓
  │
  └── Manager Approval
          ↓
      Manager Review
        ├── Rejected → Notify Employee → End
        │
        └── Approved
              ↓
          Send to HR
              ↓
        Update Leave Balance
              ↓
        Notify Employee
              ↓
        Leave Approved
```

---

## Task 2 – DMN Decision Table

<img width="643" height="333" alt="image" src="https://github.com/user-attachments/assets/2a3f0261-8979-46a2-a75e-fd6b6f2337e6" />
<img width="1437" height="402" alt="image" src="https://github.com/user-attachments/assets/b7931154-7c56-4ff2-b5c0-7fda5f87ea29" />
<img width="903" height="279" alt="image" src="https://github.com/user-attachments/assets/71dc9a7a-5d3a-4a1e-afde-daebba742fc7" />


The DMN handles:

* Leave balance validation
* Leave type
* Number of leave days
* Automatic approval
* Manager approval
* Insufficient balance rejection

---

## Task 3 – Service Tasks vs User Tasks

### Service Tasks

Automated activities:

* Fetch Leave Balance
* Send to HR
* Update Leave Balance
* Notify Employee

### User Task

Human interaction:

* Manager Review / Approval

### Main Variables

```text
employeeId
employeeName
leaveType
days
availableBalance
managerId
balanceStatus
decision
```

---

## Task 4 – DMN Decision Placement

The solution uses **two DMN decision tables**:

1. **Balance Status Decision** – checks whether sufficient leave balance is available.
2. **Leave Approval Routing Decision** – determines automatic approval or manager approval.

This keeps the decision logic simple, organized, and easy to maintain.

---

## Project Files

```text
├── leave-request-approval.bpmn
├── leave-decisions.dmn
├── README.md
```
