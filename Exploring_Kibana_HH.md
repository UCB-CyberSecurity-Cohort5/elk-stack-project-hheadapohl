## Activity File: Exploring Kibana

* You are a DevOps professional and have set up monitoring for one of your web servers. You are collecting all sorts of web log data and it is your job to review the data regularly to make sure everything is running smoothly.

* Today, you notice something strange in the logs and you want to take a closer look.

* Your task: Explore the web server logs to see if there's anything unusual. Specifically, you will:

:warning: **Heads Up**: These sample logs are specific to the time you view them. As such, your answers will be different from the answers provided in the solution file.

---

### Instructions

1. Add the sample web log data to Kibana.

2. Answer the following questions:

    - In the last 7 days, how many unique visitors were located in India?
        - 250 unique visitors
    - In the last 24 hours, of the visitors from China, how many were using Mac OSX?
        - 16.98% of users were using Mac OSX
    - In the last 2 days, what percentage of visitors received 404 errors? How about 503 errors?
        - 33.33% of users received 404 errors, 0% received 503 errors
    - In the last 7 days, what country produced the majority of the traffic on the website?
        - China, with 310 unique visitors
    - Of the traffic that's coming from that country, what time of day had the highest amount of activity?
        - 12:00PM
    - List all the types of downloaded files that have been identified for the last 7 days, along with a short description of each file type (use Google if you aren't sure about a particular file type).
      - .gz (gzip compressed file)
      - .css (cascading style sheet - used to format contents of web pages)
      - .zip (lossless compressed file format)
      - .deb (Debian Linux Package File - used for installation packages for Debian Linux distributions)
      - .rpm (Red Hat Package Manager package file - used for installation packages for Red Hat distributions of Linux)

3. Now that you have a feel for the data, Let's dive a bit deeper. Look at the chart that shows Unique Visitors Vs. Average Bytes.
     - Locate the time frame in the last 7 days with the most amount of bytes (activity).
        - 03-20-2022 at 21:00 hours
     - In your own words, is there anything that seems potentially strange about this activity?
        - There is only one unique visitor, but around 16000 average bytes. One would expect average bytes to track with number of unique visitors, but a huge spike in average bytes at a single point in time by a single user indicates that this user was transferring a disproportionate and suspicious amount of data.

4. Filter the data by this event.
     - What is the timestamp for this event?
        - 03-20-2022 at 22:55
     - What kind of file was downloaded?
        - A .rpm file
     - From what country did this activity originate?
        - India
     - What HTTP response codes were encountered by this visitor?
        - HTTP response code 200, meaning no errors.

5. Switch to the Kibana Discover page to see more details about this activity.
     - What is the source IP address of this activity?
        - 35.143.166.159
     - What are the geo coordinates of this activity?
        - "lat": 43.34121, "lon": -73.6103075
     - What OS was the source machine running?
        - Windows 8
     - What is the full URL that was accessed?
        - https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-6.3.2-i686.rpm
     - From what website did the visitor's traffic originate?
        - http://facebook.com/success/jay-c-buckey


6. Finish your investigation with a short overview of your insights.

     - What do you think the user was doing?
        - The user was downloading a metricbeat RPM file (a linux package)
     - Was the file they downloaded malicious? If not, what is the file used for?
        - No, metricbeat just monitors system activity. But the activity itself is suspicious.
     - Is there anything that seems suspicious about this activity?
        - Certainly. Downloading random Linux packages from a foreign country in the middle of the night is not normal activity
     - Is any of the traffic you inspected potentially outside of compliance guidlines?
        - The fact that the package was downloaded from India outside of working hours (10:55PM) is a red flag for someone breaking company protocol/compliance guidelines.

---
?? 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
