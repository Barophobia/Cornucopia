+++
title = "Join AD Domain"
chapter = true
+++

### Verify you can resolve the Active Directory Domain Controller FQDN - (Optional)

Open a command prompt and ping your ADDC FQDN, replace DC.network.com in the command below.
```
ping DC.network.com
```
If the ping is successful you can begin the joining process.

### Joining the domain
- Open Server Manager and click Local Server on the left hand menu panel
- Click the workgroup property in the properties panel, this will open a System Properties window.
- Click on the Change button in the System Properties window
- In the Member of section, select Domain and enter the domain name into the field.
- A windows security box will pop up asking for account details, enter an Administrator account for your domain.
- If the joining process was successful a small new window will open that welcomes you to the domain, click Ok.
- A window will appear saying you need to restart your device, click Ok and then Close the System Properties window.
- Now Restart your device when prompted.

Once the device has restarted you will be able to login as a domain user.