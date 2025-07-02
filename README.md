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

Next, scroll down the EC2 settings and make sure the Amazon Machine Image(AMI) is with the free tier eligible option.

An AMI is a template or blueprint used to create EC2 instances and contains the operating system along with the applications needed to launch the instance.

Free tier eligible AMIs are those that qualify for the AWS Free Tier, so you won't get charged for using it. Finally launch your instance!
<p>
<img src="https://i.imgur.com/59YjCJG.png" height="80%" width="80%" alt="AD-adminCreation"/>
</p>

The next step is the lauch another instance with the same settings, but instead of the value being "production," name it "development" this time.

At this point, you should have 2 instances running!
<p>
<img src="https://i.imgur.com/GmMXePm.png" height="80%" width="80%" alt="AD-adminCreation"/>
</p>

The next thing to do is create an IAM policy. Search for "IAM" in the AWS console.

IAM stands for Identity and Access Management. You'll use AWS IAM to manage the access level that other users and services have to your resources.

An IAM policy is a rule for who can do what with your AWS resources. It's all about giving permissions to IAM users, groups, or roles, saying what they can or can't do on certain resources, and when those rules kick in.
<p>
<img src="https://i.imgur.com/cUiWSig.png" height="80%" width="80%" alt="AD-adminCreation"/>
</p>

On the left-hand navigation panel, select Policies. Then switch the policy editor to JSON, and copy the code for this policy.

Hit next and name the policy. I named mine "DevEnvironmentPolicy".
<p>
<img src="https://i.imgur.com/XtV5OIa.png" height="80%" width="80%" alt="AD-adminCreation"/>
</p>
