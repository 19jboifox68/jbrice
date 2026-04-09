# Experience Section Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Add a vertical timeline "Experience" section between the About and Services sections, displaying 4 professional roles from the resume.

**Architecture:** All changes are in `index.html`. Task 1 adds CSS styles inside the existing `<style>` block. Task 2 inserts the section HTML between `#about` and `#services`. No new files needed.

**Tech Stack:** Plain HTML, CSS, Tailwind CDN (utility classes), existing `reveal` scroll-animation system already in `index.html`.

---

### Task 1: Add timeline CSS styles

**Files:**
- Modify: `index.html` — inside the `<style>` block, after the `.about-photo` styles (around line 497)

- [ ] **Step 1: Find the insertion point**

In `index.html`, locate this comment block (around line 450):
```css
/* ── About photo ── */
```
Insert the new CSS **before** this comment (keep photo styles grouped). The exact anchor to insert before is:
```css
    /* ── About photo ── */
```

- [ ] **Step 2: Insert the timeline CSS**

Add the following block immediately before `/* ── About photo ── */`:

```css
    /* ── Experience Timeline ── */
    .timeline {
      position: relative;
      padding-left: 32px;
    }
    .timeline::before {
      content: '';
      position: absolute;
      left: 0;
      top: 8px;
      bottom: 0;
      width: 2px;
      background: rgba(212,212,212,0.15);
    }
    .timeline-entry {
      position: relative;
      padding-bottom: 40px;
    }
    .timeline-entry:last-child {
      padding-bottom: 0;
    }
    .timeline-dot {
      position: absolute;
      left: -37px;
      top: 6px;
      width: 10px;
      height: 10px;
      background: var(--accent);
      border-radius: 50%;
      box-shadow: 0 0 8px rgba(212,212,212,0.4);
    }

```

- [ ] **Step 3: Verify CSS was inserted correctly**

Search `index.html` for `.timeline-dot` — it should appear once inside the `<style>` block.

---

### Task 2: Insert the Experience section HTML

**Files:**
- Modify: `index.html:1377–1378` — insert between closing `</section>` of `#about` and the `#services` comment block

- [ ] **Step 1: Find the insertion point**

In `index.html`, locate this exact block (around line 1377):
```html
  </section>

  <!-- ══════════════════════════════════════
       SERVICES — WHAT I BUILD
  ══════════════════════════════════════ -->
```

- [ ] **Step 2: Insert the Experience section HTML**

Replace the above block with:

