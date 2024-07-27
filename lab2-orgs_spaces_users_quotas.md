# Orgs, Spaces, Users & Roles

## Goal
Use the CLI to create a space, add a user and assign the user a role.

Approximate time: 15 minutes

## Exercise:
### Create a space in your organization

In the CLI, make sure you are targeting your installation.

Using the CLI and cf help, perform the following:

* Find the name of your organization.
* List the spaces in your organization.
* Create a new space called "labtest". Notice that the organization manager now has SpaceManager and SpaceDeveloper roles for the new space.

* List the space-users in the labtest space.

In your browser, verify that your labtest space is visible in your Apps Manager.

### Add a user to the labtest space
*This exercise is optional* If you have access to another email account, you can add another user to your organization. In Apps Manager, click on your organization, then the Members tab, then Invite New Members.

After inviting a new member, check the email and create an account.

Once the new member has accepted, use cf org-users to verify that you have the member in your organization.

Using the CLI, add the member to your labtest space as a SpaceDeveloper.

Log out of the organization manager and log in as the new user. That new user can now use the labtest space as a developer.

Log out as the developer user and back in as the organization manager.

### Create a space quota
Create a space quota to allow only one instance of an application, that is 512mb in size.
use cf space-quotas to view the quotas you created
use set-space-quota to assign it to your space
unset the quota.  (Note if you want to check out the quota in action don't unset or delete it, but you will need to do this after it fails in subsequent labs)
Delete the space quota.
