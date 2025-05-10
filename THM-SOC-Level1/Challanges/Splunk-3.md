1 . How many logs are ingested from the month of March, 2022?
  - Filtered the search by date
  - ![](../../images/Splunk-3/Splunk-3-1.png)
2 . Imposter Alert: There seems to be an imposter account observed in the logs, what is the name of that user?
  - Listed all the users and noticed a very odd username
  - ![](../../images/Splunk-3/Splunk-3-2.png)
3 . Which user from the HR department was observed to be running scheduled tasks?
  - Filtered search by users and schedule command line to find the answer
  - ![](../../images/Splunk-3/Splunk-3-3.png)
4 . Which user from the HR department executed a system process (LOLBIN) to download a payload from a file-sharing host.
  - Filtered users by commandline and saw certutil.exe downloaded by user Haroon
  - ![](../../images/Splunk-3/Splunk-3-4-1.png)
  - ![](../../images/Splunk-3/Splunk-3-4-2.png)
5 . To bypass the security controls, which system process (lolbin) was used to download a payload from the internet?
  - Found the answer on the same page
  - ![](../../images/Splunk-3/Splunk-3-5.png)
6 . What was the date that this binary was executed by the infected host? format (YYYY-MM-DD)
  - Found the answer on the same page
  - ![](../../images/Splunk-3/Splunk-3-6.png)
7 . Which third-party site was accessed to download the malicious payload?
  - Found the answer on the same page
  - ![](../../images/Splunk-3/Splunk-3-7.png)
8 . What is the name of the file that was saved on the host machine from the C2 server during the post-exploitation phase?
  - Found the answer on the same page
  - ![](../../images/Splunk-3/Splunk-3-8.png)
9 . The suspicious file downloaded from the C2 server contained malicious content with the pattern THM{..........}; what is that pattern?
  - After visiting the website sad the flag
  - ![](../../images/Splunk-3/Splunk-3-9.png)
10. What is the URL that the infected host connected to?
  - Coppied the link
  - ![](../../images/Splunk-3/Splunk-3-0.png)
