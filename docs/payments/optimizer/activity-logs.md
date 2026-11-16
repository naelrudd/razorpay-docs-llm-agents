> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Activity Logs on Optimizer

> See every change made to your Optimizer routing rules, compare rule chains, review canary runs and restore an earlier version in one click.

Available in
🇮🇳 India

> [!NOTE]
>
> **Feature Availability**
>
> Activity logs are available only to Optimizer merchants, on request. To enable Activity logs for your account, reach out to your Optimizer Account Manager or Razorpay Tech Support.

Activity logs give you a record of every change made to your Optimizer routing rules. See what changed, when it changed and who changed it, compare a new rule chain with the one it replaced and restore an earlier version in one click.

Log in to the [Razorpay Dashboard](https://dashboard.razorpay.com/) and click **Optimizer**. On the **Rules** page, click **Activity logs** in the top-right corner.

![Optimizer Rules page with the Activity logs link highlighted in the top-right corner](https://mintcdn.com/razorpay-881012b3/lduAlum148c_aWjV/static/docs-home/assets/optimizer-activity-logs-rules-page.png?fit=max\&auto=format\&n=lduAlum148c_aWjV\&q=85\&s=4a344adcb92fb51926d163039773620b)

## View Activity Logs

The Activity logs page lists every change to your rule chain and every canary run, newest first. Each entry shows:

* **Date and time** of the event.
* **Category**: **Rule chain changes** or **Canary run**.
* **User**: name and email address of the team member who made the change.
* **Description**: the outcome of the event.
* **Restorable**: shown on earlier rule chain versions you can go back to.

Click the arrow at the end of any row to open the entry.

![Activity logs page listing rule chain changes and canary runs with Date and time, Category, User, Description and Restorable columns](https://mintcdn.com/razorpay-881012b3/lduAlum148c_aWjV/static/docs-home/assets/optimizer-activity-logs-list.png?fit=max\&auto=format\&n=lduAlum148c_aWjV\&q=85\&s=8506c88d8d650b3147468997fbf63e31)

The table below lists what each description means:

| Description | Meaning |
| :- | :- |
| **Live** | The rule chain currently running on your account. |
| **Published** | A rule chain that was published earlier and has since been replaced. You can restore it. |
| **Completed** | A canary run that has finished. |

## Filter and Search Activity Logs

Use the filters at the top of the page to find a change quickly. You can:

* Filter by **Event category**: **All categories**, **Rule chain changes** or **Canary run**.
* Filter by user with **Select users**: **All users** or a specific team member.
* Filter by **Duration**: **All time**, **Last 7 days**, **Last 30 days** or **Last 90 days**.
* Use the search box to find entries by event category, user name, email or description.
* Click **×** in the search box to clear it.

![Activity logs filters with Event category, Select users and Duration dropdowns and the search box above the entries](https://mintcdn.com/razorpay-881012b3/lduAlum148c_aWjV/static/docs-home/assets/optimizer-activity-logs-filter-search.png?fit=max\&auto=format\&n=lduAlum148c_aWjV\&q=85\&s=c9d006f1fbee5c7a30ae1304719055a5)

> [!NOTE]
>
> Activity logs are kept for 90 days. Search does not look inside rules. To find when a specific rule changed, filter by **Rule chain changes** and open the entries.

## Review Rule Chain Changes

Click any **Rule chain changes** entry to see the change. The date, time, user name and email appear at the top, followed by a side-by-side view:

* **New rule set**: the rule chain after the change.
* **Old rule set**: the rule chain before the change.

Rules are listed in priority order. Each rule shows its name, its condition and the provider it routes payments to. Rules that changed are highlighted.

![Rule chain changes entry with the New rule set and Old rule set side by side, each rule tagged Added or Reordered](https://mintcdn.com/razorpay-881012b3/lduAlum148c_aWjV/static/docs-home/assets/optimizer-activity-logs-rule-chain-changes.png?fit=max\&auto=format\&n=lduAlum148c_aWjV\&q=85\&s=deb4843ad98b7ca6ae0e93a16a1ed4a7)

Each rule in the new rule set has a tag that shows what changed:

| Tag | Meaning |
| :- | :- |
| **Added** | A new rule was added to the rule chain. |
| **Edited** | A setting of the rule was changed, for example its provider or condition. |
| **Reordered** | The rule moved to a different priority. |
| **No change** | The rule is the same as before. |

## View Rule Details

To see exactly what changed in a rule:

* Click **View details** next to an edited rule, or click **Show more** on the summary below the rule sets.
* Each changed field is listed with the old value struck through and the new value next to it.
* Click **Show less** to collapse the details.

For a newly added rule, **Show more** lists the **Rule name**, **Condition**, **Provider** and **Status**.

![Rule chain changes entry with an edited rule expanded, showing the old provider struck through and the new provider beside it](https://mintcdn.com/razorpay-881012b3/lduAlum148c_aWjV/static/docs-home/assets/optimizer-activity-logs-rule-details.png?fit=max\&auto=format\&n=lduAlum148c_aWjV\&q=85\&s=234678b7634e75526ccd338021c135fc)

## Restore an Earlier Rule Chain

To go back to an earlier version of your rule chain:

1. Open the **Rule chain changes** entry that has the version you want.
2. Review the rule sets and tags to confirm it is the right version.
3. Click **Restore** on the rule set you want to go back to.

**Restore** shows on both rule sets for **Published** entries. For the **Live** entry, the new rule set is already running, so **Restore** shows only on the old rule set.

![Rule chain changes entry with the Restore button on each rule set](https://mintcdn.com/razorpay-881012b3/lduAlum148c_aWjV/static/docs-home/assets/optimizer-activity-logs-restore.png?fit=max\&auto=format\&n=lduAlum148c_aWjV\&q=85\&s=b860ea2db0b6d2edb7662dbe8f765eee)

> [!NOTE]
>
> Restoring a rule chain changes how your payments are routed. Review the rule sets before you restore.

## Review Canary Runs

A canary run tests a new rule chain on a share of your traffic before it goes live for all payments. The rest of your traffic continues to use your existing rule chain. Click any **Canary run** entry to see:

* The traffic share and time window of the test, for example **5% traffic · 3:01 pm – 3:02 pm**.
* **New rule set** and **Existing rule set**, each with its traffic share, **Success rate** and number of **transactions** in the test window.
* **Per-gateway success rate breakdown**: click **Show details** to see the **Transactions**, **New rule set SR**, **Existing rule set SR** and **Change** for each gateway.

![Canary run entry showing 5% traffic from 3:01 pm to 3:02 pm, the New rule set and Existing rule set success rates and transaction counts, and the per-gateway success rate breakdown](https://mintcdn.com/razorpay-881012b3/lduAlum148c_aWjV/static/docs-home/assets/optimizer-activity-logs-canary-run.png?fit=max\&auto=format\&n=lduAlum148c_aWjV\&q=85\&s=18da0bca587935175d3b91eb15540365)

> [!NOTE]
>
> If no payments were processed during the test window, the success rate shows "–" and the transaction count shows 0.

## Related Information

* [Optimizer](https://razorpay.com/docs/payments/optimizer)
