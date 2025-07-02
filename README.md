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

Nice! Now that the policy is set up, we need to create an AWS alias account.

Once you onboard new users into your AWS account, these new users get access through a unique login URL for your account.

An Account Alias is a friendly name for your AWS account that you can use instead of your account ID (which is usually a bunch of digits) to sign in to the AWS Management Console.
<p>
<img src="https://i.imgur.com/zXwjnAc.png" height="80%" width="80%" alt="AD-adminCreation"/>
</p>

Moving along, we will create User Groups.

An IAM user group is a collection/folder of IAM users. It allows you to manage permissions for all the users in your group at the same time by attaching policies to the group rather than individual users.

Again, on the left-hand panel, choose User groups and select create group. Also, make sure the policy we created earlier is attached to this user group.
<p>
<img src="https://i.imgur.com/FwRQ03d.png" height="80%" width="80%" alt="AD-adminCreation"/>
</p>

This time, we will add users to the user group.

IAM users are the people who will get access to your resources/AWS account, whereas user groups are the collections/folders of users for easier user management.

We're adding users to iam-dev-group to grant them the permissions associated with that group.

Make sure to check the box "Provide user access to the AWS Management Console".
<p>
<img src="https://i.imgur.com/uGxuEAX.png" height="80%" width="80%" alt="AD-adminCreation"/>
</p>

Success! Now you should be seeing sign in details for the new user. Important to take note of this.
<p>
<img src="https://i.imgur.com/oWJNY6g.png" height="80%" width="80%" alt="AD-adminCreation"/>
</p>

Time to test the new user's access. 

In an incognito window sign in the the AWS console using the username and password of the created user. There should be some access denied panels showing on the account. 

Go to the EC2 console, and make sure the region is the same area where you created the production and development instances. Next select the production instance -> instance state -> select stop instance.

You should get a red banner telling you that this action cannot be done since this user doesn't have authorization. 
<p>
<img src="https://i.imgur.com/YswrFAg.png" height="80%" width="80%" alt="AD-adminCreation"/>
</p>

Now try to stop the development instance. You see the user was able to do this action.

You have now completed using AWS IAM to control and test user permissions.
<p>
<img src="https://i.imgur.com/ym1ohfc.png" height="80%" width="80%" alt="AD-adminCreation"/>
</p>

