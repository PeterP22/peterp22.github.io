---
title: "Turning video into a database"
date: 2026-07-04
---

I came across TwelveLabs this week. They just raised $100 million to build what they're calling video superintelligence, and the pitch caught my attention: roughly 80% of the world's data is video, and almost none of it is searchable. Text got its database decades ago. Video never did. You can't grep a screen recording.

So I signed up and spent a session actually testing it, not just reading the landing page.

## What they've built

Two models do the work. Marengo turns video into something you can search: it processes the visuals, the audio, the speech, and any text on screen all at once, so you can ask for a moment in plain English and get exact timestamps back. Pegasus goes the other way and turns video into text: summaries, chapters, and open-ended questions against the footage.

The bit I found genuinely clever is their framing. Marengo gives machines coordinates, Pegasus gives machines descriptions. Index enough footage and you've basically got a knowledge store that compounds, the more you put in, the more useful every query gets.

![The TwelveLabs pipeline: video sources flow through a CLI into either an indexed library (Marengo search, Pegasus analysis) or direct one-shot analysis with Pegasus 1.5](/assets/img/twelvelabs-pipeline.svg)

## What I built

Rather than clicking around their playground, I built a small Python CLI that covers the whole loop: create an index, upload a video, search it, summarise it, ask it questions. It's public at [github.com/PeterP22/twelvelabs-playground](https://github.com/PeterP22/twelvelabs-playground) if you want to try it yourself. The free tier gives you 10 hours of indexing with no credit card, which is plenty to form an opinion.

## The test

First video in: [How To Become Cracked at Programming](https://www.youtube.com/watch?v=vyNqvjOdTi0) by bigboxSWE. 4 minutes 37 seconds, downloaded with yt-dlp because TwelveLabs needs an actual file, not a YouTube link. Indexing took about 2 minutes.

Then I started querying it, and this is where it got interesting.

Searching "balatro gameplay footage" ranked the Game of the Year nomination scene first. But the third hit was the one that sold me: a clip whose transcript is literally just the word "seconds". There's nothing in the spoken audio to match on. The model matched on what was visible on screen. A transcript tool has no answer to that.

Chapter generation gave me a clean nine chapter breakdown with timestamps and titles. And when I asked it an open-ended question ("list every concrete piece of advice with timestamps, and describe the visual style"), it pulled out all the advice, described the editing style, and correctly identified the sponsor segment, right down to the discount code shown on screen.

Sample of the chapter output:

```
[0s - 31s]   The Essence of Obsession in Programming
[31s - 61s]  Balatro: A Solo Developer's Masterpiece
[61s - 91s]  The Meditative Art of Game Development
...6 more chapters, all accurate
```

## The rough edges

Worth being honest about this part. Their platform has moved fast this year and the docs haven't kept up. I hit three breaks in one session: a helper method that no longer exists in the new SDK, a search response schema that changed with Marengo 3.0, and a summarise endpoint that got deprecated in January and now returns a 410. All three were fixable in minutes, but if you're evaluating this for production, budget for API drift.

## Where I'd take it

The whole session cost about 5 of my 600 free minutes. The obvious next step is the library play: index a stack of videos and search across all of them at once, which is where the compounding value should show up. I've got a few personal use cases queued: finding the strongest 30 second moments in long screen recordings for short-form content, chaptering technical talks, and a workout form check, because why not.

Video's been the one data type we could store but not query. That's changing. Worth a weekend.
