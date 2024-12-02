# Zapier

Automation in Zapier is done with Triggers and Actions. Below are all triggers and actions available for Seven Time in Zapier.

## Triggers

### Customers
- New Customer
- Updated Customer

### Invoices
- New Invoice
- Updated Invoice

### Projects
- New Project
- Updated Project

### Tasks
- New Task
- Updated Task

### Timer
- <details>
    <summary>Timer started</summary>
      Using the following inputs, it is possible to track specific users, work orders etc.
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>user</td>
        <td>User</td>
      </tr>
      <tr>
        <td>workOrder</td>
        <td>Work order</td>
      </tr>
    <tr>
        <td>project</td>
        <td>Project</td>
      </tr>
    <tr>
        <td>customer</td>
        <td>Customer</td>
      </tr>
      <tr>
        <td>timeCategory</td>
        <td>Time category</td>
      </tr>
      <tr>
        <td>task</td>
        <td>Task</td>
      </tr>
    </table>
</details>

### Time logs
- New Time Log
- Updated Time Log

### Users
- Updated User

### Work orders
- New Work Order
- Updated Work Order


## Actions
### Customers
- <details>
    <summary>Get Customer by Name or Number</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>name</td>
        <td>Name</td>
      </tr>
      <tr>
        <td>customerNumber</td>
        <td>Customer number</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Get Customer by id</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>id</td>
        <td>ID</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Create Customer</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>createdByUser</td>
        <td>Created by user</td>
      </tr>
      <tr>
        <td>name</td>
        <td>Customer name</td>
      </tr>
      <tr>
        <td>customerNumber</td>
        <td>Customer number</td>
      </tr>
      <tr>
        <td>address</td>
        <td>Address</td>
      </tr>
      <tr>
        <td>address2</td>
        <td>Address 2</td>
      </tr>
      <tr>
        <td>zipCode</td>
        <td>Zip code</td>
      </tr>
      <tr>
        <td>city</td>
        <td>City</td>
      </tr>
      <tr>
        <td>country</td>
        <td>Country</td>
      </tr>
      <tr>
        <td>phone</td>
        <td>Phone</td>
      </tr>
      <tr>
        <td>email</td>
        <td>Email</td>
      </tr>
      <tr>
        <td>organizationNumber</td>
        <td>Organization number</td>
      </tr>
      <tr>
        <td>vatNumber</td>
        <td>VAT number</td>
      </tr>
      <tr>
        <td>paymentDays</td>
        <td>Payment days</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Update Customer</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>id</td>
        <td>ID</td>
      </tr>
      <tr>
        <td>modifiedByUser</td>
        <td>Modified by user</td>
      </tr>
      <tr>
        <td>name</td>
        <td>Customer name</td>
      </tr>
      <tr>
        <td>customerNumber</td>
        <td>Customer number</td>
      </tr>
      <tr>
        <td>address</td>
        <td>Address</td>
      </tr>
      <tr>
        <td>address2</td>
        <td>Address 2</td>
      </tr>
      <tr>
        <td>zipCode</td>
        <td>Zip code</td>
      </tr>
      <tr>
        <td>city</td>
        <td>City</td>
      </tr>
      <tr>
        <td>country</td>
        <td>Country</td>
      </tr>
      <tr>
        <td>phone</td>
        <td>Phone</td>
      </tr>
      <tr>
        <td>email</td>
        <td>Email</td>
      </tr>
      <tr>
        <td>organizationNumber</td>
        <td>Organization number</td>
      </tr>
      <tr>
        <td>vatNumber</td>
        <td>VAT number</td>
      </tr>
      <tr>
        <td>paymentDays</td>
        <td>Payment days</td>
      </tr>
    </table>
</details>

