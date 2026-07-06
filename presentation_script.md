# Building CTF Challenges with Claude & Claude Code
## Speaker Script for DefCon Talk (30-45 minutes)

---

## Slide 1: Title Slide
**[2 minutes]**

Good [morning/afternoon/evening] everyone! Today I'm going to share my experience building "The Hackers Challenge" - a complete CTF competition - using Claude and Claude Code. This is the story of how AI fundamentally changed my development workflow and what I learned along the way.

---

## Slide 2: The Origin Story
**[3-4 minutes]**

Let me start with how this all began. I was tasked with organizing "The Hackers Challenge" CTF event. The scope was ambitious:
- 15+ challenges across 4 different categories
- Only 4 weeks to build everything from scratch
- And my major blocker? Coding time.

I was honestly hesitant to take this on. But then someone named Pope gave me advice that changed everything: "Use LLMs for development assistance."

Here's the key insight that emerged from this experience: Previously, my bottleneck was writing code. With Claude, the bottleneck shifted to testing and validating AI output. This might sound like a small distinction, but it represents a fundamental shift in how development works. Instead of spending hours writing boilerplate and debugging syntax errors, I was spending that time thinking architecturally and validating solutions.

---

## Slide 3: The LLM Journey & Costs
**[4-5 minutes]**

Let me walk you through my journey with different LLMs, because I didn't start with Claude.

**Early Experiments (Early 2024):**
First, I tried a local LLM with Ollama. It didn't work out, though I should probably keep investigating this option. Then I tried Google Gemini - I just didn't like the results it was giving me.

**Discovery: Claude Free**
Then I discovered Claude Free. I gave it this prompt:

"I want to create a web version of the board game 'The Mind'. Players play cards 1-100 in ascending order without communication. Create Node.js backend with Socket.IO and React frontend."

I loved the results! But here's the catch - Claude Free doesn't include Claude Code access. So I was constantly copying and pasting code back and forth between the chat and my IDE.

**The Mistake:**
So I made a financial mistake - I bought a full year subscription instead of starting with monthly. If you're considering this, start with monthly to see if it works for your workflow.

**The Reality:**
But here's what actually happened: I spent one weekend - about 4 sessions of roughly 5 hours each - and completely coded SyncFlow, the multiplayer game challenge.

**Side note:** This isn't a sales pitch, but I will mention that Anthropic keeps releasing new models and adding features, which is genuinely exciting. I haven't really tried ChatGPT or Codex. I used Claude because many developers consider it the best coder, and I had previous work experience with it.

---

## Slide 4: How My Approach Changed
**[3-4 minutes]**

This slide really captures the transformation in my workflow.

**Before: Traditional Coding**
- Write every line myself
- Debug syntax errors
- Search Stack Overflow constantly
- Slow progress
- **Bottleneck: Writing code**

**After: Claude-Assisted Development**
- Describe what I want
- Claude generates the implementation
- I test and validate the results
- Iterate based on what I find
- **Bottleneck: Testing AI output**

I went from being a code writer to being a solution architect. My role shifted from "how do I implement this?" to "what exactly do I need, and is this implementation correct?"

---

## Slide 5: What I Built
**[3-4 minutes]**

So what did I actually build in those 4 weeks?

**SyncFlow - Multiplayer Game:**
A complete Node.js + Socket.IO + React application with AI bot timing algorithms

**GraphQL Challenges (8 total):**
Real-world vulnerabilities including introspection attacks, NoSQL injection, rate limiting bypasses, and authorization flaws

**Encoding Challenges (4 total):**
Creative challenges using QR codes, RGB ASCII art, DTMF tones, and Morse code in video

**CTFd Platform:**
Custom theme with dynamic scoring

**Infrastructure:**
Everything deployed in Docker containers, nginx reverse proxy, LetsEncrypt SSL automation, and Route 53 DNS management.

The result: 15+ challenges, all built with Claude assistance, in just 4 weeks.

---

## Slide 6: SyncFlow - The Multiplayer Challenge
**[4-5 minutes]**

Let me dive deeper into one specific challenge: SyncFlow.

