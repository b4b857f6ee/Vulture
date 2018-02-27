================================================
Overview
================================================

The goal of this application is to provide a sourcetype for Splunk using the log of the WAF Vulture from the MongoDB Repository of the appliance
This application provide you the same dashboard you can found on the appliance directly.

================================================
Splunk - Configuration
================================================

Install this app into Splunk by doing the following:

  1. Log in to Splunk Web and navigate to "Apps » Manage Apps" via the app dropdown at the top left of Splunk's user interface
  2. Click the "install app from file" button
  3. Upload the file by clicking "Choose file" and selecting the app
  4. Click upload
  5. Restart Splunk if a dialog asks you to

Once the app is installed, you have to create a new index and a new input:

  1. Create a new index, Go to Settings -> Indexes -> New indexes -> name it as "vulture" (the dashboard work with this index)
  2. Create a new input
,
 Go to Settings -> Data inputs -> UDP -> Add New
  Select your port "9601"(for exemple) and the Source Type as vulture and the index as vulture

================================================
Vulture - Configuration
================================================

Log configuration



  1. Connect to your vulture GUI
Go to -> Repository -> Syslog
  2. Create new SyslogRepository with

Repository name "Splunk"
Syslog server IP address "Your Splunk IP"
Syslog server port number "9601"(for exemple) by default
Syslog protocol "UDP"
Syslog facility "local7"
Syslog security level "info"


  3. Go to -> Configuration Profiles -> Logs -> "Default Log Profile (Repo) 	Vulture Internal Database (MongoDBRepository)"

In Optional syslog repository "Select your SyslogRepositoryName"


  4. Go to Applications -> Applications -> Click on your App to edit -> Logs

Log Profile "Select the MongoDB repository"
Log Level "Error"

Restart your application, access to your website and you have to received your logs whan your access to your website.


  5. Check the splunk index to be sure in a search tab search :"

index=vulture"

================================================
Getting Support
================================================

Go to the following website if you need support

OR

You can access the source-code and get technical details about the app

  -->  https://github.com/b4b857f6ee/Splunk_Vulture