# Chronicle Search Project

<details open><summary>
   
## Description
   
 </summary>

This was a project for the Google Cybersecurity course to get hands-on experience with Chronicle, a SIEM.

  <details open><Summary> 
  
  ### Goal 
  
  </Summary>

  - To use Chronicle to investigate a suspicious domain.
  - Identify assets that accessed the domain. 
  - Evaluate the HTTP events associated with the domain.
  - Identify which assets submitted login information to the domain.
  - Identify additional domains.

</details>

  <Details open><Summary>
  
  ### Scenario

  </Summary>
  
> "You are a security analyst at a financial services company. You receive an alert that an employee received a phishing email in their inbox. You review the alert and identify a suspicious domain name contained in the email's body: `signin.office365x24.com`. You need to determine whether any other employees have received phishing emails containing this domain and whether they have visited the domain. You will use Chronicle to investigate this domain." 

  </Details>
<Details open><Summary>  

  ###  Definitions

  </Summary>
  
- `Siem` - Security information and event management - tools that collect and analyze log data to monitor critical activities
    
- `Chronicle` - a cloud native SIEM, a platform for collecting, analyzing and reporting on data from different sources
    
- `Udm` - Unified Data Model Search - Default search type in Chronicle. Searches data that has been normalized, ingested and parsed already. This type of search is faster than the raw log search 
    
- `Raw data search` - Searches raw unparsed logs, supports use of regular expressions.
  
  </Details>
</details>

<details open>
  <summary>

