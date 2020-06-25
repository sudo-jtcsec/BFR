# BFR
Yet another recon script, except this is the first one I made

Includes objects for storing an asset, its different pages, and findings. Has functionality for using Discord Webhook to send myself updates when im too lazy to sit at my computer and the script takes hours to finish

Current flow:
- Use Sublister to find subdomains
- Create asset object
- Iterate through assets and perform the following:
  - NMAP and store output
    - send discord update
  - Run dirsearch on subdomain
    - TO DO: currently only check 443. Dynamically change protocol and port based off of NMAP output
    - TO DO: Check dirsearch extensions for analysis
  - Iterate through subdomains
    - If status code from dirsearch was 200, use requests module to retrieve and store cookies, headers, and response
    - Repeat requests injecting a variety of headers for potential SSRF
      - TO DO: don't hardocde IP
      - TO DO: dynamically check output and add finding if pingback recieved
  - To Do: analyze assit lists based off of modular definitions
    - Type: substring or regex
    - Where to check - all files, js files, headers, cookies, etc.
    - Confiednce level
  
