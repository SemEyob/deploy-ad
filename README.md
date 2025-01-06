<p align="center">
  <img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1 align="center"> Deploying Active Directory in the Cloud (Azure)</h1>
In this home lab, I will install Active Directory Domain Services (AD DS), set up a forest (`mydomain.com`), and use Active Directory Users and Computers (ADUC) to create and assign users to connect to `VM-Client-1` via Remote Desktop (RDP). I will also use PowerShell ISE to run a script that creates randomized users for RDP access.

<h2>Environments and Technologies Used</h2>
<ul>
  <li>Microsoft Azure (Virtual Machines/Compute)</li>
  <li>Remote Desktop</li>
  <li>Active Directory Domain Services</li>
  <li>PowerShell</li>
</ul>

<h2>Operating Systems Used</h2>
<ul>
  <li>Windows Server 2022</li>
  <li>Windows 10 (21H2)</li>
</ul>
<h2>Key Takeaways and Skills Gained</h2>
<ul>
  <li><strong>Active Directory Deployment:</strong> Successfully installed and promoted Active Directory Domain Services (AD DS), creating a functional forest and domain (<code>mydomain.com</code>).</li>
  <li><strong>Organizational Unit Management:</strong> Designed and implemented OUs for organizing users and devices, demonstrating understanding of administrative best practices.</li>
  <li><strong>Administrative User Setup:</strong> Created and managed Domain Admin accounts with secure roles, ensuring proper delegation of administrative privileges.</li>
  <li><strong>Client Integration:</strong> Joined and managed Windows 10 clients within the domain using ADUC, showcasing knowledge of domain-based administration.</li>
  <li><strong>Remote Desktop Configuration:</strong> Enabled and tested Remote Desktop access for non-administrative domain users, enhancing accessibility and usability.</li>
  <li><strong>Automation with PowerShell:</strong> Automated the creation of bulk users for RDP access, improving efficiency and scalability in user management.</li>
</ul>
<h2>High-Level Deployment and Configuration Steps</h2>

<h3>Part 1: Install Active Directory</h3>
<ol>
  <li>Login to DC-1 and install Active Directory Domain Services</li>
  <p align="center">
   
    
![Screenshot (108)](https://github.com/user-attachments/assets/30d53139-6fba-40d8-a5e3-e5bc71067aab)

  </p>

  <li>Promote the server as a Domain Controller and set up a new forest as <code>mydomain.com</code></li>
  <p align="center">
    
  ![Screenshot (109)](https://github.com/user-attachments/assets/3b516947-bdeb-4d35-813d-9f3c8a88e4a6)

![Screenshot (110)](https://github.com/user-attachments/assets/69df48c5-cebd-41b1-a42c-0377dcfd38c6)

  </p>

  <li>Restart the server and log in as <code>mydomain.com\labuser</code></li>
  <li>Create Organizational Units (OUs) named <code>_EMPLOYEES</code> and <code>_ADMINS</code></li>
  <p align="center">
   
![Screenshot (111)](https://github.com/user-attachments/assets/57832e81-05ff-4c72-bc9b-d5614b0b032e)

  </p>

  <li>Create a Domain Admin user (<code>jane_admin</code>) in ADUC and add her to the <code>Domain Admins</code> security group</li>
  <li>Log in as <code>mydomain.com\jane_admin</code> for administrative tasks</li>
</ol>

<h3>Join Client-1 to the Domain</h3>
<ol>
  <li>Login to Client-1 as the local admin and join it to the domain <code>mydomain.com</code></li>
  <li>Verify Client-1 appears in ADUC</li>
  <p align="center">
    
  ![Screenshot (113)](https://github.com/user-attachments/assets/b677bfcf-76dc-4ee2-af97-58b4e2552ed0)

  ![Screenshot (114)](https://github.com/user-attachments/assets/cf936b2c-c745-4834-a424-bd035255d720)

  </p>

  <li>Create a new OU named <code>_CLIENTS</code> and move Client-1 into it</li>
</ol>

<h3>Part 2: Setup Remote Desktop for Non-Administrative Users</h3>
<ol>
  <li>Log in to Client-1 as <code>mydomain.com\jane_admin</code></li>
  <li>Enable Remote Desktop and allow access for domain users</li>
  <p align="center">
    
  ![Screenshot (115)](https://github.com/user-attachments/assets/5b284051-8024-4622-9558-d45565fcda94)

  </p>

  <li>Test by logging in as a non-administrative user</li>
</ol>

<h3>Create Randomized Users with PowerShell</h3>
<ol>
  <li>Login to DC-1 as <code>jane_admin</code></li>
  <li>Open PowerShell ISE as an administrator</li>
  <li>Run a PowerShell script to create multiple users for RDP access</li>
  <p align="center">
   
  ![Screenshot (116)](https://github.com/user-attachments/assets/116c2694-776c-4b9d-84f3-f50c79e433b5)

  </p>
</ol>


</ul>