## Tools Used
  
  </summary>

 ### **Commands/Code**
   * [Unified Data Model field list](https://cloud.google.com/chronicle/docs/reference/udm-field-list)
 ### **Environment**
   * Chronicle Web Platform - Lab Version
   * Chrome Browser
      
</details>

<Details open>
  <Summary>
    
 ## Step 1 - Launch Chronicle

</summary>

We will launch [Chronicle's learning lab](http://goo.gle/chroniclelab) to complete the scenario.


<img align="center" width="900" alt="Chronicle1" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/4b6225a5-1000-4499-9268-a1f0cf47ef2e">

Chronicle is Google's cloud native SIEM, a platform for collecting, analyzing and reporting on data from different sources.

A SIEM, or Security Information and Event Management, are tools that collect and analyze log data to monitor critical activities.


</details>

<Details open>
  <Summary>
    
 ## Step 2 - Perform a Domain Search

  </Summary>
  
<img align="center" width="900" alt="Chronicle2" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/419fcb3d-03bc-4aa6-b0f8-3f37c77a44cd">


For the scenario we are looking for a domain that was contained in a phishing e-mail. I search for `signin.office365x24.com` domain. Under the **DOMAINS** section `signin.office365x24.com` will be listed if it exists in the ingested data. I then click `signin.office365x24.com` to complete the search.

</details>

<Details open>
  <Summary>

 ## Step 3 - Evaluate the search results

  </Summary>

  Though not required for the scenario, I will go through each "Insight Card". (Mostly for future reference if needed, feel free to minimize section to skip)
  
<img align="center" width="900" alt="chronicle3" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/eb81faf7-eba2-4a9e-911e-ad3f600a4ea8">

   <Details Open><Summary><h3>VT Context</h3></Summary>
      
   ***VT CONTEXT*** - Provides VirusTotal information available on the domain.
 
      
   <img align="center" width="450" alt="Chronicle3_1VTcontext" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/9af6b69f-fba1-4de2-814c-e583cd094a09">

   </Details>

   <Details Open><Summary><h3>WhoIS</h3></Summary> 

   ***WHOIS*** - Free and publicly available directory that includes information on registered domains. Useful for assessing a domain's reputation and origin.

   <img width="900" alt="Chronicle3_2WhoIS" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/4bced61d-ea5c-41f6-ad53-68b05696cf18">

   </Details>

   <Details Open><Summary><h3>Prevalance</h3></Summary>  

   ***Prevalance*** - Provides a graph showing if a domain has been accessed previously. Usually less prevalent domains can be an indication of a greater threat.
   
   <img width="900" alt="Chronicle3_3Prevalence" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/f99bc982-7e27-4b8b-9a09-a25eef712f96">
   </Details>

   <Details Open><Summary><H3>Resolved IPs, Sibling Domains, ET Intelligence Rep List</H3></Summary>

   ***RESOLVED IPS*** - Maps domain to IP Address. IP address can then be clicked to create a new search in Chronicle for the IP Address allowing for further investigation, and information if there is a broader compromise. `signin.office365x24.com` maps to `40.100.174.34`.
   
   ***SIBLING DOMAINS*** - Provides additional information about the domain, focusing on common parent domains. Listed here for our search of `signin.office365x24.com` is the top domain `office365x24.com` and sibling domain `login.office365x24.com`.  
   
   ***ET INTELLIGENCE REP LIST*** - Provides threat intelligence information using ProofPoint's Emerging Threats (ET) Intelligence Rep List. 

   <img width="900" alt="Chronicle3_456ResolvedIPSSiblingDomainsETIntelligenceRepList" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/7b0ec115-9b0a-4923-8166-651d5c19ad07">

   </Details>

   <Details Open><Summary><h3>Timeline</h3></Summary>

   ***TIMELINE*** - Includes events and interactions with the domain. Clicking **EXPAND** will show `GET` and `Post` requests.

   `GET` - request that retrieves data from a server.

   `POST` - request that submits data to a server.

   <img width="450" alt="Chronicle3_7Timeline" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/e75a82cb-b9c7-4ee5-a88a-4a773ea5091d">

   </Details>

   <Details Open><Summary><h3>Assets</h3></Summary>

   ***ASSETS*** - Details a list of assets that have interacted with the domain.
   
   <img width="450" alt="Chronicle3_8Assets" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/8c767b00-3526-4b78-a04c-d7cc82a83668">
   </Details>
</Details>

<Details open>
  <Summary>
    
## Step 4 - Investigate the threat intelligence data

  </Summary>

First I check **VT CONTEXT** to see if there is any VirusTotal data on the domain. There is none.
  
<img width="900" alt="Chronicle4_1" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/6ae6b72b-4c93-4a96-9784-f04ac0faf2c0">

I then access the **Top Private Domain** `office365x24.com` to view any **VT CONTEXT** on the top domain.

<img width="900" alt="Chronicle4_2a" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/17b4167b-c7be-4b7d-b970-97296810ef24">

Four vendors have flagged this domain as malicious.

<img width="900" alt="Chronicle4_2b" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/688148a3-fc98-4f29-9af2-73c186a1a390">

I then look at the **ET INTELLIGENCE REP LIST** insight card.

<img width="450" alt="4_3a" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/147d0bb0-13e6-4498-b276-0c76671e4ace">


</Details>

<details open>
  <summary>
    
## Step 5 - Investigate the affected assets and events

   </summary>

Assets that accessed the domain:
   
<img width="450" alt="5_1a" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/3914b029-a456-4406-be81-af9e7983afcd">

Timeline of HTTP requests including `GET` and `POST`

The `Post` requests to `/login.php` could indicate the transfer of login information.

<img width="450" alt="5_2a" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/1477a867-2192-464f-824e-c26745759f32">

Raw log viewer can give more details about each of the connections:


<img width="900" alt="5_2b" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/0acde163-f839-4763-b78f-078f680127c4">


</details>

<details open>
  <summary>
    
## Step 6 - Investigate the resolved IP address

  </Summary>

  Based on the affected assets, and `POST` requests the domain is most likely malicious. Next I will investigate the IP address found under the **Resolved IPS** to identify if there are other domains being used.
  
<img width="450" alt="Chronicle6_1a" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/e60ac1a4-de1e-461b-a2dd-341699a33551">

Under **RESOLVED IPS** the address `40.100.174.34` can be selected. 

<img width="900" alt="Chronicle6_2a" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/cd23759f-5cb0-4f95-9101-856454bf19df">

After selecting the address, a timeline of requests can be seen. `POST` requests may indicate an asset has be phished. These are worth noting.

<img width="450" alt="Chronicle6_2a1" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/cbacd021-71e7-4810-b070-18061f258d4c">

We can also see additionally affected assets.

<img width="450" alt="Chronicle6_2b" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/b93a4cbb-bf8e-4eae-8185-49c6917fe1a5">

Listed are other domains associated with the IP address.

<img width="450" alt="Chronicle 6_2c" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/d8aaaaec-040d-44f7-9935-a900a9007150">

A mock incident journal was created along with this lab and will be uploaded eventually.

</details>

<Details open>
  <Summary>
    
 ## Conclusion

  </Summary>
    
 In this Lab I used Chronicle to:
 
   * Access threat intelligence reports on the domain
         - Determined the behavior of `signin.office365x24.com` as  drop site for logs and stolen credentials. According to ET Intelligence Rep List
   * Identify the assets that accessed the domain
         - `roger-spence-pc`, `emil-palmer-pc`, `coral-alverez-pc`, `ashton-davidson-pc`, `jude-res-pc`,`bruce-monroe-pc`, are assets that accessed domain
   * Evaluate the HTTP events associated with the domain
         - Two `POST` requests were made to the do the domain. Indicating the submission of sensitive data.
   * Identify which assets submitted login information to the domain
         - `ashton-davidson-pc`, `emil-palmer-pc` submitted login information.
   * Identify additional domains 
         - `40.100.174.34` resolves to `signin.office365x24.com` as well as `signin.accounts-google.com`
     
After investigating the suspicious domain, I determined that it was involved in phishing campaigns. I also determined via Post requests to the domain, that login information had been submitted to the domain. I also identified two domains that were also related to the domain that I was investigating. 

</Details>
