---
layout: section
class: text-center
---

# Infrastructure as Code Foundations

<div class="opacity-80 italic mb-4">
From manual clicks to infrastructure at scale
</div>

<!--
# Speaker Notes

Setup:
- Bridge from history to solutions
- Frame the fundamental challenge
- Connect to their experiences

Key Points:
- Manual ways don't scale
- Teams need better tools
- Common patterns emerge

Questions/Engagement:
- "How do you handle infrastructure now?"
- "What problems do you face?"

Next:
- Show traditional approach first
-->

---
layout: center
hideInToc: true
---

# The Modern Challenge of Growth
Building and scaling your first application

<div class="flex gap-12">
  <div v-click class="challenge-box">
    <div class="text-xl mb-2">Initial Setup</div>
    <ul>
      <li>Small team (3 developers)</li>
      <li>Promising app with database</li>
    </ul>
  </div>

  <div v-click class="challenge-box">
    <div class="text-xl mb-2">Growing Pains</div>
    <ul>
      <li>Manual Azure setup</li>
      <li>Configuration complexity</li>
      <li>Multiple environments needed</li>
      <li>Team coordination needed</li>
    </ul>
  </div>
</div>

<style>
.challenge-box {
  @apply p-4 rounded bg-gray-100 bg-opacity-10;
}
</style>

<!--
# Speaker Notes

Setup:
- Realistic scenario they'll face
- Common startup journey
- Growing pains are normal

Key Points:
- Small team, big ambitions
- Manual processes break down
- Need for automation appears

Questions/Engagement:
- "Seen these challenges?"
- "How would you solve them?"

Next:
- Look at two possible approaches
-->

---
layout: center
hideInToc: true
---

# Two Ways to Create Infrastructure

<div class="flex justify-center gap-16">
  <div v-click class="flex flex-col items-center">
    <div class="text-4xl mb-4">👆</div>
    <div class="text-xl font-bold mb-4">Click. Click. Click...</div>
    <div class="text-6xl">
      🖥️
    </div>
  </div>

  <div v-click class="flex flex-col items-center">
    <div class="text-4xl mb-4">⌨️</div>
    <div class="text-xl font-bold mb-4">Code Once, Deploy Many</div>
    <div class="code-box">
      resource webApp {
        name = "myapp"
        ...
      }
    </div>
  </div>
</div>

<div v-click class="mt-12 text-center text-xl">
  Let's see what this means in practice...
  (demo in Azure)
</div>

<style>
.code-box {
  @apply font-mono p-4 rounded bg-blue-300 bg-opacity-30 text-sm;
}
</style>

<!--
# Speaker Notes

Setup:
- Contrast traditional vs modern
- Both achieve same result
- Different long-term impacts

Key Points:
- Clicking: Fast start, hard to scale
- Code: Initial investment, long-term gain
- Both valid in different contexts

Questions/Engagement:
- "Which have you tried?"
- "What were the results?"

Demo plan:
1. "Let me show you the traditional way first..."
2. Open Azure Portal
3. Start creating a web app
4. Point out:
   - Many clicks needed
   - Many decisions to make
   - Easy to miss steps
   - Hard to document
   - Even harder to repeat exactly

Questions to ask:
- "How would you document all these steps?"
- "How would you share this with your team?"
- "What happens when you need 10 of these?"
-->

---
layout: center
hideInToc: true
---

# Issues with Manual Management
Why clicking doesn't scale

<div class="grid grid-cols-2 gap-8 mt-8">
  <div v-click class="issue-box">
    <div class="text-xl mb-2">Process Issues</div>
    <ul>
      <li>Hard to replicate</li>
      <li>No history tracking</li>
      <li>Error-prone</li>
    </ul>
  </div>

  <div v-click class="issue-box">
    <div class="text-xl mb-2">Team Issues</div>
    <ul>
      <li>Team coordination challenges</li>
      <li>Tribal knowledge</li>
      <li>Configuration drift</li>
    </ul>
  </div>
</div>

<div v-click class="mt-12 text-center text-xl bg-blue-500 bg-opacity-10 p-4 rounded">
  So how can we do this better?
