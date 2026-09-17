# Decision log

Your methods section. About one page total.

Answer these as you go, not the night before it is due.
Specifics beat polish - a short honest answer is worth more than a long vague one.

Delete these instructions when you are done, or leave them. It does not matter.

---

## 1. What did you set out to build, and what changed?

What you wanted at the start, and what is actually live now.
Name one thing you dropped or added along the way, and why.

I set out to build a site that holds personal information about me — work history,
projects, education, how to reach me — not a pitch. What's live now matches that:
a plain five-page site (Home, Work, Projects, About, Contact) with no marketing
language and no calls to action. The clearest thing I dropped, deliberately, was
any framing of myself as available for hire or contract work — see question 3.

---

## 2. A fork in the road

Name one real choice where you could have gone two ways.
Plain HTML or a framework. One page or several. Your own CSS or someone's template.
What goes on the front page and what does not.

Say which you picked, what the alternative was, and what you gave up by not taking it.

"There was no alternative" is not an answer. Find the fork.

The design handoff came from a prototype built in a component runtime — a
single JS-driven page with a page switcher rather than real navigation. I could
have kept that structure and shipped one HTML file with JavaScript swapping the
visible section, or converted it into a real static multi-page site: separate
`index.html`, `work.html`, `projects.html`, `about.html`, and `contact.html`,
linked with ordinary `<a href>` navigation and no JS at all. I picked the
static multi-page version. The JS approach would have been closer to a
1:1 port of the prototype and slightly less work up front, but it meant the
site depended on JavaScript to be navigable at all, and it doesn't match what
GitHub Pages is actually good at serving. Going static costs a small amount of
duplication across the five files (the rail markup is repeated in each) but
means every page works with JS off, has its own URL, and needed no build step.

---

## 3. Where you overruled the agent

One time Claude suggested, wrote, or claimed something and you did not take it.

What did it do? How did you notice? What did you do instead?

If it genuinely never happened, say so plainly, and then say what you would have had to
check in order to notice. Being honest here costs you far less than a story you cannot
defend when you record your video.

While putting together the design in Claude, the agent kept steering the copy and
layout toward something that read like an ad for my contracting availability —
pitch-style language, a "hire me" framing. I didn't want that; this is meant to
be a personal page, not a sales page. I overruled it and had it rewrite the
content in a plainer, more understated voice with no marketing language and no
calls to action, which is what the handoff spec and the final site both reflect.

---

## 4. How you know it works

What check did you run, and what did it tell you?

Then the real question: **what would have made this check fail?**
A check that could not have failed is not a check.

Link to your `verification/` folder.

*Your answer here.*

---

## 5. What is still wrong

One thing on your own site that is not right, not finished, or that you do not
fully understand.

What would you do next, and how would you find out?

*Your answer here.*
