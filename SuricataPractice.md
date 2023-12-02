# Examine Suricata alerts, logs, and rules.


## Description
 
  This was a project for the Google Cybersecurity Coursera course, tasking us with using Suricata to create custom rules, examine log outputs and monitor traffic captured in a packet capture file.

<Details open><Summary>
  
  ### Goal

  </Summary>
  
- Gain hands on practical experience running Suricata and using bash command line.

<Details open><Summary>
  
### Scenario

  </Summary>

> "As a security analyst monitor traffic on your employer's network. Configure Suricata and use it to trigger alerts."

</Details>

## Tools Used
 ### - Code
  - Bash Shell
  - JSON

## File Definitions
`sample.pcap` - provided packet capture file used for the exercise to test the Suricata rules

`custom.rules` - provided file with a custom rule. I add additional rules to it during the project and test them against the `sample.pcap` file.

`fast.log` - Contains alerts that Suricata generates

`eve.json` - Main, standard, and default log for events, generated when Suricata runs. Located in `/var/log/suricata` directory. Contains detailed information and network telemetry events triggered by alerts.


 ### - Environment
  - Virtual Linux machine via Qwiklabs
  - Suricata

 ## Task 1 Examine a custom rule in Suricata

  `/home/analyst` contains `custom.rules` file which defines what Suricata captures
- Use `cat custom.rules` to display the rules in file.
[Picture of `cat custom.rules` display]

### Action
*Action* - First part of the signature. 

`alert` - 

*Common actions are:*

`drop` - 

`pass` - 

`reject`

### Header
*Header* - defines the signature's network traffic, which can include attributes such as protocols, destination and source IP addresses, destination and source ports, and traffic direction.

`http`

`$HOME_NET any -> $EXTERNAL_NET any` - 

`$` - indicates start of variable

### Rule Options

*Rule options* - allow you to customize signatures with additional parameters. Configuring this can help specifiy network traffic you wish to find. 



 ## Task 2


 ## Task 3


 ## Step 4


 ## Step 5 


 ## Step 6

## Conclusion
