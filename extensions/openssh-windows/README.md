# WinRM Extension

This extension enables [openssh on windows server](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse). This makes it possible to troubleshoot Windows nodes from the master over ssh, without needing Remote Desktop.

It enables you to remote into your cluster using the master node as a proxy host.  If installed on the windows machines you can:

```
ssh -t -i "$KEY_FILE" -o "ProxyCommand ssh -i $KEY_FILE -W %h:%p $SSH_USER@<master-node-public-ip>" "$SSH_USER@<windows-nod-ip>"
```

# Configuration

|Name               |Required|Acceptable Value     |
|-------------------|--------|---------------------|
|name               |yes     |openssh              |
|publicKey          |yes     |ssh-rsa AAsdAB112C1yc2EA....    |
|version            |yes     |v1                   |
|rootURL            |optional|                     |

# Example

``` javascript
    ...
    "agentPoolProfiles": [
      {
        "name": "windowspool1",
        "extensions": [
          {
            "name": "openssh"
          }
        ]
      }
    ],
    ...
    "extensionProfiles": [
      {
        "name": "openssh",
        "version": "v1",
        "extensionParameters":"ssh-rsa AAsdAB112C1yc2EA..."
      }
    ]
    ...
```

# Troubleshoot

Extension execution output is logged to files found under the following directory on the target virtual machine.

```sh
C:\WindowsAzure\Logs\Plugins\Microsoft.Compute.CustomScriptExtension
```

The specified files are downloaded into the following directory on the target virtual machine.

```sh
C:\Packages\Plugins\Microsoft.Compute.CustomScriptExtension\1.*\Downloads\<n>
```
