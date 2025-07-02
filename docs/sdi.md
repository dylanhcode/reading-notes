# System Design Interview - An Insider's Guide
**Status**: 🕓 In Progress  

---

## 🧠 Summary
A brief summary of the book in 2–5 sentences. What is the core idea? What’s the tone? Who should read this?

---

## ✍️ Key Ideas

- Idea 1: A short bullet or paragraph explanation
- Idea 2: ...
- Idea 3: ...

---

## ✅ Actionable Takeaways

- [ ] Thing to try in real life
- [ ] Behavior to adopt
- [ ] Insight to revisit later

---

## 🧷 Notes by Chapter

### Chapter 1: Scale From Zero to Millions of Users

- Goal
    - build a system that supports a **single user** => **millions of users**

- Single server setup
    - Web app:
        - backend: Java, Python, etc
            - handle business logic, storage, etc.
        - frontend: HTML, JavaScript
            - presentation
    - Mobile app:
        - communication: HTTP
        - API response format: most commonly used JSON

    <div style="text-align: center;">
    <img src="https://raw.githubusercontent.com/dylanhcode/reading-notes/main/images/image0.png" alt="Single Server Request Flow Diagram" style="width:600px;"/>
    </div>

- Database
    - with increasing users, we need multiple servers: one for web/mobile traffic, the other for the DB. 
        - Separating web/mobile traffic (web tier) and database (data tier) servers allows them to be scaled independently.

    <div style="text-align: center;">
    <img src="https://raw.githubusercontent.com/dylanhcode/reading-notes/main/images/image1.png" alt="Database Diagram" style="width:600px;"/>
    </div>

- Load balancer (Web Tier)
    - Users/clients connect to the public IP of the load balancer directly => load balancer connects to the web servers via private IPs* (*: IP addr only reachable between servers in the same network).
        - web servers are unreachable directly by clients for better security.

    <div style="text-align: center;">
    <img src="https://raw.githubusercontent.com/dylanhcode/reading-notes/main/images/image2.png" alt="Load Balancer Diagram" style="width:600px;"/>
    </div>

    - Benefits:
        - solved no-failover* (*: a system lacks the ability to automatically switch to a backup or redundant system when the primary system fails or becomes unavailable) issue.
            - if one server goes offline, all the traffic will be routed to the other server => prevent the website from going down.
        - improved the availability of the web tier.
            - if web traffic grows rapidly which requires more servers than two => the load balancer can handle adding new servers gracefully => once new servers added to the web server pool, requests will be routed to them automatically by load balancer.

- Database replication (Data Tier)

### Chapter 2: Title

...

