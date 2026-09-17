# Secure-Cloud-File-Sharing-for-Team-Collaboration

## Objective
I configured secure file sharing to allow authorized users to access company files for viewing, downloading, or editing as needed. This supports common business use cases such as sharing reports with internal teams, granting contractors limited access to specific project files, and hosting approved marketing materials for public distribution. To implement this, I navigated to the Azure Storage service and configured file shares within the storage account.

## Skills Learned

- Created department-specific file storage (Finance) to keep sensitive information organized and controlled.
- Applied storage limits to prevent unnecessary cloud costs and manage usage responsibly.
- Implemented backup and recovery options to protect files from accidental deletion, ransomware, or system failures.
- Enabled easy employee access by connecting cloud file storage directly to a computer like a shared network drive.
- Demonstrated how companies can restore previous versions of files, reducing downtime and data loss.



## Steps

 File sharing makes files accessible to others so they can view, download, or edit them in a company. This could mean sharing reports with your team, giving contractors access to specific project files, or hosting marketing materials for public downloads. I want to set this up on my Azure Storage. I need to go to the Storage menu and head into File shares. 
On the left-hand side, I need to look for Data Storage and click on File Shares. I now want to create a new File Share. 


<img width="481" height="305" alt="image - 2026-01-12T191143 475" src="images/01.png" />



I want the file share name to be finance, and the access here to be transactionally optimized. The protocol will be SMB for now. And it is going to give me a vault name with a backup policy and just basic policy details. I'm going to hit create and wait for the validation to pass.




I want to upload some files to Finance. 
<img width="582" height="419" alt="image - 2026-01-12T191204 409" src="images/02.png" />


We can create a Directory, which lets us create a subdirectory, which I will do now and call it "FinanceDirectory1."
<img width="532" height="216" alt="image - 2026-01-12T191302 894" src="images/03.png" />


The Quota on the tab to the right is how much data can be stored within the file. Right now, we have 1024000, meaning 102 TB, which is too much. Let's bring it to 5 GB. 

<img width="661" height="155" alt="image - 2026-01-12T191312 469" src="images/04.png" />



A backup vault in Azure is like a secure digital safe where copies of your files are stored. The way I think about it is a backup copy of your cloud file cabinet. If anything happens to your original file, such as an accidental deletion, corruption, ransomware, or a hardware failure, the backup vault ensures that it can restore it to the exact state that it was in previously.


<img width="781" height="234" alt="image - 2026-01-12T191328 710" src="images/05.png" />




Now that it has been deployed, let's load up the share and connect to it. 

<img width="659" height="156" alt="image - 2026-01-12T191336 686" src="images/06.png" />


On the right-hand side it we need to make sure it is selected on Windows and assign it a drive letter. Then, copy the Script and open Windows PowerShell ISE on my computer. 


<img width="581" height="246" alt="image - 2026-01-12T191351 755" src="images/07.png" />



Well, we just copied is a command that will test to make sure that we can reach the file share, which is the storage account.file.co.windows.net, then it's going to create a key with the username\storage\account name and the password, which is one of the keys for the storage account. 

<img width="624" height="174" alt="image - 2026-01-12T191400 544" src="images/08.png" />



Let's run the script. 
<img width="752" height="100" alt="image - 2026-01-12T191415 929" src="images/09.png" />


Now I can see that it is in my Network Locations. 

<img width="449" height="278" alt="image - 2026-01-12T191423 030" src="images/10.png" />


If I double-click the Finance drive and see what's inside, I can view the Directory I made, "FinanceDirectory1," and my PNG Screenshots I added. 
<img width="462" height="179" alt="image - 2026-01-12T191431 654" src="images/11.png" />


If I go to my Credential Manager program on my own computer under Windows Credentials, I can view the most recent credential added to the computer. I see my Storage file directory added. 
<img width="535" height="178" alt="image - 2026-01-12T191441 143" src="images/12.png" />


Something I found out, there is another way of adding this File share using Active Directory, but I have not added that yet. I will set this up in another blog post. 

<img width="560" height="232" alt="image - 2026-01-12T191453 575" src="images/13.png" />


If I ever want to create a snapshot of my File share on Azure, I can create a snapshot, and it will tell me the time, who initiated it, and any comments left from other team members. 
<img width="849" height="138" alt="image - 2026-01-12T191500 108" src="images/14.png" />




I can also revisit the previous snapshots on the file share drive on my computer by right-clicking the drive and clicking on properties, and then clicking on Previous Version. 

<img width="484" height="354" alt="image - 2026-01-12T191508 482" src="images/15.png" />

