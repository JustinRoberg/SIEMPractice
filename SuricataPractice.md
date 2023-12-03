# Examine Suricata alerts, logs, and rules.
 
## Description
 
  This was a project for the Google Cybersecurity Coursera course, tasking us with using Suricata to create custom rules, examine log outputs and monitor traffic captured in a packet capture file.
 
  <Details open><Summary>
  
  ### Goal

  </Summary>
  
 - Gain hands on practical experience running Suricata and using bash command line.
 
 - Examine custom rules in Suricata
 
 - Trigger a custom rule in Suricata
 
 </Details>
 
  <Details open><Summary>
  
 ### Scenario

  </Summary>

> "As a security analyst monitor traffic on your employer's network. Configure Suricata and use it to trigger alerts."

 </Details>
 
</Details>

## Tools Used

 <Details Open><Summary>

  ### Code

 </Summary>
 
  - Bash Shell
  - JSON
 
 </Details>

<Details Open><Summary>

 ### Environment

 </Summary>
 
  - Virtual Linux machine via Qwiklabs
  - Suricata

</Details>
 
 <Details Open><Summary>
 
  ### File Explanations

 </Summary>
 
`sample.pcap` - Provided packet capture file used for the exercise to test the Suricata rules

`custom.rules` - Provided file with custom rules for network traffic. I add additional rules to it during the project and test them against the `sample.pcap` file.

`fast.log` - Contains alerts that Suricata generates

`eve.json` - Main, standard, and default log for events, generated when Suricata runs. Located in `/var/log/suricata` directory. Contains detailed information and network telemetry events triggered by alerts.

</Details>


 ## Task 1 Examine a custom rule in Suricata

In the linux virtual machine for this lab I was given a file named `custom.rules` in the `/home/analyst` directory. I am then tasked with opening the file and defining the components to a Suricata rule. 

<Details Open><Summary><h3>Commands</h3></Summary>

 Since I am already in the directory, I use `cat custom.rules` to open the file. If the file was long I could also use the `less` command to only show one page at a time, but it is not neccessary for this file. 

`Cat` - is a command used to read data from a file and give it as an output.

<img width="900" alt="SuricataTask1a" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/11f5a3cc-afa6-45c2-bfa5-1adbed6b46aa">

This rule generates a text alert whenever Suricata observes the text `GET` from an HTTP packet from the home network going to an external network.

</Details>

<Details Open><Summary><h3>Definitions & Explanations</h3></Summary>
 
<Details Open><Summary><B>Action</B></Summary>
  The Action is the first part of the signature, defining what action to take if the conditions listed are met. In our rule the action listed is `alert`.
 
  **Common Actions** 
   - `alert` - Instructs to alert on selected network traffic. IDS will inspect the traffic packets and send out an alert in case it matches.
   - `drop` - Generates an alert, but it drops the traffic, only occurs when Suricata runs in IPS mode.
   - `pass` - Allows the traffic to pass through the network interface. 
   - `reject` - Does not allow the traffic to pass. Instead, a TCP reset packet will be sent, and Suricata will drop the matching packe

  </Details>
 
<Details Open><Summary><B>Header</B></Summary>
 
 `http $HOME_NET any -> $EXTERNAL_NET any` is the header for our rule. The header defines the signature's network traffic, which can include attributes such as protocols, destination and source IP addresses, destination and source ports, and traffic direction.

   - `http` - listed after the action keyword, which is the protocol field. 

   - `$HOME_NET any -> $EXTERNAL_NET any` - Parameters to the protocol field.
   
   - `->` - Indicates direction of traffic, in this case from the `$HOME_NET` to the destination `$EXTERNAL_NET`

   - `$` - indicates start of variable

   - `$HOME_NET` - Suricata variable defined in `suricata.yaml`. In my lab it is defined as `172.21.224.0/20` subnet.
   
   - `any` - Traffic from any port defined in the `$HOME_NET` network will be monitored and caught by Suricata.

  </Details>
  
<Details Open><Summary><B>Rule Options</B></Summary>
   
 Allow you to customize signatures with additional parameters. Configuring this can help specifiy network traffic. The rule options start after the `any` in the header. 
 
 - `msg` - Option that provides a text alert. `“GET on wire”` is the text that will print for our rule.
 
 - `flow:established,to_server` - Option determines that packets from the client to the server should be matched. 
 
 - `content:"GET"` - Option instructs Suricata to look for the word `GET` in the content of the `http.method` portion of a packet.
 
 - `sid:12345` - Signature ID rule that is a unique value to identify rule.
 
 - `rev:3` - Option indicates the signature's revision which is used to identify the signature's version.

 </Details>
