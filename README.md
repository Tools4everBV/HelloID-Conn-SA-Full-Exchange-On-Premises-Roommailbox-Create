# HelloID-Conn-SA-Full-Exchange-On-Premises-Roommailbox-Create

| :information_source: Information                                                                                                                                                                                                                                                                                                                                                          |
| :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| This repository contains the connector and configuration code only. The implementer is responsible for acquiring the connection details such as username, password, certificate, etc. You might even need to sign a contract or agreement with the supplier before implementing this connector. Please contact the client's application manager to coordinate the connector requirements. |

## Description

_HelloID-Conn-SA-Full-Exchange-On-Premises-Roommailbox-Create_ is a template designed for use with HelloID Service Automation (SA) Delegated Forms. It can be imported into HelloID and customized according to your requirements.

By using this delegated form, you can create Exchange On-Premises room mailboxes with the following capabilities:

1.  Enter display name for the room mailbox with real-time validation
2.  Specify a unique alias with validation
3.  Select mail domain from available Exchange accepted domains
4.  Enter email prefix and construct full email address
5.  Set room capacity
6.  Create the room mailbox with all specified attributes
7.  Automatic validation ensures uniqueness of display name, alias, and email address

## Getting started

### Requirements

- **Exchange On-Premises Environment**:<br>
  This connector requires an Exchange On-Premises environment with PowerShell remote management enabled. The Exchange server must be accessible via HTTPS and configured to accept remote PowerShell connections.

- **Service Account**:<br>
  A service account with sufficient permissions to create room mailboxes and query Exchange objects is required. The account must have permissions to:
  - Create mailboxes in the specified Organizational Unit
  - Query mailboxes and accepted domains
  - Manage mailbox attributes

- **Active Directory Organizational Unit**:<br>
  A designated Active Directory Organizational Unit (OU) must exist for creating room mailbox objects.

### Connection settings

The following user-defined variables are used by the connector.

| Setting               | Description                                                                 | Mandatory |
| --------------------- | --------------------------------------------------------------------------- | --------- |
| ExchangeConnectionUri | The URI to connect to Exchange On-Premises (e.g., http://server/PowerShell) | Yes       |
| ExchangeAdminUsername | The username to connect to Exchange (format: domain\username)               | Yes       |
| ExchangeAdminPassword | The password to connect to Exchange                                         | Yes       |
| ADRoomMailboxOU       | The Active Directory Organizational Unit for room mailbox objects           | Yes       |

## Remarks

### Enhanced Validation with Multiple Datasources

- **Granular Uniqueness Checks**: The connector uses three separate validation datasources to ensure uniqueness:
  - **Display Name Validation**: Checks if the display name is already in use by any mailbox
  - **Alias Validation**: Ensures the specified alias is unique across all mailboxes
  - **Email Address Validation**: Verifies the email address is not already assigned
- Each validation provides detailed feedback about conflicts, including the conflicting object's properties.

### Domain Selection

- **Dynamic Domain Retrieval**: The connector dynamically retrieves all accepted domains from Exchange On-Premises, allowing users to select from available verified domains.
- **Email Construction**: Email addresses are constructed by combining the user-entered prefix with the selected domain, ensuring proper formatting.

### Enhanced Security

- **Strong Password Generation**: Room mailboxes are created with automatically generated 22-character complex passwords that meet enterprise security requirements.
- **TLS 1.2 Enforcement**: All connections to Exchange use TLS 1.2 for secure communication.

### Improved Error Handling

- **Detailed Error Reporting**: The connector includes comprehensive try-catch-finally blocks with line-level error reporting for easier troubleshooting.
- **Graceful Session Cleanup**: Exchange sessions are properly disconnected in all scenarios, including error conditions, to prevent resource leaks.

## Development resources

### PowerShell Cmdlets

The following Exchange On-Premises PowerShell cmdlets are used by the connector:

| Cmdlet             | Description                                       | Used In     |
| ------------------ | ------------------------------------------------- | ----------- |
| New-Mailbox        | Creates a new room mailbox                        | Task        |
| Set-Mailbox        | Configures mailbox properties                     | Task        |
| Get-Mailbox        | Retrieves mailbox information for validation      | Datasources |
| Get-AcceptedDomain | Retrieves accepted domains for email construction | Datasource  |

### API documentation

- [Exchange Server PowerShell Documentation](https://learn.microsoft.com/en-us/powershell/exchange/exchange-server-powershell)
- [Connect to Exchange Servers using Remote PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-servers-using-remote-powershell)
- [New-Mailbox Cmdlet Reference](https://learn.microsoft.com/en-us/powershell/module/exchange/new-mailbox)
- [Get-Mailbox Cmdlet Reference](https://learn.microsoft.com/en-us/powershell/module/exchange/get-mailbox)
- [Get-AcceptedDomain Cmdlet Reference](https://learn.microsoft.com/en-us/powershell/module/exchange/get-accepteddomain)

## Getting help

> :bulb: **Tip:**  
> _For more information on Delegated Forms, please refer to our [documentation](https://docs.helloid.com/en/service-automation/delegated-forms.html) pages_.

## HelloID docs

The official HelloID documentation can be found at: https://docs.helloid.com/
