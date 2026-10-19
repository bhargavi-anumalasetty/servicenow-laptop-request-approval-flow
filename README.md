# Laptop Request Approval Workflow (ServiceNow Service Catalog + Flow Designer)

A self-directed project built on a ServiceNow Personal Developer Instance (PDI). An employee orders a laptop from the Service Catalog, a Flow Designer flow sends the request for approval, and the request closes based on the decision.

## What it does

1. **Catalog item:** `Request a New Laptop` with form variables such as laptop type and business justification.
2. **Flow:** `Laptop Request Approval Flow` in Flow Designer, started by the Service Catalog trigger.
3. **Approval:** the **Ask For Approval** action sends an approval to the approver, and the flow waits for the decision.
4. **Outcome:** If/Else logic updates the requested item.
   - Approved: State becomes **Closed Complete**
   - Rejected: State becomes **Closed Incomplete**

## Tested

| Test | Result |
|---|---|
| Order a laptop, approve it (RITM0010003) | State: Closed Complete |
| Order a laptop, reject it (RITM0010002) | State: Closed Incomplete |

## ServiceNow terms used

Service Catalog, catalog item, variables, Request (REQ) and Requested Item (RITM), Flow Designer, trigger, action, data pills, flow logic, approvals, flow execution.

## Screenshots

**Catalog item and variables**

![Catalog item](catalog-item.png)

**The finished flow**

![Finished flow](flow.png)

**Flow execution (Completed)**

![Flow execution completed](execution-completed.png)

**Approved request: State Closed Complete**

![Approved result](result-approved.png)

**Rejected request: State Closed Incomplete**

![Rejected result](result-rejected.png)

## Limitations and next steps

- The approver is a fixed user (me), because this is a practice instance.
- **Closed Complete** only marks the request as finished in this demo. A real process would add fulfilment tasks (ordering, delivery) before closing.
- The flow updates **State** only. The catalog **Stage** field is not updated by this flow.
- Possible improvements: manager as approver, email notifications, and fulfilment tasks.

## Notes

This is a self-directed learning project on a personal developer instance, not production or client work.
