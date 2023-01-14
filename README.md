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
<img src="https://imagizer.imageshack.com/img924/6117/c1Mx2w.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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



<h2>Grant Permission Levels:</h2>
On the domain controller go back to the Resource folder created in the Local Disk (C:) Directory and right-click it. Select properties, navigate to the security tab, and select advanced: <br/>
<img src="https://imagizer.imageshack.com/img922/4379/z2wlSb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Disable the inheritence and select the second option. This will remove permissions for users. Then, click Add to add a new principle: <br/>
<img src="https://imagizer.imageshack.com/img924/7180/nW2Uwz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Click Select a principal: <br/>
<img src="https://imagizer.imageshack.com/img922/1523/YI3wuv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select Salesperson1: <br/>
<img src="https://imagizer.imageshack.com/img924/4268/NY5Mt5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Allow the user to modify files within the folder: <br/>
<img src="https://imagizer.imageshack.com/img922/6703/RMNxAw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Check the changes made by logging into Salesperson1 on the client machine and trying to access the Resource folder through the shared drive: <br/>
<img src="https://imagizer.imageshack.com/img924/3589/E0fSCM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Switch to the domain controller (admin account) and create a new user within the Users container named Worker1: <br/>
<img src="https://imagizer.imageshack.com/img922/415/JFCRJE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create a new user named Wokrer1: <br/>
<img src="https://imagizer.imageshack.com/img923/5182/UBtRJo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Set the password of your choosing and complete the user definition. For convenience purposes, deselect all of the boxes <br/>
<img src="https://imagizer.imageshack.com/img922/7044/WWTVPB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Allow only worker1 to access the Workers shared folder by changing permissions from the Security tab as completed in prior steps. Disable the inheritence and grant read-only and execute permissions: <br/>
<img src="https://imagizer.imageshack.com/img923/7828/KfmCW0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Add a new permission and click "Select a principal" enter "Worker1" and click Check Names, OK: <br/>
<img src="https://imagizer.imageshack.com/img923/6444/Ng4MHB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Check the boxes to grant specific permissions: <br/>
<img src="https://imagizer.imageshack.com/img924/990/vDqjUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Verify that the worker1 user has permission to read & execute the Workers folder: <br/>
<img src="https://imagizer.imageshack.com/img922/7128/Bgi8Vp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Switch to the client machine. log into Salesperson1 and try to access the Workers folder. You should receive a Cannot Access message. However, you should have access to the Sales folder: <br/>
<img src="https://imagizer.imageshack.com/img922/9904/tG4aZt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Navigate to the directory. right-click it, go to Properties/Security: <br/>
<img src="https://imagizer.imageshack.com/img923/7274/99Lfpq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
On the client, switch users to Worker1. You can do this easily by running "Logoff": <br/>
<img src="https://imagizer.imageshack.com/img922/9646/Sl7Lzi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Log in as cyber\Worker1: <br/>
<img src="https://imagizer.imageshack.com/img922/4800/7alDPZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Open the Run window and type \\\server1 to access the Resource folder. You should be unable to see Sales but have access to Workers: <br/>
<img src="https://imagizer.imageshack.com/img924/4307/urd5mP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Error message from trying to access Sales folder: <br/>
<img src="https://imagizer.imageshack.com/img924/8978/bDkwna.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Try to create a new folder in the Workers folder. You should receive an error due to insufficient permissions: <br/>
<img src="https://imagizer.imageshack.com/img922/2914/QZCJxj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Switch back to the domain controller and assign Worker1 full control permissions for the Workers folder.: <br/>
<img src="https://imagizer.imageshack.com/img923/8055/EBgwIA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Click apply and OK: <br/>
<img src="https://imagizer.imageshack.com/img922/32/IEMJWo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Test the change under Wokrer1. Notice that you can now add a folder within the Workers directory: <br/>
<img src="https://imagizer.imageshack.com/img922/4366/yFTxUe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


<h2>Creating a Hidden Folder:</h2>
On the DC machine, go to your C: directory and create a folder called "You_can't_see_me": <br/>
<img src="https://imagizer.imageshack.com/img923/3271/jyBxE4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Go to the folder's settings. Open the Sharing tab, click Advanced Sharing and select Share this Folder. For Share name, change the name to "You_can't_see_me$": <br/>
<img src="https://imagizer.imageshack.com/img922/3330/FnSlZD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Click Permissions and ensure Allow is checked for Full Control. Click Apply and OK: <br/>
<img src="https://imagizer.imageshack.com/img922/5564/zpsg2a.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the You_can't_see_me folder and create a new text file: <br/>
<img src="https://imagizer.imageshack.com/img922/232/m4Me4q.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Log in as the Wokrer1 user and verify that the folder appears from the shared folder. Open the Run window and type \\server1. Make sure the hidden folder does not appear in the share path: <br/>
<img src="https://imagizer.imageshack.com/img922/543/v0hAbw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Try using the Run window to access \\server1\You_can't_see_me$ again to verify the folder's content exists: <br/>
<img src="https://imagizer.imageshack.com/img923/5211/e2LXHu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Note that the content is seen: <br/>
<img src="https://imagizer.imageshack.com/img924/589/1xrihQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
