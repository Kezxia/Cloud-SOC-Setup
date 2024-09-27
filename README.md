# Cloud-SOC-Setup

![Architecture Diagram](https://imgur.com/qyxi43s.png)

> [!NOTE]
> In this lab, we will create our tenant, which serves as our main Azure account. When you create your account, the subscription will be created automatically. Next, we will create a resource group to hold our resources. Within that resource group, we will set up a virtual network, where our virtual machines will be connected—one will be a Windows VM and the other a Linux VM. Finally, we will configure the firewalls for both NSGs (Network Security Groups) to allow all internet traffic.




<details>
<summary>Part 1: Create your Azure Account.</summary>

To create your Azure account, you must have a Microsoft account. Select this [link](https://signup.live.com/signup?lcid=1033&wa=wsignin1.0&rpsnv=13&ct=1678357788&rver=7.0.6738.0&wp=MBI_SSL&wreply=https%3a%2f%2faccount.microsoft.com%2fauth%2fcomplete-signin%3fru%3dhttps%253A%252F%252Faccount.microsoft.com%252F%253Frefd%253Daccount.microsoft.com%2526refp%253Dsignedout-index&lc=1033&id=292666&lw=1&fl=easi2&mkt=en-US&lic=1&uaid=c9cb9b166cd245398fae9f662958ebda) to create a Microsoft account. If you already have an account, you can use an email address, Skype ID, or phone number to sign into your Windows PC, Xbox, or Microsoft services like Microsoft 365. You can check [here](https://go.microsoft.com/fwlink/?linkid=2215203) to confirm whether you have a Microsoft account. 

If you are new to Azure, you can sign up for a [free account](https://azure.microsoft.com/en-us/free/) on the Azure website to start exploring at no cost to you. When you are ready, you can choose to upgrade your free account. You can upgrade your [Azure free account](https://learn.microsoft.com/en-us/azure/cost-management-billing/troubleshoot-subscription/troubleshoot-azure-sign-up) to [pay-as-you-go](https://azure.microsoft.com/offers/ms-azr-0003p/) rates in the Azure portal. 

![Azure image](https://imgur.com/aJX27or.png)

Once you create your Azure account, you will enter into the [Azure portal](https://portal.azure.com/#home), where you can manage your Azure subscription using a graphical user interface (GUI). 

![Azure image](https://imgur.com/6XjX7Xt.png)

</details>


<details>
<summary>Part 2: Create a Windows 10 Pro Virtual Machine.</summary>

1. Search for Virtual Machines.<br>
![Azure image](https://imgur.com/U2rNpEs.png)<br>
2. Create a new virtual machine.<br>
![Azure image](https://imgur.com/djWC7NN.png)
3. Create a new resource group and name it. In this example, it will be RG-Cyber-Lab.<br>
![Azure image](https://imgur.com/dK2oSQ9.png)
4. Name the VM name. In this example, it will be windows-vm.<br>
![Azure image](https://imgur.com/Qd25r7p.png)
5. Change region to: EAST US 2.<br>
![Azure image](https://imgur.com/m0iiwgx.png)
6. Change operating system to Windows 10.<br>
![Azure image](https://imgur.com/DL3V9Ru.png)
7. Select see all sizes, and pick E-Series v5 with at least 2 vCPUs.<br>
![Azure image](https://imgur.com/X9qwvDF.png)
![Azure image](https://imgur.com/P4hNB24.png)
8. Create a username and password and select: Next:Disks> & click Next: Networking>.<br>
![Azure image](https://imgur.com/4P7nREE.png)
9. Create a new Virtual Network and name it. In this example, it will be Lab-VNet. Then select Review + Create.<br>
![Azure image](https://imgur.com/dzkKY0q.png)
10. Once Validation has passed, select Create for the Windows VM.<br>
![Azure image](https://imgur.com/yx6rttY.png)

</details>


<details>
<summary>Part 3: Create a Linux Virtual Machine.</summary>

1. Search for Virtual Machines.<br>
![Azure image](https://imgur.com/U2rNpEs.png)<br>
2. Create a new virtual machine.<br>
![Azure image](https://imgur.com/djWC7NN.png)
3. Put it in the existing resource group, RG-Cyber-Lab.<br>
![Azure image](https://imgur.com/dK2oSQ9.png)
4. Name the VM name. In this example, it will be linux-vm.<br>
![Azure image](https://imgur.com/CPvvOuO.png)
5. Change region to: EAST US 2.<br>
![Azure image](https://imgur.com/m0iiwgx.png)
6. Change operating system to Linux.<br>
![Azure image](https://imgur.com/kHvvvuI.png)
7. Select see all sizes, and select the same size as the windows vm.<br>
![Azure image](https://imgur.com/X9qwvDF.png)
![Azure image](https://imgur.com/P4hNB24.png)
8. Create a username and password and select: Next:Disks> & click Next: Networking>.<br>
![Azure image](https://imgur.com/LsIKvKj.png)
9. Select the same Virtual Network called Lab-VNet. Then select Review + Create.<br>
![Azure image](https://imgur.com/nK7gtIX.png)
10. Once Validation has passed, select Create for the Windows VM.<br>
![Azure image](https://imgur.com/SJlHWYV.png)
11. Search for VM to see the VMs that were created.
![Azure image](https://imgur.com/sNKeMTC.png)

</details>


<details>
<summary>Part 4: Configure Network Security Group (Layer 4 Firewall) to allow all traffic inbound for both VMs.</summary>

1. Search for Network Security Groups.<br>
![Azure image](https://imgur.com/Izr6U5Z.png)<br>
2. Edit the windows “firewall” and open it to the public by deleting the RDP traffic.<br>
![Azure image](https://imgur.com/Irqwwio.png)
3. Create our own rule that allows any inbound traffic.<br>
![Azure image](https://imgur.com/DEYagKA.png)
  - Click Inbound security rules, then click Add
  - Change Destination port ranges from 8080 to * = any
  - Priority needs to be lower than the priorities already there (65000) so 100 is fine
  - Change name to DANGER_AllowAnyCustomAnyinbound (it can be any name really)
  - Select Add
![Azure image](https://imgur.com/zsvqd8v.png)
4. Select Overview to see the security rule has been added.<br>
![Azure image](https://imgur.com/7LrEOet.png)
5. Go to the Linux NSG and edit the linux “firewall” and open to the public by deleting SSH traffic.<br>
![Azure image](https://imgur.com/Rg1CJ6O.png)
6. Create our own rule that allows any inbound traffic.<br>
![Azure image](https://imgur.com/KcZV3nk.png)
![Azure image](https://imgur.com/rs6jxCT.png)
7. Click Overview to see the security rule has been added.<br>
![Azure image](https://imgur.com/yBuXdos.png)

</details>


![Architecture Diagram](https://imgur.com/qyxi43s.png)

> [!NOTE]
> In this lab, we’ll use Remote Desktop (RDP) to access the Windows VM and ping it from our terminal. We’ll disable the Windows internal firewall, and instead of creating a standalone SQL Server database, we’ll install it inside the Windows VM. Then, we’ll ping and SSH into the Linux VM.

<details>
<summary>Part 1: Remote into the Windows VM and turn off the Windows Firewall.</summary>

1. Download Microsoft Remote Desktop to connect to the Windows VM.<br>
![Azure image](https://imgur.com/bDWjeJJ.png)<br>
2. Copy the Windows IP address and open the Microsoft Remote Desktop app.<br>
- Add PC and paste the IP address
- Give the pc a name and click add
- Double-click on windows-vm and enter the Username and Password
- Once logged in, click Accept
![Azure image](https://imgur.com/vtg0yIs.png)
![Azure image](https://imgur.com/iLSFGxn.png)
![Azure image](https://imgur.com/cD3bHiQ.png)
![Azure image](https://imgur.com/dNnsOYU.png)
![Azure image](https://imgur.com/4SvK37D.png)
![Azure image](https://imgur.com/oOlKfCi.png)
3. Open up the terminal to ping the Windows pc. Request is timing out because the Windows Firewall is still on.<br>
![Azure image](https://imgur.com/fCKbPCp.png)
4. Go to the search bar and type: wf.msc.<br>
![Azure image](https://imgur.com/RLcg4AG.png)
5. Click on “Windows Defender Firewall Properties”.<br>
![Azure image](https://imgur.com/WDLxjc0.png)
6. Turn the Firewall state “Off” for the Domain Profile, Private Profile & Public Profile.<br>
![Azure image](https://imgur.com/jowxYGx.png)
![Azure image](https://imgur.com/d3bmNDl.png)
![Azure image](https://imgur.com/DCYDKuG.png)
7. Once the Firewalls are turned off, the pings goes through.<br>
![Azure image](https://imgur.com/tOUZeQg.png)

</details>


<details>
<summary>Part 2: Install SQL Server Evaluation.</summary>

1. Open Edge and paste this [link](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2019) and select download the EXE.<br>
![Azure image](https://imgur.com/zPgooiX.png)<br>
2. Register for Free Trial with fake information as this is for learning purposes.<br>
![Azure image](https://imgur.com/u4YOals.png)
3. Download the EXE, open the file, click Download Media, and click ISO pkg. Download it on the desktop.<br>
![Azure image](https://imgur.com/qGss5Io.png)
![Azure image](https://imgur.com/j06MPeo.png)
![Azure image](https://imgur.com/kp3OPkT.png)
4. Click on Open Folder, right click and click mount, then select the setup file to download SQL.<br>
![Azure image](https://imgur.com/7XmBLG1.png)
![Azure image](https://imgur.com/sK31VmV.png)
![Azure image](https://imgur.com/6kjiebn.png)
5. Click Installation, then click “New SQL Server stand-alone…” then click next several times.<br>
![Azure image](https://imgur.com/u12uu54.png)
6. Under Feature Selection, select Database Engine Services, then click next.<br>
![Azure image](https://imgur.com/PlTcYDe.png)
7. Under Database Engine Configuration, select Mixed Mode (SQL Server authentication & Windows authentication).<br>
- enter the same password we created earlier
- add Current User, then click next, and then install
![Azure image](https://imgur.com/qPyteur.png)
8. Install is complete.<br>
![Azure image](https://imgur.com/7Jx0ZPE.png)

</details>


<details>
<summary>Part 3: Install SSMS (SQL Server Management Studio).</summary>

1. Open Edge and paste this [link](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms) and select download the SSMS.<br>
![Azure image](https://imgur.com/pbvLWwz.png)<br>
2. Open file, click install, restart & login again via Microsoft Remote Desktop.<br>
![Azure image](https://imgur.com/C7RhTru.png)
![Azure image](https://imgur.com/m65Bj2f.png)
![Azure image](https://imgur.com/dNnsOYU.png)

</details>

<details>
<summary>Part 4: Enable logging for SQL Server to be ported into Windows Event Viewer.</summary>

1. Search for Registry Editor and paste the Registry Path below in the search bar:
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\EventLog\Security
- Right click Security key & click on permissions
![Azure image](https://imgur.com/H3CxFUD.png)<br>
2. Click Add and type “NETWORK SERVICE”, then click “Check Names”, then click Ok.<br>
![Azure image](https://imgur.com/TfBqtxP.png)
3. Select NETWORK SERVICE, select Full Control, click apply & ok.<br>
![Azure image](https://imgur.com/3Zly0HS.png)
4. Copy the Windows Command Prompt.<br>
![Azure image](https://imgur.com/WROPxyb.png)
5. Search cmd for the command line, right click & run as admin, then paste the command below:
  - auditpol /set /subcategory:"application generated" /success:enable /failure:enable
  - it should successfully execute
![Azure image](https://imgur.com/XXhbVxx.png)
![Azure image](https://imgur.com/teTUT6Z.png)


</details>


<details>
<summary>Part 5: Test SQL logging to make sure it’s working properly.</summary>

1. Search for and open up the SSMS app.<br>
![Azure image](https://imgur.com/5g8os0d.png)
2. Change Authentication from Windows to SQL Server.<br>
![Azure image](https://imgur.com/zLWzPX7.png)
3. Enter the username and password we created earlier.<br>
![Azure image](https://imgur.com/n3wWfRR.png)
4. Once logged in, click on windows-vm SQL Server, then right-click on properties.<br>
![Azure image](https://imgur.com/soUFCS2.png)
5. Click on Security, under login auditing, click “both failed and successful login”, then ok.<br>
![Azure image](https://imgur.com/Ip8XT6Q.png)
6. Restart the server by clicking on windows-vm SQL Server, then click restart, and yes.<br>
![Azure image](https://imgur.com/BI3mSFI.png)
![Azure image](https://imgur.com/XyKZEhh.png)
7. Disconnect, re-connect, then enter wrong password to create a failed login log.<br>
![Azure image](https://imgur.com/J8h2KjW.png)
![Azure image](https://imgur.com/QsyTs0j.png)
![Azure image](https://imgur.com/LA4rKMk.png)
8. Search for and open the Event Viewer app to view failed login under Application.<br>
![Azure image](https://imgur.com/ILDqANs.png)
![Azure image](https://imgur.com/D4sAk43.png)

</details>


<details>
<summary>Part 6: Test ping and logging into Linux VM via SSH.</summary>

1. Copy the linux IP address.<br>
![Azure image](https://imgur.com/IX2tOT0.png)
2. Open up the terminal to ping the Linux VM. Enter: ping 20.75.86.94, then ctrl C to stop the pings.<br>
![Azure image](https://imgur.com/YSdbvWT.png)
3. SSH into the Linux VM. Enter: ssh labuser@20.75.86.94<br>
![Azure image](https://imgur.com/tIJ6y39.png)
4. To trust the certificate the VM is offering up to establish the SSH connection, you need to type yes, then the password we created earlier (nothing will show up, but it’s there).<br>
![Azure image](https://imgur.com/SL29xyQ.png)
4. This is how you know you have successfully logged into the Linux VM.<br>
![Azure image](https://imgur.com/KFygg9N.png)

</details>
