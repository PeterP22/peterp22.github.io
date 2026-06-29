---
title: "What if they just switch it off?"
date: 2026-06-29
---

Something shifted this past week, and I don't think enough people clocked it.

Anthropic pulled access to Fable 5, which is the guardrail version of their Mythos 5 model. Then they pulled Mythos 5 too. Both gone, for everyone, after a US government export control directive on the 12th of June. A few days later OpenAI previewed GPT-5.6, their new Sol model (along with Terra and Luna), and immediately limited it to a small group of trusted US partners, again at the government's request. OpenAI even said the restrictions shouldn't be the norm, which tells you they weren't thrilled about it either.

So in the space of about two weeks, the two best labs in the world released their most capable models and then locked most of us out of them.

For context on how good these are: on TerminalBench 2.1, which throws real terminal engineering tasks at the models, GPT-5.6 Sol scored 88.8%, and 91.9% in its Ultra mode. That edges out Claude Mythos 5 at 88.0%. Opus 4.8, the one I can actually use, sits at 78.9%. So the gap between what's gated and what's public is real, and it's widening.

Here's what worries me. If access can be revoked at the government's request, what happens if they decide to revoke it for everyone? Not foreign nationals, not a list of partners, everyone. You'd have a small group of people and companies with frontier intelligence, and everyone else stuck a tier or two below. That's a permanent underclass, and I don't want to be in it.

The way out is being able to run powerful models on your own hardware. This is why open source matters so much right now. A model like GLM 5.2 is open, MIT licensed, and roughly Opus 4.8 level. Nobody can switch that off. Once the weights are out, they're out. If you've got the hardware to run it, you're not asking anyone for permission.

Which brings up the question everyone actually has: which computer do you buy? Alex Finn did a good breakdown of this, and it basically comes down to three options.

![Local AI: three hardware options on a spectrum from intelligence to speed](/assets/img/local-ai-3-options.svg)

Mac Studio: huge memory, so it runs massive models, but low bandwidth means it's slow. Good if you want frontier intelligence running passively in the background, like a security scan on your codebase that you read later, rather than something you're waiting on live.

RTX 5090 (or the 6000 Pro): less VRAM but insane bandwidth, so the models run fast, as fast as cloud in some cases. This is the one if you want to run an agent off a local model and have it respond instantly.

DGX Spark: the sweet spot. 128GB of unified memory, decent speed off Nvidia's CUDA, and it's the easiest to get going. You plug it in and tell the agent on your main machine to go set it up, you don't even need a monitor on it.

The catch, and it's a real one, is that hardware goes out of date fast. Nvidia is on a yearly cadence now: Hopper in 2022, Blackwell in 2024, Rubin this year. An H100 was reselling for about 45% of its new price by year three. Jensen Huang himself said once Blackwell shipped, "you couldn't give Hoppers away." So whatever you buy is depreciating quickly, and the thing you pay a premium for today is mid-tier in two years.

![Nvidia's hardware progression: Hopper 2022 to Blackwell 2024 to Rubin 2026, and how fast each one loses value](/assets/img/nvidia-hardware-progression.svg)

So you're caught between two things. Frontier models you might lose access to at any moment, and the hardware to run open ones yourself, which bleeds value the day you buy it. Neither is comfortable. But if I had to bet, I'd rather own the depreciating hardware and the open weights than be locked out entirely.

Owning something that loses value beats renting something that can be taken away.
