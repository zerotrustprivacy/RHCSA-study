# RHCSA-study
Study notes that I am taking for the exam. Using the Sander van Vugt videos and books.
<h3>The beginning:</h3>
<p>I'm starting these notes after I'm already a quarter of the way into the material. I'm finding that most of the information from the Sander van Vugt videos is a review. I'm following along using my own RHEL Server that I installed onto VMware Workstation.. I have also started reading the RHEL book to make sure that I'm really understanding the concepts.</p>
<h3>Creating Partitions</h3>
<p><img src="Screenshot 2023-08-27 213830.png"></p>
<h3> Make File System</h3>
<p><img src= "mkfs.png"></p>
<h3> Unmount a mounted filesystem </h3>
<p><img src ="unmount.png"></p> 
<h3> Create a Swap</h3>
<p><img src ="swap.png"></p>
<h3> Resize Logical Volumes and Volume Groups</h3>
<p><img src="lvmgroups.png"</p>
<h3>Schedule Jobs</h3>
<p>Schedule jobs to run  on a repeating schedule with a user's crontab file. </p>
<p> "man at" shows how to execute schedule jobs. These are one time jobs. For example: "at now +3min" runs a job 3 min from now.</p>
<p>"atq" lists scheduled jobs. "atrm" removes the job.</p>
<p>Recurring Jobs: The crond daemon reads multiple config files. Each user has a personal file that they edit with "crontab -e". The fields in the crontab file are in the following order:
<p><ul>
  <li>Minutes</li>
  <li>Hours</li>
  <li>Day of Month</li>
  <li>Month</li>
  <li>Day of Week</li>
  <li>Command</li>
</ul></p></p>
