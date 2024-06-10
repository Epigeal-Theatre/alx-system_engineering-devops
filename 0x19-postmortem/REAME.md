
Description:
Between 10:00 AM and 11:30 AM EAT on May 6, 2024, our e-commerce website's login service experienced an outage. Users trying to log in received error messages, hindering their ability to access accounts and complete transactions. The issue was traced to a recent configuration change that caused a deadlock in the database, leading to high CPU usage and blocking the login service.

Root Cause:
The root cause of the outage was a misconfigured database index introduced during a recent configuration change. This misconfiguration led to a database deadlock, blocking access for the login service and causing high CPU usage.

Timeline:

10:00 AM EAT: The monitoring system reported a sudden spike in error rates for the login service.
10:02 AM EAT: The engineering team was alerted and began investigating.
10:05 AM EAT: The team found the login service unresponsive and attempted to restart it.
10:10 AM EAT: Restarting the service did not resolve the issue; further investigation began, focusing on a potential database problem.
10:15 AM EAT: High CPU usage was detected on the database server.
10:20 AM EAT: Attempts to optimize database queries and indexes did not significantly reduce CPU usage.
10:30 AM EAT: The incident was escalated to senior engineers and database administrators.
10:35 AM EAT: Database administrators identified a configuration change as the cause of a database deadlock.
10:40 AM EAT: The configuration change was rolled back and the database was restarted.
11:00 AM EAT: The login service was restored, allowing users to log in and complete purchases.
11:30 AM EAT: The incident was declared resolved.
Impact Analysis
Affected Systems/Services:

E-commerce website login service
Customer/User Impact:
Approximately 50% of users were unable to log in or complete purchases for 1 hour and 30 minutes.

Response and Recovery
Detection:
The incident was detected by our automated monitoring system, which reported a spike in error rates for the login service.

Response:
The engineering team was alerted and began an immediate investigation. Upon identifying a database deadlock caused by a recent configuration change, the team rolled back the change and restarted the database.

Recovery:
Rolling back the configuration change and restarting the database resolved the issue. Continuous monitoring confirmed that the login service was functioning normally.

Lessons Learned
What Went Well:

Quick detection by the monitoring system.
Prompt response and escalation by the engineering team.
Effective resolution by rolling back the configuration change.
What Went Wrong:

Insufficient pre-deployment testing of database configuration changes.
Lack of redundancy and failover mechanisms for the login service.
Action Items:

Improve Monitoring - Enhance monitoring of database performance metrics to detect issues earlier - May 20, 2023 - [Responsible Party]
Review Configuration Changes - Implement a thorough review and testing process for database configuration changes before deployment - May 25, 2023 - [Responsible Party]
Training for DBAs - Improve documentation and provide additional training for database administrators on proper configuration management - June 1, 2023 - [Responsible Party]
Increase Redundancy - Add redundancy and failover mechanisms to the login service to reduce the impact of similar incidents - June 10, 2023 - [Responsible Party]
Database Schema Review - Conduct a review of the database schema and query patterns to identify and address potential performance bottlenecks - June 15, 2023 - [Responsible Party]
Conclusion
Summary:
The outage of our e-commerce website's login service was caused by a misconfigured database index leading to a deadlock and high CPU usage. The incident was resolved by rolling back the configuration change and restarting the database. We will implement corrective and preventative measures, including improved monitoring, configuration management, and system redundancy, to prevent similar incidents in the future.
