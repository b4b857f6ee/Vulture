# Splunk App for Vulture
The goal of this application is to provide a sourcetype for Splunk using the log of the WAF Vulture from the MongoDB Repository of the appliance
This application provide you the same dashboard you can found on the appliance directly.

Vulture project : https://www.vultureproject.org/

# Splunk - Installation

Connect to your splunk installation

create a index call "vulture"

cd $HOME_SPLUNK/etc/apps

wget https://github.com/b4b857f6ee/Vulture/archive/master.zip

unzip master.zip

 mv Vulture-master/vulture ./
 
 mv vulture Vulture
 
 rm -rf Vulture-master/
 
 chown splunk:splunk -R Vulture   (only if your are using Splunk as splunk user and not root)
 
 restart splunk
 
 Create a new input (in my case port 9601 and UDP protocol you can change it)
 
 Go to Settings -> Data inputs -> UDP -> Add New
  Select your port "9601" and the Source Type as vulture and the index as vulture
  
 That's it for the Splunk configuration
 
 
 # Vulture Configuration
 
Log configuration

Connect to your vulture GUI
Go to -> Repository -> Syslog -> Create new SyslogRepository with

Repository name "Splunk"
Syslog server IP address "Your Splunk IP"
Syslog server port number "9601" by default
Syslog protocol "UDP"
Syslog facility "local7"
Syslog security level "info"

Go to -> Configuration Profiles -> Logs -> "Default Log Profile (Repo) 	Vulture Internal Database (MongoDBRepository)"

In Optional syslog repository "Select your SyslogRepositoryName"

Go to Applications -> Applications -> Click on your App to edit -> Logs

Log Profile "Select the MongoDB repository"
Log Level "Error"

Restart your application, access to your website and you have to received your logs whan your access to your website.

Check the splunk index to be sure.

index=vulture
