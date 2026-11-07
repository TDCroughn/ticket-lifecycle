# ticket-lifecycle

<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Ticket Lifecycle: Intake Through Resolution</h1>
A hands-on walkthrough of the full ticket lifecycle in osTicket, from end-user submission to agent triage, department routing, SLA assignment, escalation, and resolution. It also demonstrates how department-level permissions control which agents can view or edit a ticket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- osTicket (admin panel, agent panel, end-user portal), a web browser, role-based agent accounts (John, Jane)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 11</b> (25H2)

<h2>Ticket Lifecycle Stages</h2>

- Intake
- Assignment and Communication
- Working the Issue
- Resolution

<h2>Lifecycle Stages</h2>

**1a. Submit the ticket as an end user**
1. Open a browser and go to `http://localhost/osTicket`, then click **Open a New Ticket**.
2. Under Contact Information, enter Email Address `karen9999@outlook.com` and Full Name `Karen`. Leave Phone Number blank.
3. Leave Help Topic as **General Inquiry**.
4. In Issue Summary, type `Entire mobile/online banking system is down`.
5. In the description box, enter: "The entire mobile/online banking system seems to be down. When I got back from lunch, I couldn't log in to the online banking platform. None of the tellers at my branch can either."
6. Click **Create Ticket**.

<p>
<img src="Create Ticket.png" width="80%" alt="End user filling out the new ticket form"/>
</p>

**1b. Observe the ticket as agent John**
1. Open a new browser tab and go to `http://localhost/osTicket/scp/login.php`.
2. Log in with the username `john` and his password.
3. Click the **Tickets** tab, then click the ticket **Entire mobile/online banking system is down** (Ticket #145655).
4. Observe the ticket's default properties:
   - **Priority:** Normal
   - **Department:** Support
   - **SLA Plan:** Default SLA (due 11/10/26 5:00 PM)
   - **Assigned To:** Unassigned

*Expected result: the ticket opens with default values, since the end user can't set priority, SLA, or assignment. Nobody owns the ticket yet, and it sits in the generic Support department with a Normal priority.*

<p align="center">
<img src="Ticket Properties.png" width="80%" alt="Agent John viewing Ticket #145655 with default properties"/>
</p>

5. Assign the ticket to Jane: [click the **Assign** (person) icon in the ticket toolbar], select `Jane Doe`, add a note, and confirm.
   *Expected result: the thread logs "John Doe assigned this to Jane Doe" and Assigned To changes from John Doe to Jane Doe.*
6. Transfer the ticket: [click the **gear icon > Transfer**], select the `SysAdmin` department, enter the note "The banking system is down", and click **Transfer**.
   *Expected result: the thread logs "Ticket transferred from Support to SysAdmin" and the Department field changes to SysAdmin.*

**1c. Observe the ticket as Jane**
1. Log out of John's session and log in to the agent panel as `jane`.
2. Open Ticket #145655.
3. Observe the properties: Department **SysAdmin**, Assigned To **Jane Doe**, Priority **Emergency**, SLA Plan **Sev-A**, Due Date **11/7/26 5:03 AM**.

*Expected result: Jane can open the ticket because she has access to the SysAdmin department and the ticket is assigned to her.*

<p align="center">
<img src="Ticket in Jane Portal.png" width="80%" alt="Agent Jane viewing the escalated ticket in the SysAdmin department"/>
</p>

**1d. Work the ticket as Jane**
1. Log in to the agent panel as `jane` and open Ticket #145655.
2. In the **Post Reply** tab, enter: "We accidentally restarted the online banking backend server due to a configuration error. We will check the settings and attempt to restart." Click **Post Reply**.

*Expected result: the reply appears in the Ticket Thread under Jane's name, and the end user receives a copy by email.*

*Note: because the Sev-A SLA allowed 1 hour (due 5:03 AM) and the ticket was still open at 5:30 AM, osTicket automatically logged "Flagged as overdue by the system." This shows how SLA plans track response expectations.*

<p align="center">
<img src="Jane's Reply.png" width="80%" alt="Jane's reply in the thread, with the system overdue flag"/>
</p>

**1e. Resolve and close the ticket as Jane**
1. As `jane`, open Ticket #145655 and click the **Post Reply** tab.
2. Enter: "Server successfully restarted. Online banking is back up. Confirmed with Karen; closing the ticket."
3. Set **Ticket Status** to `Resolved` and click **Post Reply**.

*Expected result: the thread logs "Closed by Jane Doe with status of Resolved" with a timestamp (5:33 AM), and the end user receives the message by email.*

<p align="center">
<img src="Ticket Jane Closing Reply.png" width="80%" alt="Jane's closing reply with status set to Resolved"/>
</p>

4. Click **Closed** in the top menu to confirm the ticket moved there.

*Expected result: Ticket #145655 appears in the Closed queue with Date Closed 11/7/26 5:33 AM and Closed By Jane Doe.*

<p align="center">
<img src="Ticket Closed in the Queue.png" width="80%" alt="Closed queue showing Ticket #145655"/>
</p>
<br />
