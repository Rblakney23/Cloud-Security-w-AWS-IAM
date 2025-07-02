<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>


This lab is focused on mastering AWS Identity and Access Management (IAM) — the core service for authentication and authorization in AWS.

What You'll Build
- Establish IAM users, groups, and roles to manage identity and access.

- Define least-privilege policies with JSON permission documents.

- Set up MFA enforcement for enhanced account security.

- Enable CloudTrail logging to audit IAM activity and policy usage.

Project Goals

Authenticate and Authorize
- Learn how IAM controls who (users) can do what (permissions) in your AWS environment.

Implement Least-Privilege Access
- Practice writing fine-grained policies that only allow necessary actions — a key cybersecurity best practice.

Audit & Monitor
- Use CloudTrail to track changes to identities and permissions, setting the foundation for secure, compliant access.

<h2>In-Depth Deployment and Configuration Steps</h2>
First, we will start by creating an EC2 instance:


Amazon EC2 is a service that lets you rent and use virtual computers in the cloud. They're like your personal computers, but they exist on the internet instead of being physically in front of you. You can create, customize, and use these computers for all different reasons, from running applications to hosting websites.
<p>
<img src="https://i.imgur.com/eQknYh1.png" height="80%" width="80%" alt="AD-adminCreation"/>
</p>

Now choose "add additional tags", you should see it near the name field.

Tags are like labels you can attach to AWS resources for organization. In this case, we're creating a tag called "Env" with a value of "production" or "development" to label the instances used in production vs development environments. This tagging helps us with identifying all resources with the same tag at once (they are useful filters when you're searching for something), cost allocation, and applying policies based on environment types.
<p>
<img src="https://i.imgur.com/XDfrDQJ.png" height="80%" width="80%" alt="AD-adminCreation"/>
</p>
