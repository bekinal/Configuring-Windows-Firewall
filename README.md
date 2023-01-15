<h1>Configuring Windows Firewall</h1>

<h2>Description</h2>
Project consists of using Windows Server 2016 and Windows 10 to enable, configure, and verify an active firewall. This project assumes that the Windows 10 client is added to a pre-existing domain on the Windows Server 2016.
<br />


<h2>Utilities Used</h2>

- <b>VirtualBox</b> 
- <b>Windows Firewall</b>
- <b>CMD</b>

<h2>Environments Used </h2>

- <b>Windows Server 2016</b>
- <b>Windows 10</b>

<h2>Enabling a Remote Connection:</h2>

Using the Windows toolbar, select Windows Firewall: <br/>
<img src="https://imagizer.imageshack.com/img923/2431/OkOtA0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select "Turn Windows Firewall on or off": <br/>
<img src="https://imagizer.imageshack.com/img924/2317/mz0wVk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Turn on the firewall only for "Domain network settings": <br/>
<img src="https://imagizer.imageshack.com/img922/5339/hEMx5j.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Open the Control Panel and navigate to System and Security: <br/>
<img src="https://imagizer.imageshack.com/img922/8231/WjCc5q.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Click "Allow remote access" to enable a remote connection: <br/>
<img src="https://imagizer.imageshack.com/img923/1529/Z0eAfd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the administrator credentials and select Yes: <br/>
<img src="https://imagizer.imageshack.com/img923/9585/fC5cp1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select Allow remote connections to this computer and deselect Allow connections only from computers running Remote Desktop: <br/>
<img src="https://imagizer.imageshack.com/img923/6223/AFOZOr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Verify that a remote connection is available by connecting from the server to the client using RDP. Click Start at the bottom left and search for Remote Desktop Connection: <br/>
<img src="https://imagizer.imageshack.com/img922/4789/8dxm7z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter a name for the Windows 10 client: <br/>
<img src="https://imagizer.imageshack.com/img922/8384/jWdcbB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the admin credentials and click OK: <br/>
<img src="https://imagizer.imageshack.com/img923/7731/jgtBxx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Disconnect from the session. If the connection was allowed, the client's firewall will accept incoming traffic to port 3389. To disconnect, Click Start/Power/Disconnect: <br/>
<img src="https://imagizer.imageshack.com/img924/7217/H2ly6t.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Run Windows Firewall with Advanced Security as administrator: <br/>
<img src="https://imagizer.imageshack.com/img923/340/FlNMZE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Navigate to the inbound rules tab and note that Remote Desktop on port 3389 is allowed. Check the inbound rules to see if the Remote Desktop service is allowed to run: <br/>
<img src="https://imagizer.imageshack.com/img922/6670/ZoqL7o.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />



<h2>Firewall Rule Policy Configuration:</h2>
Go to the domain controller and open the Active Directory Users and Computers window. Right-click cyber.local and use the drop-down menu to create a new Organizational Unit (OU): <br/>
<img src="https://imagizer.imageshack.com/img924/7224/LAr7tW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Name the OU "RDP Restricted" and click OK: <br/>
<img src="https://imagizer.imageshack.com/img922/8501/AKCseE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Find the Client10 object under Computers and right-click move it to the RDP Restricted OU: <br/>
<img src="https://imagizer.imageshack.com/img923/3088/17olZi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In Group Policy Mangement, right-click the Group Policy OU and create a new GPO: <br/>
<img src="https://imagizer.imageshack.com/img924/9195/eQ5qxk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Name the GPO "RDP Restriction" and click OK: <br/>
<img src="https://imagizer.imageshack.com/img924/7782/fi7SrX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Edit the RDP Restriction GPO again: <br/>
<img src="https://imagizer.imageshack.com/img923/9359/YeDw0I.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Locate Inbound Rules under Windows Firewall with Advanced Security: <br/>
<img src="https://imagizer.imageshack.com/img923/4931/Rzpjku.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Right-click Inbound Rules to create a New Rule: <br/>
<img src="https://imagizer.imageshack.com/img924/3940/cA0UKS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Check Port, click Next: <br/>
<img src="https://imagizer.imageshack.com/img924/3363/FPetQq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Check TCP and Specific Local Ports. Enter 3389 (RDP). Click Next: <br/>
<img src="https://imagizer.imageshack.com/img923/5344/4uoLLg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Check the box to Block the connection. Click next: <br/>
<img src="https://imagizer.imageshack.com/img922/2536/cS74PF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Check all boxes on the next screen. Click next: <br/>
<img src="https://imagizer.imageshack.com/img923/8259/PxpfnA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Name the new rule "Custom RDP Rule" and click Finish: <br/>
<img src="https://imagizer.imageshack.com/img924/1084/9G9GRC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In Group Policy Management, right-click the RDP Restricted OU and select Link a existing GPO: <br/>
<img src="https://imagizer.imageshack.com/img924/6559/XSbjU6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Click the RDP Restriction GPO, click OK
<img src="https://imagizer.imageshack.com/img922/5460/ezR80i.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />



<h2>Rule Verification:</h2>
On the Windows 10 client, run the command "gpupdate /force" to update the policy: <br/>
<img src="https://imagizer.imageshack.com/img924/668/MEoIrm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
With admin permissions, open Windows Firewall with Advanced Security and expand Inbound Rules: <br/>
<img src="https://imagizer.imageshack.com/img924/213/nwo5Nt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Use the Windows Start menu on the server to locate Remote Desktop Connection and click it: <br/>
<img src="https://imagizer.imageshack.com/img922/51/6dwkTK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Type the client's PC name and click Connect: <br/>
<img src="https://imagizer.imageshack.com/img922/6782/GLkEhi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The server should receive the following error: <br/>
<img src="https://imagizer.imageshack.com/img923/2834/Y5F289.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
