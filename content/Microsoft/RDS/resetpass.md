+++
title = "Reset a Domain Password in RDWeb"
date = 2021-12-09T16:51:31Z
weight = 5
chapter = true
pre = "<b> - </b>"
+++

### Resetting a domain password in RDWeb 

- Open IIS on the Server with RDWeb service installed

- Go to [Server Name] –> Sites –> Default Web Site –> RDWeb –> Pages and open the section Application Settings.

- find *PasswordChangeEnabled* and change the value to true

- Restart the IIS Service

Now you can navigate to the RDWeb page and change your password
https://[SERVERNAME]/RDWeb/Pages/en-US/password.aspx