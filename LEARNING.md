# My AI Engineering Path
<!-- Managed by the ai-engineering-from-scratch learning skills.
     Repo: https://github.com/rohitg00/ai-engineering-from-scratch -->

## Mission
Ship an AI product. Build target: all four — an AI agent, a RAG product, a trained model, and whatever the product ends up needing beyond those.

Learner note: tech-curious, not from a CS background. Explain jargon in plain words the first time it appears, use analogies, and flag gaps from placement (missed: RF hyperparameters, residual connections, attention Q/K/V) as they come up instead of doing the Review phases up front.

## Placement
- Date: 2026-10-11
- Score: 7/10 (Math & Statistics 2/2, Classical ML 1/2, Deep Learning 1/2, NLP & Transformers 1/2, Applied AI 2/2)
- Entry point: Phase 7: Transformers Deep Dive
- Pace: as fast as possible

## Path
| Phase | Name | Status | Est. hours |
|-------|------|--------|------------|
| 0 | Setup & Tooling | Skip | -- |
| 1 | Math Foundations | Skip | -- |
| 2 | ML Fundamentals | Review | 26 |
| 3 | Deep Learning Core | Review | 15 |
| 4 | Computer Vision | Skip | -- |
| 5 | NLP — Foundations to Advanced | Review | 30 |
| 6 | Speech & Audio | Skip | -- |
| 7 | Transformers Deep Dive | Do | 14 |
| 8 | Generative AI | Do | 14 |
| 9 | Reinforcement Learning | Do | 13 |
| 10 | LLMs from Scratch | Do | 26 |
| 11 | LLM Engineering | Do | 19 |
| 12 | Multimodal AI | Do | 65 |
| 13 | Tools & Protocols | Do | 43 |
| 14 | Agent Engineering | Do | 55 |
| 15 | Autonomous Systems | Do | 20 |
| 16 | Multi-Agent & Swarms | Do | 28 |
| 17 | Infrastructure & Production | Do | 34 |
| 18 | Ethics, Safety & Alignment | Do | 31 |
| 19 | Capstone Projects | Do | 620 |

Total (Review + Do): ~1053 hours across 16 phases (~433 hours excluding the Phase 19 capstones).

## Project ideas
| Idea | Pipeline | Unlocks after | Notes |
|------|----------|---------------|-------|
| Granola-style meeting note-taker | Capture device audio + mic → speech-to-text (Whisper / Deepgram / AssemblyAI, chunked) → LLM turns transcript + user's rough notes into clean notes and action items | Phase 11 (basic); Phase 6 + 7/10 for speech internals; Phase 17 to ship | Added 2026-10-11. Live transcription uses Transformers on short audio chunks, so long meetings never hit the N² cost. |

## Progress log
| Date | Lesson | Quiz | Note |
|------|--------|------|------|
| 2026-10-11 | 07/01 why-transformers | 2/3 | Started at Phase 7 by choice. Got serial vs parallel and N² cost; mixed up when to pick Mamba (thought "short input → RNN"; rule is streaming/endless → RNN-style, fits in context → Transformer). |
| 2026-10-12 | 07/02 self-attention-from-scratch | 3/3 | Q/K/V clicked after YouTube (query=search box, key=title, value=video) and worked 'it → animal' example. Asked where Q/K numbers come from (answer: learned, start random). Counted 3 comparisons for 3 words instead of 9 (forgot self + grid). Closed placement Q7 gap. |
| 2026-10-12 | 07/03 multi-head-attention | 2/3 | Warm-up 3/3, including Transformer for a cover letter (first correct on the review item). Good on the head split (768/12=64), why tiny heads fail, and GQA shrinking the KV cache. Missed: thought multi-head exists to cut GPU work; it costs about the same and the win is specialization (each head has its own 100% budget). Mixed up GQA's memory saving with MHA's purpose. |
| 2026-10-12 | 07/04 positional-encoding | 3/3 | Warm-up 3/3, which cleared the Transformer-vs-Mamba review item (2 correct in a row). Got the clock-hands analogy for sin/cos. In a mid-lesson question, thought RoPE attention changes with prompt length; it only depends on the gap (though softmax competition does grow with length). Fixed by quiz time. |
| 2026-10-12 | 07/05 full-transformer | 3/3 | Warm-up 3/3, which cleared the last review item (multi-head purpose). Closed placement Q6 gap (residuals). Mid-lesson: first thought 'output = input' from a residual was bad; it's the safety feature, since without it a useless layer erases everything. Understood encoder (both directions) vs decoder (past only) for RAG search vs answer. Asked good follow-ups on RoPE gaps for repeated words. |
| 2026-10-14 | 07/06 bert-masked-language-modeling | 2/3 | Warm-up 2/2. Got fill-in-the-blank and both-sides clues (coffee=before, dog=after). Clear on the RAG split: BERT fingerprints (fast, cheap, done once) vs Claude writes the answer. Missed: thought 80/10/10 masking exists to hide answers; the real reason is that real text has no [MASK], so training must match real use. |
| 2026-10-14 | 07/07 gpt-causal-language-modeling | 3/3 | Warm-up 3/3 (80/10/10 review item correct once). Counted 4 practice questions from a 5-word sentence. Clear on parallel training (mask) vs serial generation. Picked temperatures well: extraction=greedy, brainstorm=high, RAG=low. |

## Review queue
- 07/06 bert-masked-language-modeling: why the 80/10/10 rule (real-world text has no [MASK]; training must match use, so BERT checks every word). Same idea as train/test mismatch. Correct in 07/07 warm-up; one more and it comes off.