### Invoices
- <details>
    <summary>Get Invoice by Number</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>invoiceNumber</td>
        <td>Invoice number</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Get Invoice by id</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>id</td>
        <td>ID</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Create Invoice</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>customer</td>
        <td>Customer</td>
      </tr>
      <tr>
        <td>createdByUser</td>
        <td>Created by user</td>
      </tr>
      <tr>
        <td>language</td>
        <td>Language</td>
      </tr>
      <tr>
        <td>name</td>
        <td>Name</td>
      </tr>
      <tr>
        <td>invoiceDate</td>
        <td>Invoice date</td>
      </tr>
      <tr>
        <td>dueDate</td>
        <td>Due date</td>
      </tr>
      <tr>
        <td>project</td>
        <td>Project</td>
      </tr>
      <tr>
        <td>marking</td>
        <td>Marking</td>
      </tr>
      <tr>
        <td>yourOrderNumber</td>
        <td>Your order number</td>
      </tr>
      <tr>
        <td>contactPerson</td>
        <td>Contact person</td>
      </tr>
      <tr>
        <td>ourReference</td>
        <td>Our reference</td>
      </tr>
      <tr>
        <td>workOrder</td>
        <td>Work order</td>
      </tr>
      <tr>
        <td>resultUnit</td>
        <td>Result unit</td>
      </tr>
      <tr>
        <td>deliveryAddress</td>
        <td>Delivery address</td>
      </tr>
      <tr>
        <td>invoiceType</td>
        <td>Invoice type</td>
      </tr>
      <tr>
        <td>priceList</td>
        <td>Price list</td>
      </tr>
      <tr>
        <td>multipleTaxesOnRow</td>
        <td>Multiple taxes on row</td>
      </tr>
      <tr>
        <td>taxPercent</td>
        <td>Tax percent</td>
      </tr>
      <tr>
        <td>currencyCode</td>
        <td>Currency code</td>
      </tr>
      <tr>
        <td>currencyRate</td>
        <td>Currency rate</td>
      </tr>
      <tr>
        <td>notes</td>
        <td>Notes</td>
      </tr>
      <tr>
        <td>invoiceItems</td>
        <td>Invoice items</td>
      </tr>
      <tr>
        <td>useFooterFromSettings</td>
        <td>Use footer from settings</td>
      </tr>
      <tr>
        <td>footerText</td>
        <td>Footer text</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Update Invoice</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>id</td>
        <td>Invoice</td>
      </tr>
      <tr>
        <td>modifiedByUser</td>
        <td>Modified by user</td>
      </tr>
      <tr>
        <td>language</td>
        <td>Language</td>
      </tr>
      <tr>
        <td>name</td>
        <td>Name</td>
      </tr>
      <tr>
        <td>invoiceDate</td>
        <td>Invoice date</td>
      </tr>
      <tr>
        <td>dueDate</td>
        <td>Due date</td>
      </tr>
      <tr>
        <td>project</td>
        <td>Project</td>
      </tr>
      <tr>
        <td>marking</td>
        <td>Marking</td>
      </tr>
      <tr>
        <td>yourOrderNumber</td>
        <td>Your order number</td>
      </tr>
      <tr>
        <td>contactPerson</td>
        <td>Contact person</td>
      </tr>
      <tr>
        <td>ourReference</td>
        <td>Our reference</td>
      </tr>
      <tr>
        <td>workOrder</td>
        <td>Work order</td>
      </tr>
      <tr>
        <td>resultUnit</td>
        <td>Result unit</td>
      </tr>
      <tr>
        <td>deliveryAddress</td>
        <td>Delivery address</td>
      </tr>
      <tr>
        <td>invoiceType</td>
        <td>Invoice type</td>
      </tr>
      <tr>
        <td>priceList</td>
        <td>Price list</td>
      </tr>
      <tr>
        <td>multipleTaxesOnRow</td>
        <td>Multiple taxes on row</td>
      </tr>
      <tr>
        <td>taxPercent</td>
        <td>Tax percent</td>
      </tr>
      <tr>
        <td>currencyCode</td>
        <td>Currency code</td>
      </tr>
      <tr>
        <td>currencyRate</td>
        <td>Currency rate</td>
      </tr>
      <tr>
        <td>notes</td>
        <td>Notes</td>
      </tr>
      <tr>
        <td>invoiceItems</td>
        <td>Invoice items</td>
      </tr>
      <tr>
        <td>useFooterFromSettings</td>
        <td>Use footer from settings</td>
      </tr>
      <tr>
        <td>footerText</td>
        <td>Footer text</td>
      </tr>
    </table>
