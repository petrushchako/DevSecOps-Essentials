# DevSecOps-Essentials
acloudguru course


# Additional Resources
You have been tasked with reviewing Docker Security for your team's host of servers. Clone the Docker Bench security script from Docker's official repo, then run the script against the provided server and save the output to /tmp/bench1.out. Review the script's findings, then solve one of the warnings (such as auditing the files in /var/lib/docker). Rerun the script, this time outputting the results to /tmp/bench2.out. Run a diff of the two files to see that your change has taken affect.

The Docker Bench Security repository can be found at:
<code>https://github.com/docker/docker-bench-security.git</code>


# Learning Objectives
## 1. Clone the Docker Bench repo from GitHub into the current working directory.
**<code>git clone https://github.com/docker/docker-bench-security.git</code>**
  
## 2. Change directory to the docker-bench-security directory and run the docker-bench-security script.
Change your present working directory to docker-bench-security:
**<code>cd docker-bench-security</code>**
  
Using superuser permissions execute the docker-bench-security.sh shell script and redirect standard output to a file called /tmp/bench1.out
**<code>sudo sh docker-bench-security.sh > /tmp/bench1.out</code>**
  *The sudo command will prompt your for the cloud_user password

After running the report, you may look at the contents with the Linux <code>more</code> command:
**<code>more /tmp/bench1.out</code>**
  
  
## 3. Update the audit rules on the server to include auditing the Docker Daemon
**<code>sudo auditctl -l</code>**
  
Use the auditctl command to add a rule to audit the Docker files in /var/lib/docker:
**<code>sudo auditctl -w /var/lib/docker -k "docker lib"</code>**
  
This will setup auditing on the docker daemon. To check you may enter the -l command again.
**<code>sudo auditctl -l</code>**

## 4. Run the Docker Bench security utility again and compare the output with the first run.
Now run the docker bench utility again and direct output to /tmp/bench2.out:
**<code>sudo sh docker-bench-security.sh > /tmp/bench2.out</code>**

To view the new report contanets, you may use the <code>more</code> command again.
**<code>more /tmp/bench2.out</code>**
  
Now use the Linux diff command to compare the output from the first run in bench1.out to the second run in bench2.out:
**<code>diff /tmp/bench1.out /tmp/bench2.out</code>**
