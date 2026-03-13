# Investigation Submenu Guide

Last updated: 2026-03-14

This guide explains the pages under the `Investigate` menu in simple language.

## What This Area Is For

The `Investigate` area helps you follow where tokens came from, where they went, and whether certain wallets may be connected.

You do not need blockchain knowledge to use it. Each page is focused on one question.

## 1. Outgoing Trace

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

Use this page when you want to see who sent tokens into a wallet.

What it does:
- Starts from one wallet you enter.
- Looks at incoming transfers to that wallet.
- Keeps tracing further backwards to show earlier sender wallets.

Use this page to answer:
- "Who sent tokens into this wallet?"
- "Can I trace the source further back?"

## 3. Address Link

Use this page when you want to check whether two wallets are connected by token transfers.

What it does:
- Compares wallet A and wallet B.
- Checks whether tokens moved directly between them.
- Also checks whether they are connected through other wallets in between.

Use this page to answer:
- "Are these two wallets linked?"
- "Is the connection direct or through several steps?"

## 4. Price

Use this page when you want to review token price changes over time and see who moved tokens on a selected day.

What it does:
- Shows a price chart for the selected date range.
- Lets you click a date on the chart.
- Loads the wallets that sent tokens on that day.

Use this page to answer:
- "What was the token price during this period?"
- "Who was sending tokens on this specific day?"

## 5. Bulk Sources

Use this page when you have many wallets and want to review their incoming sources in one run.

What it does:
- Accepts a list of wallet addresses.
- Looks for source wallets that sent tokens into them.
- Exports the results for review.

Use this page to answer:
- "Can I check many target wallets at once?"
- "Can I prepare this as an export for review?"

## 6. Wallet Outgoing

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

