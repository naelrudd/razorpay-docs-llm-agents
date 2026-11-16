> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Refund Analytics

> Track refund rate, amount, count and success rate in the Analytics suite. See how refunds trend over time and open any refund for full detail without leaving the page.

The Refunds page in the Analytics suite shows how refunds are trending across your business. The page goes from insights at the top to specifics at the bottom: track your key refund metrics, see how they move over time and open any individual refund for detail without leaving the page.

Go to **Analytics** → **Refunds** on the [Razorpay Dashboard](https://dashboard.razorpay.com/) to get started.

![Refunds page in the Analytics suite showing key metrics and the refund trends chart](https://mintcdn.com/razorpay-881012b3/N9mwRqc34zgz5l6O/static/docs-home/assets/refund-analytics-1.jpg?fit=max\&auto=format\&n=N9mwRqc34zgz5l6O\&q=85\&s=6c6c0fc837884ad39b65aceb6272298b)

## **Apply Filters**

The filters at the top of the page apply to every widget below them: key metrics, trends and the refunds breakdown. Use the filters to:

* Select the **Period**: Today, Yesterday, Last 7 Days (default), Last 14 Days, Last 30 Days or a **Custom** range of up to **90 days**.
* Click **Compare with** to compare the selected period against the **Previous period** or a **Custom** date range.
* Filter by **Payment methods**: Card, Netbanking, UPI or All. Expand Card or UPI to pick a sub-type.
* Filter by refund **Status**: Pending, Processed, Failed or All.
* Filter by refund **Speed**: Normal, Instant or All.
* Filter by **Gateway**: a specific gateway or All. Available only for [Optimizer](https://razorpay.com/docs/payments/optimizer) merchants who route payments to gateways other than Razorpay.
* Click **×** on any filter to clear it.

![Period filter open with Today, Yesterday, Last 7 Days, Last 14 Days, Last 30 Days and Custom range options](https://mintcdn.com/razorpay-881012b3/N9mwRqc34zgz5l6O/static/docs-home/assets/refund-analytics-2.jpg?fit=max\&auto=format\&n=N9mwRqc34zgz5l6O\&q=85\&s=d770230c4adfb85f538656f16426849f)

![Compare with filter open showing Previous period and Custom date range options](https://mintcdn.com/razorpay-881012b3/N9mwRqc34zgz5l6O/static/docs-home/assets/refund-analytics-3.jpg?fit=max\&auto=format\&n=N9mwRqc34zgz5l6O\&q=85\&s=345b69a98618c3b5a3d8779091f83367)

![Payment methods filter open with All, Card, Netbanking and UPI options](https://mintcdn.com/razorpay-881012b3/N9mwRqc34zgz5l6O/static/docs-home/assets/refund-analytics-4.jpg?fit=max\&auto=format\&n=N9mwRqc34zgz5l6O\&q=85\&s=bf1834fded15ced7b503f33cf1c079fe)

![Status filter open with All, Pending, Processed and Failed options](https://mintcdn.com/razorpay-881012b3/N9mwRqc34zgz5l6O/static/docs-home/assets/refund-analytics-5.jpg?fit=max\&auto=format\&n=N9mwRqc34zgz5l6O\&q=85\&s=f7e761e05c3179261bd52dc706dc1f9e)

![Speed filter open with All, Normal and Instant options](https://mintcdn.com/razorpay-881012b3/N9mwRqc34zgz5l6O/static/docs-home/assets/refund-analytics-6.jpg?fit=max\&auto=format\&n=N9mwRqc34zgz5l6O\&q=85\&s=fbac9000cf32b07e7a7d1b9378b51f26)

> [!NOTE]
>
> The **Gateway** filter only shows for [Optimizer](https://razorpay.com/docs/payments/optimizer) merchants routing payments to gateways other than Razorpay.

## **Track Key Metrics**

Key metrics give you a quick read on refund health for the selected filters.

* The page shows 4 metrics by default: **Refund rate**, **Refund amount**, **Refund count** and **Refund success rate**.
* Hover over a metric name to see its definition.
* Click **Edit** to choose which metrics to display. Pin up to **4** metrics. Selecting a new metric replaces the one selected last.
* Each metric value reflects your filter selection.

![Configure metrics dialog with Refund rate, Refund amount, Refund count and Refund success rate selected](https://mintcdn.com/razorpay-881012b3/N9mwRqc34zgz5l6O/static/docs-home/assets/refund-analytics-7.jpg?fit=max\&auto=format\&n=N9mwRqc34zgz5l6O\&q=85\&s=524a67ebb95ac4d313c1662bdd9df4e2)

The table below lists the refund metrics and their definitions:

| Metric | Definition |
| :- | :- |
| **Refund rate (%)** | Share of payments authorised in the selected period that have been refunded. |
| **Refund amount (₹)** | Total value of refunds processed in the selected period. |
| **Refund count (#)** | Refund transactions processed in the selected period. |
| **Refund success rate (%)** | Share of refunds created that have been processed in the selected period. |
| **Refund TAT** | Turn Around Time (TAT) for a refund to reach a final status, shown as the median and the 90th percentile. Available only for [Optimizer](https://razorpay.com/docs/payments/optimizer) merchants, for refunds processed through gateways other than Razorpay. |

> [!NOTE]
>
> Refund rate and Refund success rate depend on the payments authorised and the refunds initiated in the selected period. Refunds for recent payments may still be in progress, so these rates can read lower for the last few days and settle over time.

## **Track Refund Trends**

The Refund trends chart plots how refunds move over time for the selected filters.

* Switch between the **Amount**, **Count** and **Success rate** tabs.
* Hover over any point on the chart to see its exact value.
* Use **Compare with** in the filters to compare against another date range.
* Switch the view to **Trend line**, **Bar chart** or **Data table**.
* Click **Download** to export the chart data as a CSV file.
* Track **TAT** for refunds processed through external gateways and split the trends by gateway. Available only for [Optimizer](https://razorpay.com/docs/payments/optimizer) merchants.

![Refund trends chart on the Amount tab with a tooltip showing the refund amount for a selected day](https://mintcdn.com/razorpay-881012b3/N9mwRqc34zgz5l6O/static/docs-home/assets/refund-analytics-8.jpg?fit=max\&auto=format\&n=N9mwRqc34zgz5l6O\&q=85\&s=347f2e140006ec51e995828b657cf459)

## **View the Refunds Breakdown**

The Refunds breakdown lists every refund that matches your filters, newest first.

* Use the quick filters to view **All**, **Processed**, **Pending** or **Failed** refunds.
* Each row shows the **Refund ID**, **Created on** date and time, **Status** and **Amount**.
* Click **Details** on any row to open the refund in the right pane.
* Click **Download** to export the list.

![Refunds breakdown table listing refunds with Refund ID, Created on, Status and Amount columns](https://mintcdn.com/razorpay-881012b3/N9mwRqc34zgz5l6O/static/docs-home/assets/refund-analytics-9.jpg?fit=max\&auto=format\&n=N9mwRqc34zgz5l6O\&q=85\&s=778568134228f2cb0306b82c2d81e4f3)

## **Open Refund Details**

Click **Details** on any row to open the right pane with the full context of a refund. The right pane shows:

* **Transaction details:** Payment ID, Bank Retrieval Reference Number (RRN), Order ID, Invoice ID, Payment method, Customer details and Processed by.
* **Refund details:** Refund ID, Acquirer Reference Number (ARN) or RRN, Refund speed, Issued on, Gateway code and Gateway message.
* **Refund timeline:** Each step from payment creation to authorisation, refund creation and refund processing, with timestamps.

![Refund details pane showing Transaction details and Refund details for a selected refund](https://mintcdn.com/razorpay-881012b3/N9mwRqc34zgz5l6O/static/docs-home/assets/refund-analytics-10.jpg?fit=max\&auto=format\&n=N9mwRqc34zgz5l6O\&q=85\&s=40a9e2fc768e1005cf611ec52096f9ab)

![Refund details pane scrolled to Refund details and the refund timeline with timestamped steps](https://mintcdn.com/razorpay-881012b3/N9mwRqc34zgz5l6O/static/docs-home/assets/refund-analytics-11.jpg?fit=max\&auto=format\&n=N9mwRqc34zgz5l6O\&q=85\&s=f0cac314aad48d6db4b9132ba07a686b)

From the right pane:

* Click **View details** to open the refund on the **Refunds** page under **Transactions**.
* Click the copy icon next to any ID to copy its value.

> [!NOTE]
>
> Share the ARN or RRN with your customer when they ask about a refund. Their bank can use it to trace the credit. Normal refunds take 3 to 5 working days to process. The money reaches your customer in 5 to 7 working days. Instant refunds reach your customer within minutes. Know more about [Instant Refunds](https://razorpay.com/docs/payments/refunds/instant.md).

## **Related Information**

* [Refunds](https://razorpay.com/docs/payments/refunds)
* [Instant Refunds](https://razorpay.com/docs/payments/refunds/instant.md)
* [Optimizer](https://razorpay.com/docs/payments/optimizer)