</div>

<style>
.issue-box {
  @apply p-4 rounded bg-gray-100 bg-opacity-10;
}
</style>

<!--
# Speaker Notes

Setup:
- Real problems from experience
- Not theoretical issues
- Every team faces these

Key Points:
- Process issues compound
- Team issues multiply
- Documentation always lags
- Changes become risky

Questions/Engagement:
- "Which issues resonate most?"
- "How do you handle these now?"

Next:
- Introduce better approaches
-->

---
layout: center
hideInToc: true
---

# Why Infrastructure as Code?
When these goals sound familiar...

<div v-clicks class="mt-8 space-y-4">
  <div class="goal-item">
    <span class="text-blue-400">✓</span> Track changes clearly and fully
  </div>
  <div class="goal-item">
    <span class="text-blue-400">✓</span> Know who changed what and why
  </div>
  <div class="goal-item">
    <span class="text-blue-400">✓</span> Make differences between environments intentional
  </div>
  <div class="goal-item">
    <span class="text-blue-400">✓</span> Make deployments and rollbacks easier
  </div>
</div>

<div v-click class="mt-12 text-center text-xl bg-blue-500 bg-opacity-10 p-4 rounded">
  💡Sounds a bit like software development lifecycle?
</div>

<style>
.goal-item {
  @apply text-xl p-2 rounded bg-gray-100 bg-opacity-10;
}
</style>

<!--
# Speaker Notes

Quick transition:
- "These goals probably sound familiar..."
- Pause after each point to let it sink in
- End with the software connection to lead into IaC principles

Keep it light - this is just making the connection between their software experience and infrastructure needs, setting up for the deeper dive into IaC coming next.
-->

---
layout: two-cols-header
hideInToc: true
---

# Core IaC Principles
Infrastructure managed with the same rigor as application code

::left::

<div v-click class="principle-box">
  <div class="text-xl mb-2">Infrastructure as Software</div>
  <ul>
    <li>Version controlled</li>
    <li>Code reviews</li>
    <li>Reduced human error</li>
    <li>Testing enabled</li>
    <li>Clear history</li>
    <li>Team collaboration</li>
    <li>Automated deployment</li>
    <li>Validations</li>
  </ul>
</div>

::right::

<div v-click class="principle-box">
  <div class="text-xl mb-2"><span v-mark.underline>Declarative</span> Definitions</div>
  <ul>
    <li>Describe desired state</li>
    <li>System handles "how"</li>
    <li>Predictable results</li>
    <li>Dependency management</li>
    <li>Idempotency</li>
  </ul>
</div>


<style>
.principle-box {
  @apply p-4 rounded bg-gray-100 bg-opacity-10;
}
</style>

<!--
# Speaker Notes

Setup:
- Connect to their software practices
- Same rigor as application code
- Proven software principles

Key Points:
- Version control for infrastructure
- Automation removes human error
- Review process for changes

Questions/Engagement:
- "Which principle seems most valuable?"
- "What challenges do you see?"

Next:
- More principles to consider
-->

---
layout: two-cols-header
hideInToc: true
---

# IaC Tools Landscape
Different tools for different infrastructure needs

::left::

<div v-click class="tool-box">
  <div class="text-xl mb-2">General Purpose</div>
  <ul>
    <li><strong>Terraform</strong> - Multi-cloud</li>
    <li><strong>Pulumi</strong> - Multi-language</li>
    <li><strong>CloudFormation</strong> - AWS</li>
    <li><strong>ARM Templates</strong> - Azure</li>
  </ul>
</div>

::right::

<div v-click class="tool-box">
  <div class="text-xl mb-2">Specialized Tools</div>
  <ul>
    <li><strong>Ansible</strong> - Configuration</li>
    <li><strong>Chef</strong> - VM management</li>
    <li><strong>Kubernetes</strong> - Containers</li>
    <li><strong>Helm</strong> - Kubernetes packages</li>
  </ul>
</div>

<style>
.tool-box {
  @apply p-4 rounded bg-gray-100 bg-opacity-10;
}
</style>

