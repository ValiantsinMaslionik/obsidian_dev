
#devtools

## Chrome extensions

Name|Description|URL
--|--|--
CSP Tester|This extension helps web masters to test web application behaviour with Content Security Policy version 2.0 implemented.|[Homepage](https://chrome.google.com/webstore/detail/csp-tester/ehmipebdmhlmikaopdfoinmcjhhfadlf?hl=en)

## Desktop tools

Name|Description|URL
--|--
MSBuildLog|Binary and Structured Log Viewer|[Homepage](https://msbuildlog.com/#commandline)
dotcover|Test coverage analysis from the command line [[Tools - dotcover]]|[Homepage](https://www.jetbrains.com/help/dotcover/Running_Coverage_Analysis_from_the_Command_LIne.html)

## Web tools
Name|Description
--|--
https://www.websequencediagrams.com|Create sequence diagrams in seconds
https://www.xmlvalidation.com/|Validate XML (including referenced DTDs) 

## PowerShell

### Invoke HTTP method

`Invoke-RestMethod http://localhost:5000/api/products -Method POST -Body (@{ Name="Soccer Boots"; Price=89.99; CategoryId=2; SupplierId=2} | ConvertTo-Json) -ContentType "application/json"`

