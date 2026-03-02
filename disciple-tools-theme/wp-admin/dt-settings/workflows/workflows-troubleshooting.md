# Workflow Troubleshooting

Use this section when a workflow does not run as expected or when you see unexpected behavior.

## The Workflow Does Not Run

If the workflow never runs when you expect it to, check the following.

### Is the Workflow Enabled?

Only workflows with **enabled** checked will run. Open the workflow and look at Step 4, or check the Enabled column in the list. Enable the workflow and save if needed.

### Does the Trigger Match?

- **Record Created**: The workflow runs only when a **new** record is created. It does not run when you edit an existing record.
- **Field Updated**: The workflow runs when fields are updated. For it to run, at least one of the fields used in your **conditions** must be part of the update (or, for a new record, must have a value). If you change only other fields, the workflow will not run.

### Are the Conditions True?

Every condition must be true. Check:

- **Value matching**: The condition value must match exactly what is stored (for example the right status key, the right user or record id, or the right date). Typos or wrong options will prevent the workflow from running.
- **Field type**: Conditions depend on the field type. If the field is empty when you expect a value (or the other way around), the condition may fail. Use "Has any value and not empty" or "Has no value or is empty" when you only care about whether something is set.

### Would the Action Change Anything?

Disciple.Tools may skip running a workflow’s actions if they would not change anything (for example the field already has that value, or the comment was already added). So the trigger and conditions might be correct, but the system does nothing because there is no update to apply. Change the record so that the action would do something new, then try again.

### Correct Post Type?

Workflows are defined per record type. Ensure you created or enabled the workflow for the same record type you are testing (for example Contacts vs Groups).

## Activity Log Shows "D.T Workflow"

When a change is made by a workflow, the activity log can show the workflow name or, if the workflow is no longer available, **D.T Workflow**. This is normal. It means the change was done by the system based on a workflow, not by a user. If you deleted or renamed the workflow, the log may still show "D.T Workflow" for past entries.

## Error or Warning When Saving

- **Name required**: In Step 4 you must enter a name for the workflow. If you see an error when saving, check that the name field is not empty.
- **At least one condition or action**: The design panel usually requires at least one condition row if you go through Step 2, and at least one action row from Step 3. If you left a step without adding any row, go back and add the required condition or action, then save again.
- **Value required**: For most conditions and actions you must enter or select a value. If the value field is empty when it is required (for example for "Equals" or "Updated To"), add the value and try saving again.

## Default Workflow Not Listed

Default workflows are provided by Disciple.Tools for specific record types (such as Contacts and Groups). If you do not see a default workflow you expect:

- Confirm you have selected the correct post type (the one that workflow is for).
- Some default workflows may depend on fields or features that exist only in the core theme. Custom or modified setups might not show all default workflows.

## Workflow Runs Too Often or at the Wrong Time

- **Field Updated**: If the workflow runs on "Field Updated," it runs on any update that includes one of the condition fields. To narrow this down, add more conditions (for example not only "Status has a value" but "Status equals Active") so it runs only when the change matches what you want.
- **Record Created**: If you use "Record Created," the workflow runs once per new record. If you are seeing multiple runs, check whether multiple records are being created (for example by an import or another process).
