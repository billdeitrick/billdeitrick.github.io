---
description: PowerShell cheat sheet for Office 365.
---

## Get-MessageTrace

* Can search up to the last 7 days of message tracking logs in O365/EOL
* If no parameters given, will return the last 48 hours of message logs across the tenant
* For more details about a particular entry, pipe the trace result to `Get-MessageTraceDetail`

## Start-HistoricalSearch

* Can be used to search the message trace for messages up to 90 days old
* Completes asynchronously and sends a message to a specified email address when finished
* Requires parameters: `StartDate, EndDate, ReportTitle, ReportType (MessageTrace or MessageDetail)`
* The `NotifyAddress` parameter specifies the address to receive an alert once the search is finished
* The `Get-HistoricalSearch` parameter can be used the retrieve the search results after it has finished

## Search-UnifiedAuditLog

* Allows searching the O365 audit log
* Returns pages of results
* The `ResultSize` or `SessionCommand` params can be used to get more entries
* To get paginated results, use the `SessionId` parameter (can be any value of your choosing) and call the cmdlet multiple times with the same session ID
