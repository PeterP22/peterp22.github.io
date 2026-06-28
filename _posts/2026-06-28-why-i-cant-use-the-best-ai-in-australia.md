---
title: "Why I can't use the best AI in Australia"
date: 2026-06-28
---

I read a cool article on the 28th of June 2026 about how a company called Baseten managed to hit 280+ tokens per second on GLM-5.2, an open-source Chinese LLM.

The significance of this is that it's a 744 billion parameter model, MIT licensed, with what I believe is a 1 million plus token context window. And if you benchmark it, it looks like it matches GPT 5.5, which is the best current version we're allowed to use. America has kept GPT 5.6 for now, so it's only allowed to be used by essentially the Feds and 100 selected companies within America. For me, being in Australia right now, that doesn't work. It's about a similar level to Opus 4.8, maybe a few percent below, at roughly 70 to 80% cheaper. If I distil it into simple words: it's a smart, cheap model that's open source.

We're at a turning point now. You've got these very large enterprise companies like OpenAI and Anthropic, and they have access to the best closed-source AI models. They're not releasing them to the public anymore, because it's a security threat, or they're far too capable and will cause disruption in the workforce. The only way around this now would be to have your own hardware to run these types of things. You've got Mac Studios, you've got the new AMD Ryzen AI Halo with 128GB of unified memory, which can literally run up to 200 billion parameter LLMs.

Just a bit of backstory: Baseten, the company I'm referencing, is focused on AI infrastructure. Their whole value prop is that they provide specialised software and computing capacity to help companies run machine learning models and generative AI in production. When it comes to the whole forward-deployed engineering model, it lets developers deploy, scale, and optimise AI models quickly, reliably, and cost-efficiently.

With open-source models, that might be a requirement for some companies. They don't want to send their data to a closed-source model where they can't see anything behind the scenes, so they might go this route. If it's just as capable but far cheaper and just as fast, and you could potentially even run it on your own hardware, which would make Baseten essentially obsolete, then that's the kind of direction we're heading in.

So in essence, it's an inference platform. Obviously, just having an AI model that's smart and cheap isn't enough anymore. To be useful in production, it has to be fast, it has to be reliable, and it has to be available at scale. That means many users hitting that model at the same time. There has to be a solution to that under the hood. A model working in a demo for one person is quite the contrast to a model working in production. Let's say you're a big bank serving hundreds of thousands of customers.

Now, I don't want to get too technical as far as how they did this, but one thing that stood out to me was the quantization. Essentially, they shrink the model's numbers from FP8 down to 4 bits, so it runs faster and uses less memory.

I was doing some coding over the weekend and came across a library called pngquant.org. It's a good analogy, because pngquant is literally quantization. In this case it takes an image with millions of possible colours (24-bit) and squeezes it down to a smaller palette, for example 256 colours, which is 8-bit. So let's say you've got a 10MB file. You can reduce it by 70%, and to the human eye it looks essentially identical.

One of the other tricks they used was to double their throughput. What they did here was increase the number of GPUs they use for the LLM inference. They'd put one GPU on the input part, essentially whatever you're giving the AI model, the pre-fill. Then the output, as in the AI writing the answer, gets its own GPU assigned. So now you've got two separate machines that can each be tuned for their own job. That's why they can get the tokens per second up to that level.