</details>

### Projects
- <details>
    <summary>Get Project by Name or Number</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>name</td>
        <td>Name</td>
      </tr>
      <tr>
        <td>projectNumber</td>
        <td>Project number</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Get Project by id</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>id</td>
        <td>ID</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Create Project</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>createdByUser</td>
        <td>Created by user</td>
      </tr>
      <tr>
        <td>name</td>
        <td>Project name</td>
      </tr>
      <tr>
        <td>projectNumber</td>
        <td>Project number</td>
      </tr>
      <tr>
        <td>customer</td>
        <td>Customer</td>
      </tr>
      <tr>
        <td>contactPerson</td>
        <td>Contact person</td>
      </tr>
      <tr>
        <td>projectLeader</td>
        <td>Project leader</td>
      </tr>
      <tr>
        <td>department</td>
        <td>Department</td>
      </tr>
      <tr>
        <td>startDate</td>
        <td>Start date</td>
      </tr>
      <tr>
        <td>endDate</td>
        <td>End date</td>
      </tr>
      <tr>
        <td>notes</td>
        <td>Notes</td>
      </tr>
      <tr>
        <td>billingMethod</td>
        <td>Billing method</td>
      </tr>
      <tr>
        <td>pricePerHour</td>
        <td>Price per hour</td>
      </tr>
      <tr>
        <td>fixedPrice</td>
        <td>Fixed price</td>
      </tr>
      <tr>
        <td>timeCategoryPriceList</td>
        <td>Time category price list</td>
      </tr>
      <tr>
        <td>marking</td>
        <td>Marking</td>
      </tr>
      <tr>
        <td>yourOrderNumber</td>
        <td>Your order number</td>
      </tr>
      <tr>
        <td>deliveryAddress</td>
        <td>Delivery address</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Update Project</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>id</td>
        <td>ID</td>
      </tr>
      <tr>
        <td>modifiedByUser</td>
        <td>Modified by user</td>
      </tr>
      <tr>
        <td>name</td>
        <td>Project name</td>
      </tr>
      <tr>
        <td>projectNumber</td>
        <td>Project number</td>
      </tr>
      <tr>
        <td>customer</td>
        <td>Customer</td>
      </tr>
      <tr>
        <td>contactPerson</td>
        <td>Contact person</td>
      </tr>
      <tr>
        <td>projectLeader</td>
        <td>Project leader</td>
      </tr>
      <tr>
        <td>department</td>
        <td>Department</td>
      </tr>
      <tr>
        <td>startDate</td>
        <td>Start date</td>
      </tr>
      <tr>
        <td>endDate</td>
        <td>End date</td>
      </tr>
      <tr>
        <td>notes</td>
        <td>Notes</td>
      </tr>
      <tr>
        <td>billingMethod</td>
        <td>Billing method</td>
      </tr>
      <tr>
        <td>pricePerHour</td>
        <td>Price per hour</td>
      </tr>
      <tr>
        <td>fixedPrice</td>
        <td>Fixed price</td>
      </tr>
      <tr>
        <td>timeCategoryPriceList</td>
        <td>Time category price list</td>
      </tr>
      <tr>
        <td>marking</td>
        <td>Marking</td>
      </tr>
      <tr>
        <td>yourOrderNumber</td>
        <td>Your order number</td>
      </tr>
      <tr>
        <td>deliveryAddress</td>
        <td>Delivery address</td>
      </tr>
    </table>
</details>

