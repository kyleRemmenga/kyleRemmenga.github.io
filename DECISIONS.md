# Decision log

Your methods section. About one page total.

Answer these as you go, not the night before it is due.
Specifics beat polish - a short honest answer is worth more than a long vague one.

Delete these instructions when you are done, or leave them. It does not matter.

---

## 1. What did you set out to build, and what changed?

What you wanted at the start, and what is actually live now.
Name one thing you dropped or added along the way, and why.

I wanted a site that holds my information. Work history, projects, education, and a way to get in touch. That is what is live now, five pages (Home, Work, Projects, About, Contact) with no marketing language or calls to action anywhere on them. The thing I dropped was any wording that made it sound like I was advertising myself for hire or for contract work, which I get into more in question 3.

---

## 2. A fork in the road

Name one real choice where you could have gone two ways.
Plain HTML or a framework. One page or several. Your own CSS or someone's template.
What goes on the front page and what does not.

Say which you picked, what the alternative was, and what you gave up by not taking it.

"There was no alternative" is not an answer. Find the fork.

The design I started from was a prototype built in a component runtime, so it was really one JS driven page with a switcher on it instead of actual navigation. I could have kept that and shipped a single HTML file with JavaScript hiding and showing whichever section you clicked, or I could split it into a real static site with a separate file for each page and normal links between them. I went with the static files. Keeping the JS would have been closer to a straight port of the prototype and probably a bit less work up front, but then the site needs JavaScript running just to get from one page to another, and that is not really what GitHub Pages is good at anyway. The tradeoff is that the left rail markup is copied into all five files, so changing the nav means changing it in five places. What I get for that is every page having its own URL and still working with JS turned off.

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

I hit the live URL with `curl -sv https://kyleremmenga.github.io/` and got a 200 back with the actual page HTML in the body. I used curl instead of just opening it in a browser so that I was looking at the real response and not at something a browser had already cached and rendered for me. I did also take a screenshot of the live site with the address bar showing. Both of those are in the [verification](verification/) folder, fetch.txt is the curl output and screenshot.png is the screenshot.

This one could have failed. If I had named the repo anything other than kyleremmenga.github.io, or if index.html had ended up sitting in a subfolder instead of at the root of the repo, the fetch would have come back 404 and I would have known something was wrong.

---

## 5. What is still wrong

One thing on your own site that is not right, not finished, or that you do not
fully understand.

What would you do next, and how would you find out?

There is one breakpoint in the CSS at 860px, and under that width the left rail is supposed to stop being a sticky sidebar and become a header with the nav running across the top. I wrote that CSS off the spec and then never checked it. I have not opened the site on a phone or dragged a browser window down to see what happens. So I do not know if the nav wraps the way I think it does, or if the links are big enough to actually tap, or if things overlap at the widths in between. To find out I would pull the live site up on my phone and resize a desktop window until something breaks, then go fix whatever broke.
