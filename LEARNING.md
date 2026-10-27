# My AI Engineering Path
<!-- Managed by the ai-engineering-from-scratch learning skills.
     Repo: https://github.com/rohitg00/ai-engineering-from-scratch -->

## Mission
Ship an AI product. Build target: all four — an AI agent, a RAG product, a trained model, and whatever the product ends up needing beyond those.

Learner note: tech-curious, not from a CS background. Explain jargon in plain words the first time it appears, use analogies, and flag gaps from placement (missed: RF hyperparameters, residual connections, attention Q/K/V) as they come up instead of doing the Review phases up front.

Teaching format (learner request, 2026-10-15): give the FULL theory of the lesson first in one go (concepts, analogies, real numbers), then ask questions together at the end. Do not interrupt every few paragraphs with check questions.

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
| 7 | Transformers Deep Dive | Done | 14 |
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
| Granola-style meeting note-taker | Capture device audio + mic → speech-to-text (Whisper / Deepgram / AssemblyAI, chunked) → LLM turns transcript + user's rough notes into clean notes and action items | Phase 11 (basic); Phase 6 + 7/10 for speech internals; Phase 17 to ship | Added 2026-10-11. Live transcription uses Transformers on short audio chunks, so long meetings never hit the N² cost. Refined 2026-10-14 (07/10): Whisper large-v3-turbo (30s chunks) + diarization (pyannote, Speaker A/B) → merge → map speakers to names (calendar/user/context) → Claude at low temperature → notes + action items. |

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
| 2026-10-14 | 07/08 t5-bart-encoder-decoder | 3/3 | Warm-up 3/3, which cleared the 80/10/10 review item. Got cross-attention (Q from decoder, K/V from encoder; 'noir' → 'black' despite reordering). Mapped the note-taker: Whisper (enc-dec, audio→text) then Claude (decoder-only, text→notes). |
| 2026-10-14 | 07/09 vision-transformers | 3/3 | Warm-up 2/2. Got patches = tokens (784 patches for 8x8). Mid-lesson: said 4x tokens gives 4x attention cost; it's 16x (N²). Fixed by quiz. Picked smaller patches for receipts and learned the risks (misread digits vs cost). Asked how many lessons remain (292 in the main path; offered a fast-track option). |
| 2026-10-14 | 07/10 audio-transformers-whisper | 2/3 | Warm-up 2/2. Got 120 chunks per hour and why (N², plus Whisper trained on 30s). Designed the full note-taker pipeline (Whisper + diarization + name mapping + Claude). Missed: thought turbo got faster through shorter chunks; it keeps the big encoder and shrinks the decoder from 32 to 4 layers. |
| 2026-10-14 | 07/11 mixture-of-experts | 3/3 | Warm-up 2/2 (Whisper-turbo review item correct once). Got router = picks top experts per word, total vs active params (MoE is faster but needs memory for ALL experts), load balancing stops 'rich get richer'. Self-host rule: MoE when GPU memory is plentiful, dense when memory is tight. |
| 2026-10-15 | 07/12 kv-cache-flash-attention | 3/3 | Warm-up 1/3: said MoE uses less memory (it needs ALL experts loaded); Whisper turbo answered 'smaller encoder' again. Mid-lesson: thought old words' K/V get recomputed for every new word; clicked once tied to the causal mask (old words can't see new ones, 'diary in pen'). Thought Flash skips math (that's sliding window); it does the same math with fewer slow-memory trips. Quiz clean. |
| 2026-10-15 | 07/13 scaling-laws | 3/3 | Warm-up 4/4 (both review items correct once). Got Chinchilla 20 tokens/param (7B → 140B), over-training for serving cost, emergence as a scoring artifact. Asked for full theory first instead of frequent questions; switched format mid-lesson. |
| 2026-10-24 | 07/14 build-a-transformer-capstone | 2/3 | Taught theory-first (full architecture walkthrough, then questions). Got loss 4.17 = uniform guessing over 65 chars, and val-loss rising = overfitting. Missed: thought 64 practice questions means running the model 64 times; it's ONE parallel pass (shift-by-one targets + causal mask). MoE review missed again ('20B memory'). |
| 2026-10-27 | 07/15 attention-variants | 3/3 | Theory-first. Got SWA-only loses/blurs far facts, Gemma 3 5:1 SWA:global mix for long-range links at ~6x less KV, differential attention = two maps minus noise at 2x KV. MoE review correct ('300B memory, 30B speed'). |
| 2026-10-27 | 07/16 speculative-decoding | 3/3 | Theory-first. Got one-pass verification at every position (links to capstone), identical output distribution, best fit = structured low-temp text (like the note-taker). Whisper turbo review missed a 3rd time ('smaller encoder'); re-explained with listener/typist analogy. Phase 7 complete. |

## Review queue
- 07/10 audio-transformers-whisper: Whisper-turbo speed comes from shrinking the DECODER (32→4 layers) and keeping the big encoder. Understanding audio is the hard part; writing text is the easy part. Chunk length stays 30s. (Correct in 07/11 warm-up, missed again in 07/12 warm-up ('smaller encoder'); needs 2 correct in a row. Missed a 3rd time in 07/16 ('smaller encoder'). Analogy: ENCODER = the ears/listener (kept big, the hard part); DECODER = the typist (shrunk 32→4 layers, the easy part). Needs 2 correct in a row.)
- 07/11 mixture-of-experts: MoE saves COMPUTE, not MEMORY. 100B total / 10B active runs about as fast as a 10B dense model but needs memory for all 100B. (Missed 07/12, correct 07/13, missed again 07/14 ('20B memory'). Needs 2 correct in a row. Rule: memory follows TOTAL params, speed follows ACTIVE params. Correct in 07/15; one more clears it.)
- 07/14 build-a-transformer-capstone: one snippet of 64 characters = 64 practice questions in ONE forward pass. Targets are the same text shifted by one; the causal mask hides the future so all 64 are answered in parallel. Running one-by-one only happens at generation time.
