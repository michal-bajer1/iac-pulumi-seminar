---
layout: section
class: text-center
---

# Evolution of Infrastructure & Systems

<div class="opacity-80 italic mb-4">
Two parallel revolutions that shaped modern computing
</div>

<!--
# Speaker Notes

Setup:
- Frame history as context for modern tools
- Set expectation for parallel stories
- Connect to their development experience

Key Points:
- Two revolutions happened together
- Each drove the other forward
- Still evolving today

Questions/Engagement:
- "What infrastructure changes have you seen?"
- "How has development changed with it?"

Next:
- Let's look at infrastructure changes first
-->

---
layout: center
hideInToc: true
---

# Infrastructure Evolution Timeline
Major shifts in how we manage infrastructure over decades


```mermaid
timeline
    section 2000s
        Physical Era : Manual Operations
        : Datacenter Hardware
        : Weeks to Deploy
    section Late 2000s
        Virtualization : VMware & Hypervisors
        : Template-based
        : Days to Deploy
    section Early 2010s
        Cloud Era : API-driven Resources
        : On-demand Scaling
        : Minutes to Deploy
    section Late 2010s
        IaC Era : Code-defined
        : Version Controlled
        : Seconds to Deploy
```
<!--
# Speaker Notes

Setup:
- Visualize the transformation scale
- Focus on speed of change
- Note accelerating pace

Key Points:
- Each jump brought 10x improvement
- Changed how we think about servers
- Automation became essential

Questions/Engagement:
- "When did you start working with cloud?"
- "Which era's tools do you use?"

Next:
- See how these changes affected teams
-->

---
layout: center
hideInToc: true
---

# Systems Architecture Evolution
How software systems grew in complexity and scale

```mermaid
timeline
    section Early 2000s
        Monolithic : Single Application
        : One Database
        : Simple Deploy
    section Mid 2000s
        Service-Oriented : Multiple Services
        : Multiple Databases
        : Coordinated Deploy
    section 2010s
        Cloud Native : Microservices
        : Distributed Data
        : Container Deploy
        : Kubernetes
    section 2020s
        Modern : Serverless & Containers
        : Many services, many databases
        : Multi-cloud
        : Continuous Deployments
```

<!--
# Speaker Notes

Setup:
- Connect to their software experience
- System architecture drove infrastructure
- Still happening today

Key Points:
- Monolith: Simple but limiting
- Services: Team independence
- Cloud Native: Infrastructure complexity
- Modern: Mix of approaches

Questions/Engagement:
- "Have you worked on any team projects?"
- "Which architectures have you worked with?"
- "What drove your architecture choices?"

Next:
- See how this affected operations
-->

---
layout: center
hideInToc: true
---

# Infrastructure Evolution Metrics
Quantifying the impact of infrastructure transformation

<table class="metrics-table">
  <thead>
    <tr>
      <th>Era</th>
      <th>Time to Provision</th>
      <th>Servers per Admin</th>
    </tr>
  </thead>
  <tbody>
    <tr v-click="1">
      <td>Physical</td>
      <td>Weeks</td>
      <td>10</td>
    </tr>
    <tr v-click="2">
      <td>Virtual</td>
      <td>Days</td>
      <td>100</td>
    </tr>
    <tr v-click="3">
      <td>Cloud</td>
      <td>Minutes</td>
      <td>500</td>
    </tr>
    <tr v-click="4">
      <td>IaC</td>
      <td>Seconds</td>
      <td>1000+</td>
    </tr>
  </tbody>
</table>

<style>
.metrics-table {
  @apply w-4/5 mx-auto mt-8;
}
.metrics-table th {
  @apply px-6 py-3 text-left bg-blue-500 bg-opacity-10 font-semibold;
}
.metrics-table td {
  @apply px-6 py-4 border-t border-gray-200 border-opacity-50;
}
</style>

<!--
# Speaker Notes

Setup:
- These metrics don't show real impact, mostly ilustrate to idea
- Focus on two key metrics

Key Points:
- Deployment time: 10000x faster
- Admin capacity: 100x increase
- Every step multiplied capability

Questions/Engagement:
- "What enabled each jump?"
- "Which metric matters more?"

Next:
- Look at what drove these changes
-->

---
layout: center
hideInToc: true
---

# The Pets vs Cattle Revolution
A fundamental shift in infrastructure mindset

<div class="flex items-center justify-center gap-8">
  <div v-click class="text-center">
    <div class="text-6xl">🐈</div>
    <div class="mt-2 opacity-70">Named Servers</div>
    <div class="text-sm">("db-master")</div>
  </div>

  <div v-click class="text-5xl text-blue-400">
    →
  </div>

  <div v-click class="text-center">
    <div class="text-6xl">🐄</div>
    <div class="mt-2 opacity-70">Numbered Resources</div>
    <div class="text-sm">("web-042")</div>
  </div>
</div>

<!--
# Speaker Notes

Setup:
- Fundamental mindset shift
- Changed how we manage servers
- Still relevant today

Key message: Fundamental shift in how we think about servers

Additional context to mention:
- Pets: We care for them individually, nurse them back to health
- Cattle: Replaceable, automated management
- Like your laptop (pet) vs a Docker container (cattle)
- This mindset shift enabled modern cloud scaling

Questions/Engagement:
- "Where do you see each approach?"
- "Which fits cloud better?"-->

---
layout: center
hideInToc: true
---

# Quick Questions

<div class="text-xl space-y-8">
  <div v-click class="question">
    Who has deployed to the cloud?
  </div>

  <div v-click class="question">
    Experience with infrastructure tools?
  </div>

  <div v-click class="question">
    Automated deployment experience (CI/CD)?
  </div>

  <div v-click class="question">
    Which tech stack?
  </div>
</div>

<style>
.question {
  @apply p-4 rounded bg-blue-500 bg-opacity-10 cursor-pointer hover:bg-opacity-20 transition-all;
}
</style>

<!--
# Speaker Notes

Setup:
- Quick audience check
- Keep it light and interactive
- Watch for experience distribution

Key Points:
- Note cloud familiarity
- Infrastructure tool exposure
- Cloud provider preferences

Questions/Engagement:
- Use raised hands for each point
- Note which tools are familiar

Next:
- Adjust examples based on responses
-->