</Details>

## Task 2 Trigger a custom rule in Suricata

Next I am tasked with triggering the rule above, and examining the alert log that Suricata will generate. I am given a `sample.pcap` file that I will process with Suricata then examine the log.

<Details Open><Summary><h3>Commands</h3></Summary>
    
First I make sure there are no logs in the `/var/log/suricata` folder:

```
ls -l /var/log/suricata
```

<img width="900" alt="SuricataTask2a" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/1147040f-89e9-4fc7-a465-46519271d850">

As I have not run Suricata on this virtual machine before there are no logs in the folder.

</Details>
   
 Next I will process `sample.pcap` with Suricata to trigger an alert and produce a log.

<Details Open><Summary><h3>Commands & Explanation</h3></Summary>

This is the command I use to run Suricata and read the `sample.pcap` file and examine it using the rules in `custom.rules` previously examined. I use `sudo` because it is needed for my virtual environment, but may not be needed for all environments.

`sudo suricata -r sample.pcap -S custom.rules -k none`

`-r  sample.pcap` - Specifies an input file to act as network traffic, for our example `sample.pcap`.

`-S custom.rules` - Tells Suricata to use the rules defined in `custom.rules`.

`-k none` - Instructs Suricata to disable all checksum checks. As this is a sample capture file, we don't need to check if a packet was changed in transit.

<img width="900" alt="SuricataTask2b" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/70a43ba3-08e3-43f4-aa98-0e20308d2ebc">

The output states how many packets have been processed by Suricata.

If Suricata adds any new alerts, from conditions of the rules being met, they will be in the `fast.log` file located on my virtual machine in `/var/log/suricata/`

</Details>

The next step is to check the Suricata log folder again. `/var/log/suricata` 

<Details Open><Summary><h3>Commands & Explanation</h3></Summary>

 ```
ls -l /var/log/suricata
```

<img width="900" alt="SuricataTask2c" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/edfebefa-d9a4-45c5-8e43-db50016dfd94">

We now see there a four new files in the log directory including `fast.log` and `eve.json`.

</Details>

 Next  I will use the `cat` command to display `fast.log`:

<Details Open><Summary><h3>Commands</h3></Summary>

 ```
 cat /var/log/suricata/fast.log
```

<img width="900" alt="SuricataTask2D" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/cd448437-ab0a-4824-b1cb-02f542483807">

We can see each entry in `fast.log` is an alert generated by Suricata as it processes network traffic against the `custom.rules` conditions. Each line will show the rule that triggered it, source, destination, and direction the traffic was heading.

</Details>

## Task 3 Examine eve.json output

Next I am asked to examine the `eve.json` file that Suricata had generated.

The `eve.json` log contains more data than the `fast.log` and is the main Suricata log file, it is stored in JSON format.


<Details Open><Summary><h3>Commands</h3></Summary>

I use the `cat` command to open the `eve.json` file.

```
cat /var/log/suricata/eve.json
``` 

<img width="900" alt="SuricataTask3a" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/a6a32465-80b2-483f-879d-011a0341bc96">

This is difficult to understand, so I will use `jq` and `less` to make the format easier to understand. 


```
jq . /var/log/suricata/eve.json | less
```

![SuricataTask3b](https://github.com/JustinRoberg/SIEMPractice/assets/133618188/cfb76362-fc8c-4a57-acf6-05c17410c0cd)

`jq` - Is a command-line tool used to interact with JSON data.

`|` - I use a pipe to send the output of the `jq` command into the `less` command. 

`less` - Allows the output to go page by page and be in a format that is more easily understood.

</Details>

Next I will use the `jq` command to extract specific event data from the `eve.json` file:

<Details Open><Summary><h3>Commands and Explanation</h3></Summary>

```
jq -c "[.timestamp,.flow_id,.alert.signature,.proto,.dest_ip]" /var/log/suricata/eve.json
```

This command will extract fields specified in the `[ ]` brackets. The fields selected are:

`.timestamp` - timestamp

`.flow_id` - flow id 

`.alert.signature` - shows the  alert signature or messages

`.proto` - protocol

`.dest_ip` - destination ip


<img width="900" alt="SuricataTask3c" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/62e822d9-9abc-4053-9e96-80a21739b46d">

</Details>

## Summary

In this lab I gained practical experience in using Suricata to

 - Create custom rules and run them in Suricata.
 
 - Monitor traffic captured in a packet capture file.
 
 - Examine the `fast.log` and `eve.json` output.


[Additional Reference](https://docs.suricata.io/en/latest/index.html)