### Tasks
- <details>
    <summary>Get Task by Id</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>id</td>
        <td>ID</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Create Task</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>createdByUser</td>
        <td>Created by user</td>
      </tr>
      <tr>
        <td>title</td>
        <td>Title</td>
      </tr>
      <tr>
        <td>workOrder</td>
        <td>Work order</td>
      </tr>
      <tr>
        <td>project</td>
        <td>Project</td>
      </tr>
      <tr>
        <td>user</td>
        <td>User</td>
      </tr>
      <tr>
        <td>startDate</td>
        <td>StartDate</td>
      </tr>
      <tr>
        <td>dueDate</td>
        <td>Due date</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Update Task</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>id</td>
        <td>Task</td>
      </tr>
      <tr>
        <td>modifiedByUser</td>
        <td>Modified by user</td>
      </tr>
      <tr>
        <td>title</td>
        <td>Title</td>
      </tr>
      <tr>
        <td>workOrder</td>
        <td>Work order</td>
      </tr>
      <tr>
        <td>project</td>
        <td>Project</td>
      </tr>
      <tr>
        <td>user</td>
        <td>User</td>
      </tr>
      <tr>
        <td>startDate</td>
        <td>StartDate</td>
      </tr>
      <tr>
        <td>dueDate</td>
        <td>Due date</td>
      </tr>
    </table>
</details>

### Timer
- <details>
    <summary>Get Active Timers</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>user</td>
        <td>User</td>
      </tr>
      <tr>
        <td>project</td>
        <td>Project</td>
      </tr>
    <tr>
        <td>customer</td>
        <td>Customer</td>
      </tr>
    <tr>
        <td>workOrder</td>
        <td>Work order</td>
      </tr>
      <tr>
        <td>timeCategory</td>
        <td>Time category</td>
      </tr>
      <tr>
        <td>task</td>
        <td>Task</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Start timer</summary>
    A timer cannot be started for a user that already has an active timer.
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>user</td>
        <td>User</td>
      </tr>
      <tr>
        <td>customer</td>
        <td>Customer</td>
      </tr>
      <tr>
        <td>project</td>
        <td>Project</td>
      </tr>
      <tr>
        <td>workOrder</td>
        <td>Work order</td>
      </tr>
      <tr>
        <td>timeCategory</td>
        <td>Time category</td>
      </tr>
      <tr>
        <td>task</td>
        <td>Task</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Stop timer</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>id</td>
        <td>ID</td>
      </tr>
      <tr>
        <td>user</td>
        <td>User</td>
      </tr>
    </table>
</details>

### Time logs
- <details>
    <summary>Get Time Log by Id</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>id</td>
        <td>ID</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Create Time Log</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>createdByUser</td>
        <td>Created by user</td>
      </tr>
      <tr>
        <td>user</td>
        <td>User</td>
      </tr>
      <tr>
        <td>timestamp</td>
        <td>Timestamp</td>
      </tr>
      <tr>
        <td>endTimestamp</td>
        <td>End timestamp</td>
      </tr>
      <tr>
        <td>time</td>
        <td>Time</td>
      </tr>
      <tr>
        <td>invoiceableTime</td>
        <td>Invoiceable time</td>
      </tr>
      <tr>
        <td>customer</td>
        <td>Customer</td>
      </tr>
      <tr>
        <td>project</td>
        <td>Project</td>
      </tr>
      <tr>
        <td>timeCategory</td>
        <td>Time category</td>
      </tr>
      <tr>
        <td>Work order</td>
        <td>workOrder</td>
      </tr>
      <tr>
        <td>Price per hour</td>
        <td>pricePerHour</td>
      </tr>
      <tr>
        <td>description</td>
        <td>Description</td>
      </tr>
      <tr>
        <td>internalDescription</td>
        <td>Internal description</td>
      </tr>
      <tr>
        <td>supplementOrder</td>
        <td>Supplement order</td>
      </tr>
      <tr>
        <td>isInvoiceable</td>
        <td>Is invoiceable</td>
      </tr>
      <tr>
        <td>isAbsence</td>
        <td>Is absence</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Update Task</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>id</td>
        <td>Time log</td>
      </tr>
      <tr>
        <td>modifiedByUser</td>
        <td>Created by user</td>
      </tr>
      <tr>
        <td>user</td>
        <td>User</td>
      </tr>
      <tr>
        <td>timestamp</td>
        <td>Timestamp</td>
      </tr>
      <tr>
        <td>endTimestamp</td>
        <td>End timestamp</td>
      </tr>
      <tr>
        <td>time</td>
        <td>Time</td>
      </tr>
      <tr>
        <td>invoiceableTime</td>
        <td>Invoiceable time</td>
      </tr>
      <tr>
        <td>customer</td>
        <td>Customer</td>
      </tr>
      <tr>
        <td>project</td>
        <td>Project</td>
      </tr>
      <tr>
        <td>timeCategory</td>
        <td>Time category</td>
      </tr>
      <tr>
        <td>Work order</td>
        <td>workOrder</td>
      </tr>
      <tr>
        <td>Price per hour</td>
        <td>pricePerHour</td>
      </tr>
      <tr>
        <td>description</td>
        <td>Description</td>
      </tr>
      <tr>
        <td>internalDescription</td>
        <td>Internal description</td>
      </tr>
      <tr>
        <td>supplementOrder</td>
        <td>Supplement order</td>
      </tr>
      <tr>
        <td>isInvoiceable</td>
        <td>Is invoiceable</td>
      </tr>
      <tr>
        <td>isAbsence</td>
        <td>Is absence</td>
      </tr>
    </table>
