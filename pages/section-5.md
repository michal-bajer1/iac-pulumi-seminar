---
layout: section
class: text-center
---

# Benefits and drawbacks

<div class="opacity-80 italic mb-4">
Key takeaways from demo 
</div>

---
layout: two-cols-header
hideInToc: true
---

# Preview Limitations
Understanding what preview can and cannot catch

::left::

<div v-click class="preview-box">
  <div class="text-xl mb-2">✅ What Preview Shows</div>
  <ul class="text-sm">
    <li>Resource additions/removals</li>
    <li>Property changes</li>
    <li>Basic validation</li>
    <li>Dependencies</li>
  </ul>
</div>

::right::

<div v-click class="preview-box">
  <div class="text-xl mb-2">⚠️ What Preview Misses</div>
  <ul class="text-sm">
    <li>API-specific rules</li>
    <li>Some validation rules</li>
    <li>Runtime conditions</li>
    <li>External dependencies</li>
  </ul>
</div>

<div v-click class="mt-8 mx-4 p-4 rounded bg-blue-500 bg-opacity-10">
  <div class="text-center font-bold">Best Practice</div>
  <div class="text-sm text-center mt-2">
    Always test changes in development environment first
  </div>
</div>

<style>
.preview-box {
  @apply p-4 rounded bg-gray-100 bg-opacity-10;
}
</style>

<!--
# Speaker Notes

Setup:
- Preview is powerful but limited
- Understanding boundaries
- Real-world experience

Key Points:
- Shows structural changes
- Misses runtime validation
- Test in dev first

Questions/Engagement:
- "Where might preview fail?"
- "How to handle limitations?"

Next:
- Team processes
-->

---
layout: center
hideInToc: true
---

# Team Workflow
Collaborative infrastructure management

```mermaid {scale: 0.8}
flowchart LR
    A[Branch] --> B[Changes]
    B --> C[Preview]
    C --> D[PR]
    subgraph Review
        D --> E[Code Review]
        E --> F[Plan Review]
    end
    Review --> G[Merge]
    G --> H[Deploy]
```

<div class="grid grid-cols-2 gap-8 mt-8">
  <div v-click class="review-point">
    <div class="text-xl mb-2">👥 Review Points</div>
    <ul class="text-sm">
      <li>Code quality</li>
      <li>Security checks</li>
      <li>Cost impact</li>
      <li>Best practices</li>
    </ul>
  </div>

  <div v-click class="review-point">
    <div class="text-xl mb-2">🔍 Validation</div>
    <ul class="text-sm">
      <li>Automated tests</li>
      <li>Policy checks</li>
      <li>Preview results</li>
      <li>Change scope</li>
    </ul>
  </div>
</div>

<style>
.review-point {
  @apply p-4 rounded bg-gray-100 bg-opacity-10;
}
</style>

<!--
# Speaker Notes

Setup:
- Standard PR process
- Multiple checkpoints
- Team collaboration

Key Points:
- Code review first
- Plan verification
- Automated checks

Questions/Engagement:
- "Similar to your workflow?"
- "What would you check?"

Next:
- Benefits and challenges
-->

---
layout: two-cols-header
hideInToc: true
---

# Benefits & Challenges
Making the transition to Infrastructure as Code

::left::

<div class="space-y-4">
  <div v-click class="benefit">
    <div class="text-xl mb-2">🎯 Benefits</div>
    <ul class="text-sm">
      <li>Version Control</li>
      <li>Familiar Dev Experience</li>
      <li>Repeatability</li>
      <li>Self-Documenting</li>
      <li>Team Collaboration</li>
    </ul>
  </div>
</div>

::right::

<div class="space-y-4">
  <div v-click class="challenge">
    <div class="text-xl mb-2">💪 Challenges</div>
    <ul class="text-sm">
      <li>Learning Curve</li>
      <li>Initial Setup</li>
      <li>Team Adoption</li>
      <li>State Management</li>
      <li>Integration of existing resources</li>
    </ul>
  </div>
</div>

<style>
.benefit {
  @apply p-4 rounded bg-green-500 bg-opacity-10;
}
.challenge {
  @apply p-4 rounded bg-orange-500 bg-opacity-10;
}
</style>

<!--
# Speaker Notes

Start with benefits:
- Each one connects to their dev experience
- Give quick examples for each
- Point out long-term gains

Then challenges:
- Be honest about difficulties
- Not appripriate at every scale
- But show they're manageable
- Most are one-time costs
- Common to all new tech adoption

Key message:
"Benefits compound over time, challenges decrease"

Ask:
"Which benefit interests you most?"
"Which challenge concerns you?"
-->

<!--
# Speaker Notes

Setup:
- Realistic assessment
- Both sides matter
- Trade-offs exist

Key Points:
- Benefits compound
- Challenges decrease
- Team impact

Challenges:
- Talk about difficulties
- Not appripriate at every scale
- Most are one-time costs
- Common to all new tech adoption

Questions/Engagement:
- "Which benefit matters most?"
- "Which challenge concerns you?"

Next:
- Language advantages
-->

---
layout: two-cols-header
hideInToc: true
---

# Language Benefits
Using C# for Infrastructure Management

::left::

<div class="space-y-4">
  <div v-click class="benefit">
    <div class="text-xl mb-2">🛠️ Development Features</div>
    <ul class="text-sm">
      <li>Strong Type System</li>
      <li>IDE Support</li>
      <li>Refactoring Tools</li>
      <li>Package Ecosystem</li>
      <li>Testing Framework?</li>
    </ul>
  </div>
</div>

::right::

<div class="space-y-4">
  <div v-click class="benefit">
    <div class="text-xl mb-2">📚 Code Organization</div>
    <ul class="text-sm">
      <li>Classes and Inheritance</li>
      <li>Error Handling</li>
      <li>Documentation Comments</li>
      <li>Code Sharing</li>
      <li>Team Collaboration</li>
    </ul>
  </div>
</div>

<style>
.benefit {
  @apply p-4 rounded bg-green-500 bg-opacity-10;
}
</style>

<!--
# Speaker Notes

Setup:
- C# advantages
- Developer experience
- Team productivity

Key Points:
- Strong typing helps
- IDE support
- Code organization

Questions/Engagement:
- "Using these features now?"
- "Which help most?"

Next:
- Platform building
-->