**The Concept:**
It's inspired by "The Mind" board game. Players have to play cards numbered 1-100 in ascending order, but there's NO communication allowed between players. We implemented a single-player mode where you play against an AI bot. Flags are awarded at levels 4, 6, 8, and 10.

**The Twist:**
There are two dealing modes - random and predictable - which affects how solvable the challenge is.

**Bot AI Implementation:**
Here's where it gets interesting. The bot needed to feel realistic. The timing algorithm is:
```
delay = (cardValue - lastCardValue) * 1000ms

if (isLastPlayerWithCards) {
  delay = 250; // Quick finish
}
```

This makes the bot feel human - it "waits" longer for bigger jumps in card values.

**Real Conversation Example:**
When building this, I hit a bug at level 2. I told Claude: "I am creating a web game for the board game 'The Mind'... there is a bug when I reach the second level"

Claude immediately identified: "The problem is in the card-played event handler. There's a race condition during level transitions..."

This is the power of the tool - instant debugging assistance.

---

## Slide 7: GraphQL Challenges
**[4-5 minutes]**

I created 8 GraphQL challenges, all based on real vulnerabilities:
- Introspection attacks
- NoSQL injection via GraphQL
- Rate limiting bypass
- Authorization flaws
- Field suggestions exploitation
- Query depth attacks
- Batch query abuse
- Type confusion

**Example: The Introspection Challenge**
I told Claude: "Create a GraphQL challenge where users need to use introspection to discover hidden fields"

Claude responded: "I'll create a GraphQL server with a hidden admin field that's only discoverable through introspection queries..."

Then it generated code with the introspection query structure. All of these challenges are based on real-world GraphQL security issues that I've seen in production systems.

---

## Slide 8: Encoding Challenges - Matrix Theme
**[4-5 minutes]**

The encoding challenges were some of the most creative:

1. **QR Code:** Hidden in Matrix-style imagery
2. **RGB ASCII Art:** Flag encoded in the RGB color channels
3. **DTMF Tones:** Phone dial tones in an audio file
4. **Morse Video:** Flashing frames contain the morse message

**Morse Code Example:**
A participant sent me: "I have this encoded message with arrows: ↗↗↗↗ ↘↗↘↗ • ↘↘ ↘↘↘..."

Claude decoded it: "This is Morse code! Up-right arrows (↗) are dots, down-right arrows (↘) are dashes..."

The decoded message was: HC MORSESWEEPUPANDDOWN

There's even a meta-reference here - the arrows literally "sweep up and down" as mentioned in the flag itself!

---

## Slide 9: The Matrix Theme Pivot
**[3-4 minutes]**

So here's something that happened just days before the event. I decided to add a Matrix theme for visual cohesion across all challenges:
- Green-on-black terminals
- Falling characters aesthetic
- Movie references embedded in challenges
- Unified visual language

Claude helped generate CSS themes, Matrix rain animations, and consistent styling across all challenges.

**The Impact:**
This transformed what could have been a bunch of disjointed challenges into a cohesive experience. Participants really loved the aesthetic - it tied everything together and made the event memorable.

---

## Slide 10: CTFd Modifications
**[3-4 minutes]**

For the platform itself, I customized CTFd with:
- Matrix-inspired custom theme
- Dynamic scoring system
- Achievement system with hacker-themed names

**Challenge Names:**
I even used Claude for naming the achievement levels. I asked: "I need names for Level 1 (10 solves), Level 2 (16 solves), Level 3 (20 solves)"

Claude suggested: "Level 1: Script Kiddie, Level 2: Code Breaker, Level 3: Cyber Operative"

**Deployment:**
Everything was containerized. The docker-compose file defined the entire stack - CTFd platform, PostgreSQL, nginx, LetsEncrypt certbot, and all challenge containers. One command deployment.

---

## Slide 11: Claude Code Frustrations
**[4-5 minutes]**

Now let me be honest about the problems I encountered.

**Problem 1: Flag Leakage**
Claude would generate flags directly in source code like:
```
const FLAG = "HC{super_secret_flag}";
if (condition) return FLAG;
```

