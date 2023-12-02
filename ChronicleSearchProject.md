# Chronicle Search Project

This was a project for the Google Cybersecurity course to get hands-on experience with Chronicle, a SIEM.

<details open><summary>
   
## Description
   
 </summary>


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
  
- Siem - Security information and event management - tools that collect and analayze log data to monitor critical activities
    
- Chronicle - a cloud native SIEM, a platform for collecting, analyzing and reporting on data from different sources
    
- Udm - Unified Data Model Search - Default search type in Chronicle. Searches data that has been normalized, ingested and parsed already. This type of search is faster than the raw log search 
    
- Raw data search
  </Details>
</details>

<details open>
  <summary>

## Tools used
  
  </summary>

 ### - Commands/Code
      -
 ### - Environment
      - Chronicle Web Platform
</details>

<Details open>
  <Summary>
    
 ## Step 1 - Launch Chronicle

</summary>

<img align="center" width="900" alt="Chronicle1" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/4b6225a5-1000-4499-9268-a1f0cf47ef2e">

</details>

<Details open>
  <Summary>
    
 ## Step 2 - Perform a Domain Search

  </Summary>
  
<img align="center" width="900" alt="Chronicle2" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/419fcb3d-03bc-4aa6-b0f8-3f37c77a44cd">

</details>

<Details open>
  <Summary>

 ## Step 3 - Evaluate the search results

  </Summary>
  
<img align="center" width="900" alt="chronicle3" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/eb81faf7-eba2-4a9e-911e-ad3f600a4ea8">

VT context - *

<img width="380" alt="Chronicle3_1VTcontext" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/9af6b69f-fba1-4de2-814c-e583cd094a09">

WhoIS - *

<img width="727" alt="Chronicle3_2WhoIS" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/4bced61d-ea5c-41f6-ad53-68b05696cf18">

Prevalance - *

<img width="1172" alt="Chronicle3_3Prevalence" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/f99bc982-7e27-4b8b-9a09-a25eef712f96">


<img width="720" alt="Chronicle3_456ResolvedIPSSiblingDomainsETIntelligenceRepList" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/7b0ec115-9b0a-4923-8166-651d5c19ad07">

<img width="478" alt="Chronicle3_7Timeline" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/e75a82cb-b9c7-4ee5-a88a-4a773ea5091d">

<img width="482" alt="Chronicle3_8Assets" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/8c767b00-3526-4b78-a04c-d7cc82a83668">

</Details>

<Details open>
  <Summary>
    
## Step 4 - Investigate the threat intelligence data

  </Summary>
  
<img width="1264" alt="Chronicle4_1" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/6ae6b72b-4c93-4a96-9784-f04ac0faf2c0">

<img width="1176" alt="Chronicle4_2a" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/17b4167b-c7be-4b7d-b970-97296810ef24">

<img width="1035" alt="Chronicle4_2b" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/688148a3-fc98-4f29-9af2-73c186a1a390">

<img width="213" alt="4_3a" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/147d0bb0-13e6-4498-b276-0c76671e4ace">

</Details>

<details open>
  <summary>
    
## Step 5 - Investigate the affected assets and events

   </summary>
   
<img width="483" alt="5_1a" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/3914b029-a456-4406-be81-af9e7983afcd">

<img width="482" alt="5_2a" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/1477a867-2192-464f-824e-c26745759f32">

<img width="1648" alt="5_2b" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/0acde163-f839-4763-b78f-078f680127c4">

</details>

<details open>
  <summary>
    
## Step 6 - Investigate the resolved IP address

  </Summary>
  
<img width="219" alt="Chronicle6_1a" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/e60ac1a4-de1e-461b-a2dd-341699a33551">

<img width="1651" alt="Chronicle6_2a" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/cd23759f-5cb0-4f95-9101-856454bf19df">

<img width="479" alt="Chronicle6_2a1" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/cbacd021-71e7-4810-b070-18061f258d4c">

<img width="480" alt="Chronicle6_2b" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/b93a4cbb-bf8e-4eae-8185-49c6917fe1a5">

<img width="479" alt="Chronicle 6_2c" src="https://github.com/JustinRoberg/SIEMPractice/assets/133618188/d8aaaaec-040d-44f7-9935-a900a9007150">

</details>

<Details open>
  <Summary>
    
 ## Conclusion

  </Summary>
    
 In this activity, you used Chronicle to investigate a suspicious domain used in a phishing email. Using Chronicle's domain search, you were able to:
 
- Access threat intelligence reports on the domain
- Identify the assets that accessed the domain

- Evaluate the HTTP events associated with the domain

Identify which assets submitted login information to the domain

Identify additional domains 

After investigation, you determined that the suspicious domain has been involved in phishing campaigns. You also determined that multiple assets might have been impacted by the phishing campaign as logs showed that login information was submitted to the suspicious domain via POST requests. Finally, you identified two additional domains related to the suspicious domain by examining the resolved IP address. 
</Details>
