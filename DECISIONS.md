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

While designing the look and feel of my page in Claude design, Claude kept trying to steer this project to read more like a personal advertisement for myself. I had given design my resume and details from my LinkedIn, which contains information about contracting work that I have done, so I think that Claude felt a personal advertisement was more in line with what I was going for. After several corrections I just had to specify verbatim what I wanted parts of the website to say.

---

## 4. How you know it works

What check did you run, and what did it tell you?

Then the real question: **what would have made this check fail?**
A check that could not have failed is not a check.

Link to your `verification/` folder.

I fetched the live URL directly with `curl -sv https://kyleremmenga.github.io/`
and confirmed a `200` response with the actual page HTML in the body, not just
a browser telling me it looked fine. I also took a browser screenshot of the
live URL with the address bar visible. Both are in [`verification/`](verification/):
`fetch.txt` (the raw curl output) and `screenshot.png`.

What would have made this fail: if the repo had been named anything other than
`kyleremmenga.github.io`, or if `index.html` had ended up nested in a subfolder
instead of the repo root, the fetch would have come back with a 404 instead of
the page — that's a check that could actually catch a real mistake, not one
that was guaranteed to pass.

---

## 5. What is still wrong

One thing on your own site that is not right, not finished, or that you do not
fully understand.

What would you do next, and how would you find out?

The site has a single responsive breakpoint at 860px — below it, the left rail
is supposed to collapse from a sticky sidebar into a static header with the
nav running horizontally. I wrote that CSS against the spec, but I haven't
actually opened the site on a phone or narrowed a browser window to check it.
I don't know if the nav wraps cleanly, whether the touch targets are big
enough, or whether anything overlaps at in-between widths. Next step is to
open the live site on my phone and in a resized desktop browser and see
where it breaks, then fix whatever doesn't hold up.