This is a security nightmare for a CTF! The solution: I had to explicitly instruct "store flags in environment variables, never in source code."

**Problem 2: Inadequate File Structure**
Without specific instructions, Claude wouldn't organize files logically. Everything ended up in one directory with no separation of concerns.

The solution: Provide explicit file structure requirements upfront in your prompts.

**Key Lessons:**
- Be explicit about security requirements
- Define file structure early
- Review generated code carefully
- Use environment variables for secrets
- Test in isolation first

**Bottom line:** Claude is a powerful assistant, but you're still the security architect. Don't blindly trust the output.

---

## Slide 12: The Missed Opportunity
**[3-4 minutes]**

Here's something I wish I had done: an agentic approach.

**The Vision:**
- Claude Agent 1 creates a CTF challenge
- Claude Agent 2 attempts to solve it
- Iterate and refine based on the solver's feedback

**Benefits:**
- Automatic difficulty validation
- Discover unintended solutions before participants do
- Faster iteration cycles
- More robust challenges

**Why I Didn't Do It:**
Honestly? Time constraints with the 4-week deadline, and I didn't think of it until after the event. It would have required building an orchestration layer.

But this could be a future project - building an agentic CTF challenge creation and testing system. If anyone here wants to collaborate on this, talk to me after!

---

## Slide 13: Key Lessons Learned
**[4-5 minutes]**

Let me summarize the key lessons from this experience:

**Development Workflow:**
1. **Start with Clear Requirements:** Detailed prompts lead to better results
2. **Iterate in Small Steps:** Test each component before moving on
3. **Be Security-Conscious:** Explicitly state security requirements
4. **Document as You Go:** Claude can help generate documentation too

**The Bottleneck Shift:**
Before: Writing code was the bottleneck
After: Testing and validating became the bottleneck

And honestly? This is actually a good problem to have! It means you're spending time on higher-level thinking rather than syntax.

**The Reality:**
- You're still the architect
- Claude accelerates implementation
- Quality depends on your prompts
- Testing is still your job
- Security review is critical

Don't treat this as autopilot. Treat it as a force multiplier.

---

## Slide 14: Questions?
**[Remaining time for Q&A]**

Thank you all for listening! 

**Resources:**
- GitHub: [your-repo-link]
- Claude AI: claude.ai  
- Claude Code: Anthropic's agentic coding tool

I'm happy to take questions about any part of the process - the challenges themselves, working with Claude, the deployment infrastructure, or anything else.

**Final thought:** This experience showed me we're moving from coding being a blocker to coding being an enabler. The future of development is less about writing every line of code and more about architecting solutions and validating implementations.

---

## Q&A Session Notes

**Common Questions to Prepare For:**

1. **"How accurate was Claude's code?"**
   - Generally high quality, but required testing and iteration
   - Security aspects needed manual review
   - Infrastructure code was particularly good

2. **"Would you use this approach again?"**
   - Absolutely, but with the lessons learned applied upfront
   - More explicit security requirements from the start
   - Better file structure specifications

3. **"What about other LLMs?"**
   - Haven't extensively tested ChatGPT/Codex
   - Claude worked for my use case
   - Recommend trying different options for your specific needs

4. **"Cost analysis?"**
   - Full year subscription (~$200)
   - For 4 weeks of intensive use
   - ROI was positive given the time saved

5. **"Can you share the challenges?"**
   - [Provide GitHub link]
   - All Dockerized and documented
   - Feel free to use them for your own events

---

## Timing Breakdown
- Slide 1: 2 min
- Slide 2: 3-4 min
- Slide 3: 4-5 min
- Slide 4: 3-4 min
- Slide 5: 3-4 min
- Slide 6: 4-5 min
- Slide 7: 4-5 min
- Slide 8: 4-5 min
- Slide 9: 3-4 min
- Slide 10: 3-4 min
- Slide 11: 4-5 min
- Slide 12: 3-4 min
- Slide 13: 4-5 min
- Slide 14: 1 min + Q&A

**Total Presentation: 30-35 minutes**
**Q&A: 10-15 minutes**
**Total: 40-50 minutes**
