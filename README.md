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

**2b. Observe the ticket as agent John**
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
<img src="04-ticket1-agent-view.png" width="80%" alt="Agent John viewing Ticket #145655 with default properties"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
