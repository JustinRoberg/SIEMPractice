# Perform Query with Splunk 
<Details open><Summary>

  ## Description

  </Summary>
  
  This was a project for the Google Cybersecurity Coursera course, tasking us with using Splunk Cloud to perform a search and investigation to gain hands-on experience with a SIEM.

<Details open><Summary>  

  ### - Goal

  </Summary>

  *  Upload sample log data 

  * Search through indexed data

  *  Evaluate search results

  * Identify different data sources 

  * Locate failed SSH login(s) for the root account
  
  </Details>
  
<Details Open><Summary>
  
  ### - Scenario

</Summary>

> "You are a security analyst working at the e-commerce store Buttercup Games. You've been tasked with identifying whether there are any possible security issues with the mail server. To do so, you must explore any failed SSH logins for the root account."  

</Details>

<Details Open><Summary>
  
## Tools Used

</Summary>

  <Details Open><Summary>
    
  ### Code/Commands

  </Summary>

  **SPL** - Search Processing Language - Splink's own querying language. USed to retrieve and search through events in Splunk.
  
  `index=main` - Retrieve events from an `index` named `main`
  
  `|` - **Pipe** - in SPL, pipes `|` are used to seperate commands as well as chain commands together sending one output into the next command.
  
  `*` - **Wildcard** - Used to match characters in string values, useful in Splunk to find data that is similar but not identical.
  
  [Further Reference](https://docs.splunk.com/Documentation/Splunk/9.0.2/SearchReference/UnderstandingSPLsyntax)
    
  </Details>

  <Details Open><Summary>
    
  ### Environment

  </Summary>
  
  * Splunk Cloud
  * Web Browser
    
  </Details>
 
 </Details>

 <Details open><Summary>
   
 ## Step 1 Upload Data into Splunk

  </Summary>

  To start the Lab we were given a zip file with data to upload to Splunk to ingest and index. I will also set up a Splunk Cloud instance to work with the data.

  <img width="450" alt="SplunkPart1a" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/9c138b64-819e-4642-bcf3-69aeeb8df980">

  The instance settings are as follow:
  ```
  Input Type: Uploaded File
  File Name: tutorialdata.zip
  Source Type: Automatic
  Host: Source path segment number: 1 
  Index: Default

  ```
  </Details>

<Details open><Summary>
   
 ## Step 2 Understanding A Basic Search

  </Summary>
 
   In the following step I will conduct a basic `index=main` search as well as define the retrieved fields for reference.
  
  <img width="900" alt="08218c7c097b14b42ef02965350a088e" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/e14ea3dd-5d54-4e25-b7ec-dbc7b9f9650e">

 There are several field values that are returned. Under **SELECTED FIELDS** there are the following designations to be defined:

  **Host** - The host field specifies the name of the network host from which the event originated. In this search there are five hosts:

   * **mailsv** - Buttercup Games' mail server. Examine events generated from this host.

   * **www1** - This is one of Buttercup Games' web applications.

   * **www2** - This is one of Buttercup Games' web applications.

   * **www3** - This is one of Buttercup Games' web applications.

   * **vendor_sales** - Information about Buttercup Games' retail sales.

  **source** - The source field indicates the file name from which the event originates. 

  **sourcetype** - The sourcetype determines how data is formatted. 
  
  </Details>

  <Details open><Summary>
   
    
 ## Step 3 Narrow Search

  </Summary>

  The original search `index=main` returned over 100,000 events. I need to narrow down the results to find any failed SSH logins for the root account on the mail server.

  I clear the search and input `index=main host=mailsv` which instructs splunk to return events in the index named "main" only if they are from the mail server.

  This brings the returned results to over 9000.
   
  <img width="900" alt="419cfeb25956eb361ed5cd871e03a352" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/e14bd12b-151d-45de-ab7d-da5d441b81ae">

  </Details>

  <Details open><Summary>
   
 ## Step 4 Search for Failed Login for Root / Evaluate Results

  </Summary>

   I continue to narrow the search results of the events for the mail server. I add `fail* root` to the previous search. 

  `index=main host=mailsv fail* root`

   The wildcard `*` on "fail" will tell splunk to search for terms that contain "fail", like failed. `root` keyword tells Splunk to include any event that contains the term "root" which is what we are searching for.

  
  <img width="900" alt="2cc856c052b8e4dfa5b90c27765e7e96" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/d6e7ee38-041d-45ba-a52f-25c6ea4f7552">

  This brings the results down to just over 300 events. Indicating that there are over 300 failed SSH logins for the root account on the mail server.

  
  </Details>

     

  <Details open><Summary>
   
 ## Conclusion

  </Summary>

  In the lab I was able to use Splunk to find over 300 failed SSH logins. This activity was part of a series of scenarios that were to documented in a mock incident journal. I hope to upload and add the journal to the project in the near future.
  
  </Details>
