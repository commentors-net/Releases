# Investigation Submenu Guide

<img width="1524" height="283" alt="image" src="https://github.com/user-attachments/assets/803e0eef-c722-4720-a597-416fcca6fa54" />

This guide explains the pages under the `Investigate` menu in simple language.

## What This Area Is For

The `Investigate` area helps you follow where tokens came from, where they went, and whether certain wallets may be connected.

You do not need blockchain knowledge to use it. Each page is focused on one question.

## 1. Outgoing Trace
<img width="1514" height="1217" alt="image" src="https://github.com/user-attachments/assets/6dfefc4f-13aa-4165-875a-8fa016c2bd04" />

Use this page when you want to see where tokens moved after leaving frozen wallets.

What it does:
- Starts from one or more frozen wallets.
- Follows outgoing transfers step by step.
- Shows the results as a tree so you can see the path more clearly.

Use this page to answer:
- "Where did funds go after they left this frozen wallet?"
- "Which wallets received funds next?"

Important note:
- If you leave the wallet list empty, the system uses the default XT.com exchange frozen address.

## 2. Incoming Trace
<img width="1529" height="801" alt="image" src="https://github.com/user-attachments/assets/87a8d88d-9eec-47f2-8722-85a78dab04ac" />

Use this page when you want to see who sent tokens into a wallet.

What it does:
- Starts from one wallet you enter.
- Looks at incoming transfers to that wallet.
- Keeps tracing further backwards to show earlier sender wallets.

Use this page to answer:
- "Who sent tokens into this wallet?"
- "Can I trace the source further back?"

## 3. Address Link
<img width="1532" height="507" alt="image" src="https://github.com/user-attachments/assets/999b4ede-dcce-4e87-81b9-db557dca3bd0" />

Use this page when you want to check whether two wallets are connected by token transfers.

What it does:
- Compares wallet A and wallet B.
- Checks whether tokens moved directly between them.
- Also checks whether they are connected through other wallets in between.

Use this page to answer:
- "Are these two wallets linked?"
- "Is the connection direct or through several steps?"

## 4. Price
<img width="1522" height="1059" alt="image" src="https://github.com/user-attachments/assets/532a853f-92c9-4698-a9a0-a926c9ae8c7c" />

Use this page when you want to review token price changes over time and see who moved tokens on a selected day.

What it does:
- Shows a price chart for the selected date range.
- Lets you click a date on the chart.
- Loads the wallets that sent tokens on that day.

Use this page to answer:
- "What was the token price during this period?"
- "Who was sending tokens on this specific day?"

## 5. Bulk Sources
<img width="1520" height="640" alt="image" src="https://github.com/user-attachments/assets/f29da32b-4900-4242-8829-52d42beb9ea4" />

Use this page when you have many wallets and want to review their incoming sources in one run.

What it does:
- Accepts a list of wallet addresses.
- Looks for source wallets that sent tokens into them.
- Exports the results for review.

Use this page to answer:
- "Can I check many target wallets at once?"
- "Can I prepare this as an export for review?"

## 6. Wallet Outgoing
<img width="1539" height="597" alt="image" src="https://github.com/user-attachments/assets/916fc0e4-1c15-4075-87cb-ad57308e94eb" />

Use this page when you want the outgoing history of one wallet over a long period.

What it does:
- Starts from one wallet.
- Lists the outgoing token transfers from that wallet.
- Lets you export the result.

Use this page to answer:
- "What has this wallet sent out over time?"
- "Can I review the full outgoing history?"

## Quick Summary

- `Outgoing Trace`: Follow money leaving frozen wallets.
- `Incoming Trace`: Follow money coming into a wallet.
- `Address Link`: Check whether two wallets are connected.
- `Price`: Review price history and sending activity by day.
- `Bulk Sources`: Review many wallets in one export.
- `Wallet Outgoing`: Review one wallet's outgoing history.

## Best Practice

Start with the page that matches your question:
- If your question is about where funds went, use `Outgoing Trace`.
- If your question is about where funds came from, use `Incoming Trace`.
- If your question is about whether two wallets are related, use `Address Link`.

