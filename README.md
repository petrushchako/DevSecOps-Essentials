# DevSecOps-Essentials
acloudguru course


# Additional Resources
You have been tasked with reviewing Docker Security for your team's host of servers. Clone the Docker Bench security script from Docker's official repo, then run the script against the provided server and save the output to /tmp/bench1.out. Review the script's findings, then solve one of the warnings (such as auditing the files in /var/lib/docker). Rerun the script, this time outputting the results to /tmp/bench2.out. Run a diff of the two files to see that your change has taken affect.

The Docker Bench Security repository can be found at:

https://github.com/docker/docker-bench-security.git


Learning Objectives
1. Clone the Docker Bench repo from GitHub into the current working directory.
  **git clone https://github.com/docker/docker-bench-security.git**
  
2. Change directory to the docker-bench-security directory and run the docker-bench-security script.
  Change your present working directory to docker-bench-security:
  **$ cd docker-bench-security**
  
  Using superuser permissions execute the docker-bench-security.sh shell script and redirect standard output to a file called /tmp/bench1.out
  $ sudo sh docker-bench-security.sh > /tmp/bench1.out
  *The sudo command will prompt your for the cloud_user password

  After running the report, you may look at the contents with the Linux <code>more</code> command:
  $ more /tmp/bench1.out
  
  
3. Update the audit rules on the server to include auditing the Docker Daemon
  $ sudo auditctl -l
  
  Use the auditctl command to add a rule to audit the Docker files in /var/lib/docker:
  $ sudo auditctl -w /var/lib/docker -k "docker lib"
  
   This will setup auditing on the docker daemon. To check you may enter the -l command again.
  $ sudo auditctl -l
4. Run the Docker Bench security utility again and compare the output with the first run.
  Now run the docker bench utility again and direct output to /tmp/bench2.out:
  $ sudo sh docker-bench-security.sh > /tmp/bench2.out

  To view the new report contanets, you may use the <code>more</code> command again.
  $ more /tmp/bench2.out
  
  Now use the Linux diff command to compare the output from the first run in bench1.out to the second run in bench2.out:
  $ diff /tmp/bench1.out /tmp/bench2.out
  