<!--
# Speaker Notes

Setup:
- Many tools solve different problems
- No single perfect solution
- Choose based on needs

Key Points:
- General vs specialized
- Multi-cloud vs single cloud
- Configuration vs provisioning
- We'll focus on Pulumi because:
  * Real programming languages
  * Strong typing
  * Familiar development experience

Questions/Engagement:
- "Used any of these?"
- "Which would fit your needs?"
- "Seen them in internships/jobs?"

Next:
- Focus on development workflow
-->

---
layout: center
hideInToc: true
---

# The Development Workflow
From local development to deployment

<div class="workflow">
  <div v-click class="step">
    <div class="icon">👩‍💻</div>
    <div class="text">Local Development</div>
    <div class="code-box">
      main.cs
    </div>
  </div>

  <div v-click class="arrow">→</div>

  <div v-click class="step">
    <div class="icon">🔍</div>
    <div class="text">Preview Changes</div>
    <div class="detail">pulumi preview</div>
  </div>

  <div v-click class="arrow">→</div>

  <div v-click class="step">
    <div class="icon">📤</div>
    <div class="text">Create PR</div>
    <div class="detail">git push</div>
  </div>
</div>

<style>
.workflow {
  @apply flex items-center justify-center gap-8 mt-12;
}
.step {
  @apply flex flex-col items-center;
}
.icon {
  @apply text-4xl mb-4;
}
.text {
  @apply text-xl font-bold;
}
.detail {
  @apply text-sm opacity-75 mt-2;
}
.arrow {
  @apply text-2xl text-blue-400;
}
.code-box {
  @apply font-mono p-2 rounded bg-blue-300 bg-opacity-30 text-sm;
}
</style>

<!--
# Speaker Notes

Setup:
- Similar to app development
- Familiar git workflow
- Focus on safety

Key Points:
- Local development first
- Preview before pushing
- Standard PR process

Questions/Engagement:
- "Familiar workflow?"
- "What would you verify?"

Next:
- See team review process
-->

---
layout: center
hideInToc: true
---

# Team Review Process

<div class="workflow">
  <div v-click class="step">
    <div class="icon">👥</div>
    <div class="text">Team Review</div>
    <div class="detail">Code Review + Preview</div>
  </div>

  <div v-click class="arrow">→</div>

  <div v-click class="step">
    <div class="icon">🤖</div>
    <div class="text">CI Validation</div>
    <div class="detail">Tests & Security</div>
  </div>

  <div v-click class="arrow">→</div>

  <div v-click class="step">
    <div class="icon">🚀</div>
    <div class="text">Deploy</div>
    <div class="detail">pulumi up</div>
  </div>
</div>

<div v-click class="mt-12 text-center">
  <div class="text-xl mb-2">Just like your application code!</div>
  <div class="text-sm opacity-75">Same tools, same process, same confidence</div>
</div>

<style>
.workflow {
  @apply flex items-center justify-center gap-8 mt-12;
}
.step {
  @apply flex flex-col items-center;
}
.icon {
  @apply text-4xl mb-4;
}
.text {
  @apply text-xl font-bold;
}
.detail {
  @apply text-sm opacity-75 mt-2;
}
.arrow {
  @apply text-2xl text-blue-400;
}
</style>

<!--
# Speaker Notes

Setup:
- Infrastructure changes need review
- Same rigor as code review
- Team involvement important

Key Points:
- Multiple eyes on changes
- Automated validation
- Clear deployment process

Questions/Engagement:
- "How do you review changes now?"
- "What would you check?"

Demo teaser:
- "We'll see this in action soon"

Next:
- See this in practice
-->

---
layout: center
hideInToc: true
---

# Quick Questions

<div class="text-xl space-y-8">
  <div v-click class="question">
    When should your project start using IaC?
  </div>

  <div v-click class="question">
    Other examples of using declarative code?
  </div>
</div>

<style>
.question {
  @apply p-4 rounded bg-blue-500 bg-opacity-10 cursor-pointer hover:bg-opacity-20 transition-all;
}
</style>