</details>

### Users
- <details>
    <summary>Get User by Name</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>name</td>
        <td>Name</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Get User by Id</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>id</td>
        <td>ID</td>
      </tr>
    </table>
</details>

### Work orders
- <details>
    <summary>Get Work Order</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>title</td>
        <td>Work order title</td>
      </tr>
      <tr>
        <td>workOrderTitle</td>
        <td>Work order number</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Get Work Order by Id</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>id</td>
        <td>ID</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Create Work Order</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>title</td>
        <td>Title</td>
      </tr>
      <tr>
        <td>customer</td>
        <td>Customer</td>
      </tr>
      <tr>
        <td>createdByUser</td>
        <td>Created by user</td>
      </tr>
      <tr>
        <td>project</td>
        <td>Project</td>
      </tr>
      <tr>
        <td>startDate</td>
        <td>Start date</td>
      </tr>
      <tr>
        <td>endDate</td>
        <td>End date</td>
      </tr>
      <tr>
        <td>estimatedTime</td>
        <td>Estimated time</td>
      </tr>
      <tr>
        <td>description</td>
        <td>Description</td>
      </tr>
      <tr>
        <td>yourOrderNumber</td>
        <td>Your order number</td>
      </tr>
      <tr>
        <td>workAddress</td>
        <td>Work address</td>
      </tr>
    </table>
</details>

- <details>
    <summary>Update Project</summary>
      <table>
      <tr>
        <th>Key</th>
        <th>Label</th>
      </tr>
      <tr>
        <td>id</td>
        <td>Work order</td>
      </tr>
      <tr>
        <td>modifiedByUser</td>
        <td>Modified by user</td>
      </tr>
      <tr>
        <td>title</td>
        <td>Title</td>
      </tr>
      <tr>
        <td>customer</td>
        <td>Customer</td>
      </tr>
      <tr>
        <td>project</td>
        <td>Project</td>
      </tr>
      <tr>
        <td>startDate</td>
        <td>Start date</td>
      </tr>
      <tr>
        <td>endDate</td>
        <td>End date</td>
      </tr>
      <tr>
        <td>estimatedTime</td>
        <td>Estimated time</td>
      </tr>
      <tr>
        <td>description</td>
        <td>Description</td>
      </tr>
      <tr>
        <td>yourOrderNumber</td>
        <td>Your order number</td>
      </tr>
      <tr>
        <td>workAddress</td>
        <td>Work address</td>
      </tr>
    </table>
</details>
