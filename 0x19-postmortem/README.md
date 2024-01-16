0x19. Postmortem

Foundations > System engineering & DevOps > On call
Project author

Sylvain Kalache

Description

Practice in writing a proper report on the failure of a piece of software or web architecture.
Mandatory Tasks
⬜ 0. My first postmortem

Using one of the web stack debugging project issue or an outage you have personally face, write a postmortem. Most of you will never have faced an outage, so just get creative and invent your own :)

Requirements:

    Issue Summary (that is often what executives will read) must contain:
        duration of the outage with start and end times (including timezone)
        what was the impact (what service was down/slow? What were user experiencing? How many % of the users were affected?)
        what was the root cause
    Timeline (format bullet point, format: time - keep it short, 1 or 2 sentences) must contain:
        when was the issue detected
        how was the issue detected (monitoring alert, an engineer noticed something, a customer complained…)
        actions taken (what parts of the system were investigated, what were the assumption on the root cause of the issue)
        misleading investigation/debugging paths that were taken
        which team/individuals was the incident escalated to
        how the incident was resolved
    Root cause and resolution must contain:
        explain in detail what was causing the issue
        explain in detail how the issue was fixed
    Corrective and preventative measures must contain:
        what are the things that can be improved/fixed (broadly speaking)
        a list of tasks to address the issue (be very specific, like a TODO, example: patch Nginx server, add monitoring on server memory…)
    Be brief and straight to the point, between 400 to 600 words

While postmortem format can vary, stick to this one so that you can get properly reviewed by your peers.
Advanced Tasks
⬜ 1. Make people want to read your postmortem

We are constantly stormed by a quantity of information, it’s tough to get people to read you.

Make your post-mortem attractive by adding humour, a pretty diagram or anything that would catch your audience attention.




SOLUTIONS


Issue Summary:

    Start time: 01/02/24 10:00 AM (CAT); End time: 01/02/24 2:30 PM (CAT).
    The WordPress page was returning a 500 status code error, so the page was down for 100% of the users.
    Root cause: conflict between a recently updated WordPress plugin and other plugins within our WordPress environment.

Timeline:

    01/02/24 10:00 AM (CAT) — Users’ complaints initiated the investigation.
    01/02/24 10:05 AM (CAT)— The technical team was alerted to the issue.
    01/02/24 10:10 AM (CAT) — An engineer began diagnostics, suspecting server misconfiguration or plugin conflicts as root causes.
    01/02/24 12:05 PM (CAT) — Server and WordPress logs were scrutinized.
    01/02/24 12:15 PM(CAT) — A plugin conflict was identified as a primary cause due to error messages in the logs.
    01/02/24 12:20 PM (CAT)—Temporary fix by disabling the problematic plugin.
    01/02/24 1:00 PM (CAT) — Resource consumption was reduced, and the user experience improved.
    01/02/24 2:10 PM (CAT) — Full website functionality was restored through a rollback to a previous stable plugin version.
    01/02/24 2:15 PM (CAT) — Ongoing monitoring ensures stability.

Root Cause:

Plugin Conflict: The Apache 500 Error was primarily due to a conflict between a recently updated WordPress plugin and other plugins on our website. This conflict led to excessive resource consumption, causing server resource exhaustion and errors.

Resolution:

Disabling Problematic Plugins and Rollback: To resolve the issue:

    Identifying the Problematic Plugin: A thorough examination of logs revealed the conflicting plugin, “W3 Total Cache.”
    Temporary Disabling: The problematic plugin was temporarily disabled to reduce resource consumption and restore partial functionality.
    Rollback to Previous Version: A stable version of “W3 Total Cache” was restored to fully resolve the issue and regain full website functionality.

Corrective Measures:

What Needs Improvement or Fixing?

    Plugin Compatibility Testing: Enhance the process to avoid deploying conflicting plugins.
    Resource Scaling: Improve infrastructure scalability.
    Error Handling and Monitoring: Enhance error handling and monitoring procedures.

Tasks to Address the Issue:

    Establish a staging environment for testing all updates.
    Create a comprehensive checklist for compatibility testing.
    Implement automated testing tools.
    Regularly review server resources and scalability.
    Implement automatic scaling.
    Monitor resource utilization and adjust resources.
    Configure Apache for detailed error logging.
    Implement robust monitoring tools and alerts.

Preventative Measures:

What Needs Improvement or Fixing?

    Resource Management: Ongoing monitoring and optimization.
    Incident Response Planning: Develop and document a comprehensive plan.

Tasks to Address the Issue:

    Conduct monthly audits of plugins and themes.
    Implement a regular performance review process.
    Develop and document an incident response plan.
    Organize training sessions for the technical team.


