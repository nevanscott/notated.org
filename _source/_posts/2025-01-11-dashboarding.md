---
title: Dashboarding
date: 2025-01-11T04:31:00+01:00
---
One of my goals for this year is to get a better handle on the financial picture of the business at [Button School](https://buttonschool.com), so this week, I've been working with some spreadsheets and trying to figure out ways to understand and visualize the data better for myself.

I have transaction records for course sales in Airtable and Stripe, as well as bank records, all of which I can download as CSV documents.

At first I tried messing around with the data as spreadsheets, which meant trying to piece back together how pivot tables work, and lots of trial and error with the chart generation settings in Sheets and Numbers. I was able to get some workable charts breaking down revenue by month, for example, but I could really only reasonably do this for one source of records at a time, and started running up against a wall when I wanted to combine data sources and do more advanced filtering.

I had another problem: how many steps was I going to have to either write down or remember to perform in order to get from the raw data to a usable visualization?

This seemed like a situation that called for firing up my text editor and writing some code. But how to start?

This is the point where I often get a bit stuck trying to decide how to proceed, thinking about what would be the best way to build something like this. I tend to prefer light-weight solutions that will be easy to maintain over time, but that I also won't mind throwing away and starting over from scratch. (For various reasons, I also tend to shy away from low- and no-code solutions, since—well—how is that going to be expressive and precise enough?)

In this case, luckily I remembered that the team at [Observable](https://observablehq.com) had somewhat recently released [Observable Framework](https://observablehq.com/framework/), an open source static site generator that seemed like it should give me a lot of what I might otherwise look for from something like a [Jupyter notebook](https://jupyter.org), but with the benefit of allowing me to work in JavaScript (which I'm more comfortable with than Python) and first-class support for [D3](https://d3js.org) (which produces visualizations friendlier to my soft-hearted designer sensibilities).

I fired up a new project locally with some suggested examples to start, looked through what was there, and then... crickets.

Reading through the docs and looking at the examples, I could see that there were some nice ways to import data from a local CSV file to work with, but being unfamiliar with the idioms and libraries available[^protovis], I found myself playing a bit of whack-a-mole guessing at what did what.

It's 2024, and I decided to try turning to an LLM[^llm]. After giving the LLM some context about what I was attempting to do, and some back and forth sharing code snippets that I knew were working, as well as some intended example inputs and outputs, I managed to cobble things together.

Based on this experience, I have a few observations:

- Using an LLM for coding assistance strikes me as the most useful use case I have personally tested for these tools.
- In this case, I knew what I was trying to do, could help break things down into smaller tasks, and critically analyze the suggestions the LLM made for me.
- In addition to saving me time writing boilerplate code, this process filled in a gap between my higher-level understanding of what needed to be built, and concrete information I didn't have at my fingertips about how these particular libraries worked.
- When something wasn't working as I expected it to, I found I could give an explanation of what had gone wrong to the LLM, and it was capable of making a good guess about where the problem may have been with suggestions for possible solutions.
- This particular LLM seems to have been trained on examples containing, and given explicit instruction to include a fairly significant amount of inline comments in the code it generates. I found this super helpful as I assessed its suggestions, and also to be better-documented than what I would have likely created for a prototype like this on my own.

I think after this experience I can see more clearly why developers seem to be the most optimistic about the possibilities of LLM technology. That said, I am even more convinced that prompting an LLM to do something that you don't know how to do yourself would likely result in a maddeningly confusing outcome with much less chance of success.

It may be a bit trite, but I hold to the point of view that technology, and especially computing technology, should augment, not substitute, human thought. I'm curious to see if the development and use of LLMs moves more in this direction.

But I'm not holding my breath.

*[CSV]: Comma-separated values

*[LLM]: Large language model

[^protovis]: I haven't used D3 professionally since I worked with its predecessor, [Protovis](http://mbostock.github.io/protovis/), more than a decade ago.

[^llm]: I am deeply skeptical of the hype around these technologies, and concerned about their usage for all sorts of reasons, including their impact on labor and the environment—not to mention the speculative economic bubble surrounding them that so smacks of the height of blockchain boosterism, and the questionable legality of hoovering up a bunch of human-created content without permission to feed these machines "data". However, as a teacher I am very aware that my students make use of them within their studies as well as their work, and I would feel remiss if I didn't try to understand how they may be useful. If nothing else, if or when I field questions about them, I would prefer my criticisms to be grounded in some practical first-hand experience. If you have made or would make a different choice about this than I have, I certainly don't blame you.
