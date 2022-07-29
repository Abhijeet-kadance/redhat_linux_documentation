# YUM REPOLIST 

> Step 1> Connect ISO IN Virtual Machine

> Step 2> Mount the repos from  ISO file to Local Repository Directory

> Step 3> Configure YUM

## Configuration of YUM

    cd to your ISO file PATH

    cd /run/media/root/RHEL-8-6-0-BaseOS-x86_64

    Traverse to cd /etc/yum.repos.d (YUM configuration direcotry)

    create a new repo file for our own repolist

    For That do :

    gedit test.repo

    ##################

    Inside the File we have to add 2 folder path that are necesarry for us to fetch all the required libraries from our ISO file 

    /run/media/root/RHEL-8-6-0-BaseOS-x86_64/AppStream

    /run/media/root/RHEL-8-6-0-BaseOS-x86_64/BaseOS

    >> Now in linux for yum to know that to use these paths as base URL 

    add baseurl to the path as 

    baseurl=/run/media/root/RHEL-8-6-0-BaseOS-x86_64/AppStream

    baseurl=/run/media/root/RHEL-8-6-0-BaseOS-x86_64/BaseOS

    >> TO TELL THE YUM these files are present Locally on your system Not Online you have to tell the YUM find the file locally as 

    baseurl=file:///run/media/root/RHEL-8-6-0-BaseOS-x86_64/AppStream

    baseurl=file:///run/media/root/RHEL-8-6-0-BaseOS-x86_64/BaseOS


    >> To defrentiate Repos we have to give name as:

    [dvd1]
    baseurl=file:///run/media/root/RHEL-8-6-0-BaseOS-x86_64/AppStream
    gpgcheck=0

    [dvd2]
    baseurl=file:///run/media/root/RHEL-8-6-0-BaseOS-x86_64/BaseOS
    gpgcheck=0


***TRY YUM INSTALL NOW***

yum install httpd

and It will install from our conf repo file {dvd1} {dvd2}


-----

***To check your Repository***

yum repolist 

this will display OUR 2 repos

Also to check the details of this repos you can add the -v (verbose) attribute/flag to the command

yum repolist -v

----

### Incase that some softwares are not available locally in your ISO files repos you have to install them anyhow then in that case we can download tem either online or from online repos that can also be configured in your system.

For that we have to set these repo form some online Repo libraries 

epel redhat library is one good option to choose 

sudo dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-9.noarch.rpm

(Please search online incase this link wont work)

after this command runs successfully you can now see there are 2 more repos added in your repolist 

$ dnf repolist / yum repolist

---