```html
  </section>

  <!-- ══════════════════════════════════════
       EXPERIENCE
  ══════════════════════════════════════ -->
  <section id="experience" class="py-28">
    <div class="max-w-7xl mx-auto px-6">
      <div class="mb-16 max-w-xl">
        <p class="section-label reveal">Experience</p>
        <h2 class="section-heading reveal reveal-delay-1 mb-4 split-heading">
          The work that<br/>
          <span class="text-accent">built the expertise.</span>
        </h2>
      </div>

      <div class="timeline max-w-3xl">

        <!-- Entry 1 -->
        <div class="timeline-entry reveal">
          <div class="timeline-dot"></div>
          <div class="mb-1">
            <span style="color:var(--text);font-weight:600;font-size:1rem;letter-spacing:-0.02em;">AI Automation Specialist (Freelance)</span>
          </div>
          <div class="flex justify-between items-baseline mb-3" style="font-size:0.875rem;">
            <span style="color:var(--accent);font-weight:400;">Self-Employed</span>
            <span style="color:var(--text-muted);font-weight:400;">Jan 2026 – Present</span>
          </div>
          <ul style="color:var(--text-muted);font-weight:300;line-height:1.75;font-size:0.9rem;list-style:none;padding:0;display:flex;flex-direction:column;gap:6px;">
            <li style="padding-left:1rem;position:relative;"><span style="position:absolute;left:0;color:var(--accent);">–</span>Design and deploy multi-step automation workflows across n8n, Make.com, and Zapier for clients in sales ops, content, and customer support</li>
            <li style="padding-left:1rem;position:relative;"><span style="position:absolute;left:0;color:var(--accent);">–</span>Build webhook-triggered pipelines integrating CRMs, Google Workspace, Slack, and AI APIs (OpenAI, OpenRouter, Gemini)</li>
            <li style="padding-left:1rem;position:relative;"><span style="position:absolute;left:0;color:var(--accent);">–</span>Implement JavaScript code nodes for data transformation, error handling, and conditional routing logic</li>
            <li style="padding-left:1rem;position:relative;"><span style="position:absolute;left:0;color:var(--accent);">–</span>Built and deployed 10+ automation workflows as portfolio projects spanning sales ops, content pipelines, and customer support use cases</li>
          </ul>
        </div>

        <!-- Entry 2 -->
        <div class="timeline-entry reveal reveal-delay-1">
          <div class="timeline-dot"></div>
          <div class="mb-1">
            <span style="color:var(--text);font-weight:600;font-size:1rem;letter-spacing:-0.02em;">Senior Project Expert</span>
          </div>
          <div class="flex justify-between items-baseline mb-3" style="font-size:0.875rem;">
            <span style="color:var(--accent);font-weight:400;">Cognizant</span>
            <span style="color:var(--text-muted);font-weight:400;">Jul 2020 – Jan 2026</span>
          </div>
          <ul style="color:var(--text-muted);font-weight:300;line-height:1.75;font-size:0.9rem;list-style:none;padding:0;display:flex;flex-direction:column;gap:6px;">
            <li style="padding-left:1rem;position:relative;"><span style="position:absolute;left:0;color:var(--accent);">–</span>Managed complex client account operations; identified repetitive manual workflows and built internal process documentation to support future automation</li>
            <li style="padding-left:1rem;position:relative;"><span style="position:absolute;left:0;color:var(--accent);">–</span>Gained deep exposure to CRM workflows, ticket routing logic, and SLA-driven escalation patterns — directly informing current automation design work</li>
          </ul>
        </div>

        <!-- Entry 3 -->
        <div class="timeline-entry reveal reveal-delay-2">
          <div class="timeline-dot"></div>
          <div class="mb-1">
            <span style="color:var(--text);font-weight:600;font-size:1rem;letter-spacing:-0.02em;">Engagement Specialist</span>
          </div>
          <div class="flex justify-between items-baseline mb-3" style="font-size:0.875rem;">
            <span style="color:var(--accent);font-weight:400;">Synchrony Financial</span>
            <span style="color:var(--text-muted);font-weight:400;">Apr 2019 – Oct 2019</span>
          </div>
          <ul style="color:var(--text-muted);font-weight:300;line-height:1.75;font-size:0.9rem;list-style:none;padding:0;display:flex;flex-direction:column;gap:6px;">
            <li style="padding-left:1rem;position:relative;"><span style="position:absolute;left:0;color:var(--accent);">–</span>Handled billing inquiries and account issue resolution; recognized patterns in manual back-office processes ripe for automation</li>
          </ul>
        </div>

        <!-- Entry 4 -->
        <div class="timeline-entry reveal reveal-delay-3">
          <div class="timeline-dot"></div>
          <div class="mb-1">
            <span style="color:var(--text);font-weight:600;font-size:1rem;letter-spacing:-0.02em;">Earlier Roles</span>
          </div>
          <div class="flex justify-between items-baseline mb-3" style="font-size:0.875rem;">
            <span style="color:var(--accent);font-weight:400;">Contact Solutions · Collabera · Wipro</span>
            <span style="color:var(--text-muted);font-weight:400;">Oct 2015 – Feb 2019</span>
          </div>
          <ul style="color:var(--text-muted);font-weight:300;line-height:1.75;font-size:0.9rem;list-style:none;padding:0;display:flex;flex-direction:column;gap:6px;">
            <li style="padding-left:1rem;position:relative;"><span style="position:absolute;left:0;color:var(--accent);">–</span>Customer service and lead generation across inbound and outbound programs; built strong communication and process documentation skills</li>
          </ul>
        </div>

      </div>
    </div>
  </section>

  <!-- ══════════════════════════════════════
       SERVICES — WHAT I BUILD
  ══════════════════════════════════════ -->
```

- [ ] **Step 3: Verify section was inserted correctly**

Search `index.html` for `id="experience"` — it should appear once. Also confirm `id="services"` still exists after it.

- [ ] **Step 4: Open in browser and verify visually**

Open `index.html` in a browser and confirm:
- Scrolling past About reveals the Experience section
- Timeline vertical line and silver dots render
- All 4 entries show correct role, company, dates, and bullets
- Company names are silver, dates are muted, role titles are white
- Scroll-reveal animations trigger on scroll

- [ ] **Step 5: Commit**

```bash
git add index.html
git commit -m "feat: add experience timeline section between about and services"
```
