####################Linux for DevOps #############################

***********Linux file system Hierarchy **************
root is a super user 

/ = This is top level directory. It is parent directory for all other directories.It is called as root directory like C:\ of windows 
/root = It is home directory for root user(Super user). It provides working environment for root user  like c:\users\administrator
/home = It is home diretory for other users. It provide working environment for other users
/usr = by default softwares are installed in usr direcotry 
/bin = it contains commands used by all users 
/sbin = it contains commands used by super user(root)
/var = it contains variable data like mails, log


*********Basic Commands***************
Date: Current date and time 
Cal : Show this month calendar
uptime : Tell how long the system has been running. How many users are currently logged in , and the system load averages for the past 1,2 and 15 Min
whoami : print the user name associated with the current effective user ID. same  as id -un
users: print the user names of users currently logged in to the current host
id : print user and group information for the spefied users  or for the current user 
who : print information about users who are currently logged in 
ls : list information about the files(the current directory by default)
     -t sort by modification time, newest first
     -l use a long listing format 
     -h human readable
     -r reverse order while sorting
pwd : Present working directory
cat <filename> : standard output
less : view a file page by page 
more : output the content of the file
@Similar to more, less command allows you to view the contents of a file and navigate through file. The main difference between more and less is that less command is faster because it does not load the entire file at once and allows navigation though file using page up/down keys.@
head <filename> :  Output the first 10 lines of file 
tail <filename> :  Output the last 10 lines of file 
page <filename> :  Display file page by page 
touch <filename> : create a 0 byte file 
cat > <filename>  create a file and allow to write
cat >> <filename>  add content end of the file
nano create a file if filename doesnt exist - Editor
vi  create a file if filename doesnt exist  -Editor
rm <filename> :remove a file 
mkdir <dirname>  create a directory
rmdir <dirname remove a empty directory
rm -rf <dirname> remove a directory
tree - list contents of directories in a tree-like format
find :find a file   Find command is used to find the files or directory path, it is exactly like the find option in windows where you can search for a file.
		find / -option filename 
		name : For a searching file with its name
		-user: For files whose owner is a particular user 
		-group : for files belonging to particular group
grep  Grep stands for Global Regular Expression Print. It is used to pick out the required expression from the file and print the output.
	grep <Patron> filename
	- i Ignore case distinctions in both the PATTERN and the input files
	ls -lt | grep ^d   - combine two commands ^d - starting letter is d 
cd :  switch between directories 
diff find content different in 2 files
sed stands for Stream editor, which is used to search a word in the file and replace it with the word required to be in the output.
chmod: Change file permissions 
chown:  change ownership of a file
file:  Show what kind of file it is 

**************File Permission*************
Permisions are applied at 3 levels
-Owner or user Level
-Group Level 
-Others Level
Permissions are applied in 3 ways 
r = Read Only
w = Write/edit/append/deleted
x = Execute/run 
file type
- = Normal file
b = Block file
c = character file 
d = directory 
l = link files 
- rwx rw- r--    ====<File type>

**********User Management
In Linux there are three types of users
1] Super or root user : User is the most powerful user.He is the administrator user
2] System User: Users created by the softwares or applications 
3] Normal User: Normal users are the users created by the root user
All user related information stored in  cat /etc/passwd
cat /etc/group
Whenever a user is created in Linux , below things happen by default 
1] A home directory is created (/home/username)
2] Unique UID and GID are given to user
3] An entry in etc/passwd 
The syntax for creating a user in linux is 
useradd <option> <Username>
options are 
-u user id 
-G Secondory group ID
-g primary group id
-d home directory 
-c comment
-s shell
userdd nihira 
usermod -g sonu nihira  Sonu is group id  -chnaging group id for nihira
password set for user
passwd <username >
 nano /etc/ssh/sshd_config 
After configuration changes : service sshd reload 

************************Networking 
Networking 
hostname  Lists host name of the server
cat /etc/hostname 
init 6   restart system
ping <ip> Availability of Destination server over the network
wget  Download packages/softwares onto Linux System
ifconfig List ip address of the server
telnet connect to remote host /check port availability status
telnet localhost 22  instead of localhost you can give ipaddress of server

**********************Crontab ****************
crontab 
In any operating system, it is possible to create job that you want to reoccur. This process known as job scheduling., is usually done based on user defined jobs. 

crontab -l
crontab -e 

field 	Description 	Allowed Value
MIN 	Minute Field 	0 to 59 
HOUR 	Hour field 		0 to 23
DOM     Day of the Month 1 - 31
MON 	Month field      1-12
DOW     Day of Week 	 0-6

Example 
Execute a job at 8.30 on everyday morning
30 8 * * * Command 
Execute job at 2.00 PM on every Saturday 
00 14 * * 6 Command 
Execute a job at 12.00 AM on 1 july
00 00 01 07 * command 
Execute job at 3.30 PM on every month 25th 
30 15 25 * * 

*************Process Management 
Process management 
when you start a program or running an application 	in Linux, it actually run as a process 
A linux proess running in foreground or in the background, uses memory and CPU resources.
ps -ef list the process which are running in the system
PID (Process ID) and PPID(Parent process ID)
kill /kill -9  kill a process or service 
fg  -- run the program in the foreground 
bg run the service in the back group 
top  list top 20 process which are consuming more CPU  
 
sleep 90 & === process running in background 
jobs command to see jobs status 
bg %1   ---run in background 
Top command 

***********************SSH
SSH 
The SSH protocol(also referred to as secure Shell) is a method for secure remote login from one computer to another. It provides several alternative options for strong authentication. and it protects the communications security and integrity with strong encryption.
port no 22
daemon sshd
config file /etc/ssh/sshd_config
HTTP
port 80
Daemon httpd
config : /etc/httpd/conf/httpd.config

**********
tar -cvf dir1.tar dir1 
tar -xvf dir1.tar 

tar -xvzf dir1.tar.gz
cvf - create verbose file 
xvf   extract verbose file 

gzip 
gunzip 

*********************
curl  access the application as from browser
netstat - tulpn   Which ports are used 

Port Number    Service
21				FTP
22				SSH 
23  			TELNET
25				SMTP
53				DNS
80				HTTP
443				HTTPS

Services 
Service : This Controls the starting and stopping of services 
chkconfig : This controls which services are set to start on boot.
service <name of the service> status  ---to check the status of the service
service <name of the service> start   --- to start the services
service <name of the service> stop    --- to stop a service 
service <name of the service> reload  --- to reload the service
service <name of the service> restart  --- to restart the service 

chkconfig --list  to check the availability of service 
chkconfig <service> on  --to make the service available after restart 
chkconfig <srvice> off  -- to make the service unavailable after restart 

systemctl state httpd : same as service command 

*********************** Softlink and Hardlink ***************
Softlink and Hard link
Softlink : Shortcut file 
Size of link file is equal to no. of characters in the name of original file 
If original file is deleted,link is broken and data is lost 
Command  ln -s <Src file> <dest_file>

Hardlink : 
Size of both file is same 
If original file is deleted then also link will contain data 
Command : ln <src file> <dest_file>

**************Copy files between servers 
SCP (Secure Copy) is a command line utility that allows you to securely copy files and directories between two systems.