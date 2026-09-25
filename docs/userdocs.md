# User Guide

## What this plugin does

The **User Lifecycle Management** plugin (`tool_userautodelete`) automates the management of Moodle user accounts over
their whole lifetime. Instead of manually hunting down inactive or obsolete accounts, administrators define
**workflows** that run automatically in the background.

A workflow is made up of one or more **steps**. Each step contains:

- **Filters** that decide which users the step applies to, for example:
  last access to the site, authentication method, cohort membership, course enrolment, role assignment,
  suspension state, account confirmation, profile field values, a specific date, or a time delay.
- **Actions** that are performed when a user enters the step, for example:
  send an email, suspend or unsuspend the account, change cohort membership, change a profile field,
  anonymize the account, or delete the user.

Users move through a workflow step by step. A typical workflow could:

1. Send a warning email to users who have not logged in for a long time.
2. Wait for a grace period.
3. If the user still has not returned, send a final notice, then delete and anonymize the account in a
   GDPR-compliant way.

To help you use the plugin safely, it also provides:

- A **dry-run mode** that shows which users a workflow would pick up, without doing anything to them.
- An **action log** that records every email sent, account suspended, and account deleted by the plugin.


## Requirements

- Administrator access to your Moodle site
- Moodle 4.5 (LTS) or later
- PHP 8.1 or later


## Using the plugin

### 1. Install the plugin

1. Download the latest release from the
   [Moodle plugin directory](https://marketplace.moodle.com/plugins/tool_userautodelete).
2. Go to **Site administration > Plugins > Install plugins** and upload the ZIP file.
3. Follow the on-screen steps to finish the installation.

On Moodle 5.1 or later, if you install the plugin manually, put the code in `public/admin/tool/userautodelete`.
On earlier versions, use `admin/tool/userautodelete`.

### 2. Open the workflow management page

1. Go to **Site administration > Plugins**.
2. Scroll down to **Admin tools** and click **User Lifecycle Management > Workflows**.

### 3. Create a workflow

1. Click **Create new default workflow**. This creates a ready-made example workflow that you can adapt.
2. Click **Turn editing on** to change the workflow.
3. Click a filter or action to change its settings, such as how long a user must be inactive or the text of an email.
   You can also add or remove steps, filters, and actions.
4. Click **Turn editing off** when you are finished.

### 4. Check the workflow with a dry run

> **Always do a dry run before you enable a workflow.**

1. On the workflow page, click **Turn editing on**, then click **Dry-run**.
2. Check that the list shows only the users you expect. You can click a username to open that user's profile.

The dry run lists only the users who match the filters of the **first** step of the workflow.

### 5. Enable the workflow

> **Warning:** Enabling a workflow starts real, automated processing. Accounts may be suspended, anonymized, or deleted
> right away, and deletions cannot be undone.

1. Click **Turn editing off**, then click **Enable workflow**.
2. Go back to the workflow overview and check that the workflow status is **Active**.

A scheduled task processes the workflow in the background, so the first run may not happen straight away.

### 6. Review what happened

1. Go to **Site administration > Plugins > Admin tools > User Lifecycle Management > Action log**.
2. You can use the filter bar to narrow down the list of actions.


## More information

- Full documentation: <https://moodleuserlifecycle.gandrass.de/>
- Bug reports and feature requests: <https://github.com/ngandrass/moodle-tool_userautodelete/issues>
