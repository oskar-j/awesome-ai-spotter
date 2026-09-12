# Awesome AI content detector [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

A curated list of awesome AI countermeasures — tools, models, datasets and research for detecting AI-generated content. What began as a response to the popularity of **ChatGPT** now covers the wider generative-AI landscape: text written by LLMs such as ChatGPT, Claude and Gemini, deepfake and AI-generated images, video and audio, and the watermarking and provenance standards designed to label synthetic media at the source. Collected and manually curated by [@oskar-j](https://github.com/oskar-j).

> ⚠️ **A word of caution:** no AI detector is fully reliable. Independent evaluations report significant false-positive rates (notably against non-native English writers), so treat any detection score as a signal — not proof.

## Contents

* [Official documentation and guidelines](#official-documentation-and-guidelines)
* [Frameworks and libraries](#frameworks-and-libraries)
* [Deep learning models at Huggingface](#deep-learning-models-at-huggingface)
* [Datasets and benchmarks](#datasets-and-benchmarks)
* [Commercial products and/or freeware](#commercial-products-andor-freeware)
* [Image, video and audio deepfake detection](#image-video-and-audio-deepfake-detection)
* [Watermarking and content provenance](#watermarking-and-content-provenance)
* [Tutorials (e.g. YouTube)](#tutorials-eg-youtube)
* [Research papers](#research-papers)
* [Obsolete (no more valid)](#obsolete-no-more-valid)

## Official documentation and guidelines

* [Educator FAQ](https://help.openai.com/en/collections/5929286-educator-faq) - OpenAI's official FAQ for educators on using ChatGPT in teaching and assessment **(from OpenAI)**.
* [How can educators respond to students presenting AI-generated content as their own?](https://help.openai.com/en/articles/8313351-how-can-educators-respond-to-students-presenting-ai-generated-content-as-their-own) - OpenAI help-center article stating that AI detectors have not proven reliable enough to base disciplinary decisions on, with suggested classroom alternatives.
* [Google Search's guidance about AI-generated content](https://developers.google.com/search/blog/2023/02/google-search-and-ai-content) - Google's official position that Search rewards high-quality content however it is produced, while using AI to manipulate rankings violates its spam policies.
* [Turnitin's AI writing detection capabilities FAQs](https://guides.turnitin.com/hc/en-us/articles/28477544839821-Turnitin-s-AI-writing-detection-capabilities-FAQs) - Turnitin's official documentation of how its AI writing detection model works, what content it covers and its known limitations.
* [UNESCO Guidance for generative AI in education and research](https://www.unesco.org/en/articles/guidance-generative-ai-education-and-research) - UNESCO's global policy guidance on regulating generative AI in education, including how institutions should handle AI-generated work.
* [AI Detectors Don't Work. Here's What to Do Instead.](https://mitsloanedtech.mit.edu/ai/teach/ai-detectors-dont-work/) - MIT Sloan Teaching & Learning Technologies guidance documenting detector error rates and recommending clear policies, assignment design and dialogue with students instead.

## Frameworks and libraries

* [Binoculars](https://github.com/ahans30/Binoculars) - Zero-shot LLM-generated text detector (ICML 2024) that contrasts the perplexities of two closely related language models, requiring no training data.
* [Fast-DetectGPT](https://github.com/baoguangsheng/fast-detect-gpt) - Efficient zero-shot detector (ICLR 2024) using conditional probability curvature, roughly 340x faster than DetectGPT at higher accuracy.
* [DetectGPT](https://github.com/eric-mitchell/detect-gpt) - Official implementation of the ICML 2023 zero-shot method that detects machine-generated text via negative curvature regions of a model's log-probability function.
* [Ghostbuster](https://github.com/vivek3141/ghostbuster) - Berkeley detector (NAACL 2024) that passes documents through weaker language models and trains a classifier over their features, without needing target-model token probabilities.
* [Glimpse](https://github.com/baoguangsheng/glimpse) - ICLR 2025 method that estimates full probability distributions from partial API observations, enabling white-box detection methods such as Fast-DetectGPT to work with proprietary models.
* [RADAR](https://github.com/IBM/RADAR) - IBM's NeurIPS 2023 framework that trains an AI-text detector via adversarial learning against a paraphraser, for robustness to paraphrasing attacks.
* [GLTR](https://github.com/HendrikStrobelt/detecting-fake-text) - MIT-IBM Watson AI Lab and HarvardNLP tool (ACL 2019) that visualizes per-token language-model probabilities to help humans spot statistically generated text.
* [LLM-DetectAIve](https://github.com/mbzuai-nlp/LLM-DetectAIve) - MBZUAI system (EMNLP 2024) for fine-grained detection, classifying text as human-written, machine-generated, machine-humanized or human-written-then-polished.

## Deep learning models at Huggingface

* [Hello-SimpleAI/chatgpt-detector-roberta](https://huggingface.co/Hello-SimpleAI/chatgpt-detector-roberta) - RoBERTa-base classifier fine-tuned on the HC3 corpus to distinguish ChatGPT answers from human-written ones (trained in early 2023, so dated against newer models).
* [openai-community/roberta-base-openai-detector](https://huggingface.co/openai-community/roberta-base-openai-detector) - OpenAI's classifier fine-tuned from RoBERTa on GPT-2 outputs, detecting GPT-2-generated text with roughly 95% accuracy.
* [TrustSafeAI/RADAR-Vicuna-7B](https://huggingface.co/TrustSafeAI/RADAR-Vicuna-7B) - RoBERTa-based detector trained via adversarial learning against a paraphraser (NeurIPS 2023), robust to paraphrasing attacks.
* [desklib/ai-text-detector-v1.01](https://huggingface.co/desklib/ai-text-detector-v1.01) - DeBERTa-v3-large based detector trained on the RAID dataset, a top performer on the RAID benchmark for adversarial robustness.
* [MayZhou/e5-small-lora-ai-generated-detector](https://huggingface.co/MayZhou/e5-small-lora-ai-generated-detector) - Lightweight e5-small classifier with LoRA fine-tuning reaching 0.939 accuracy on the RAID test set.
* [SuperAnnotate/ai-detector](https://huggingface.co/SuperAnnotate/ai-detector) - RoBERTa-large binary classifier trained on 44k text pairs from 14 generator models across the GPT, Llama, Anthropic and Mistral families.

## Datasets and benchmarks

* [RAID](https://github.com/liamdugan/raid) - ACL 2024 benchmark of over 10 million documents spanning 11 LLMs, 11 domains, 4 decoding strategies and 12 adversarial attacks, with a public detector leaderboard.
* [HC3](https://huggingface.co/datasets/Hello-SimpleAI/HC3) - Human ChatGPT Comparison Corpus of about 48k question-answer pairs with parallel human and ChatGPT responses in English and Chinese.
* [MAGE](https://github.com/yafuly/MAGE) - ACL 2024 benchmark of 447k human and machine texts from 27 LLMs across 10 domains, with eight testbeds of increasing difficulty for detection in the wild.
* [M4](https://github.com/mbzuai-nlp/M4) - Multi-generator, multi-domain, multi-lingual corpus for machine-generated text detection (EACL 2024 Best Resource Paper), also underpinning SemEval-2024 Task 8.
* [M4GT-Bench](https://github.com/mbzuai-nlp/M4GT-Bench) - ACL 2024 benchmark with three tasks: binary detection, multi-way generator identification and human-to-machine transition boundary detection.
* [DetectRL](https://github.com/NLP2CT/DetectRL) - NeurIPS 2024 benchmark evaluating detectors under realistic conditions such as varied prompts, human revision and adversarial attacks.

## Commercial products and/or freeware

* [GPTZero](https://gptzero.me/) - Widely used AI text detector with sentence-level highlighting and a free tier, popular in education for identifying text generated by ChatGPT, Claude, Gemini and other LLMs.
* [Pangram](https://www.pangram.com/) - AI text detector claiming over 99% accuracy with a very low false-positive rate, including detection of "humanizer"-rewritten text.
* [Originality.ai](https://originality.ai/) - Paid AI content detector combined with plagiarism, fact-checking and readability tools, aimed at publishers, SEO agencies and web-content teams.
* [AI Content Detector - Copyleaks](https://copyleaks.com/ai-content-detector) - AI text detector covering 30+ languages, with integrated plagiarism detection, LMS integrations, an enterprise API and a [Chrome extension](https://chromewebstore.google.com/detail/ai-content-detector-copyl/gplcmncpklkdjiccbknjjkoidpgkcakd).
* [Winston AI](https://gowinston.ai/) - Commercial AI detector offering a sentence-by-sentence "AI Prediction Map", plagiarism checking, OCR scanning of images and documents, and support for 14+ languages.
* [Turnitin AI Writing Detection](https://www.turnitin.com/solutions/topics/ai-writing/) - AI writing detection built into Turnitin's academic-integrity suite, scoring student submissions segment-by-segment for likely AI-generated long-form text.
* [Sapling AI Detector](https://sapling.ai/ai-content-detector) - Free online AI-generated text detector with a paid API for higher-volume use, from the maker of the Sapling writing-assistant platform.
* [ZeroGPT](https://www.zerogpt.com/) - Free web-based AI detector with batch file checking and multilingual support, bundled with plagiarism, grammar and word-count utilities.
* [Scribbr AI Detector](https://www.scribbr.com/ai-detector/) - Free, no-signup AI detector from the academic proofreading service Scribbr, aimed at students checking text from ChatGPT, Gemini and Copilot.
* [QuillBot AI Detector](https://quillbot.com/ai-content-detector) - Free AI detector within the QuillBot writing suite that classifies passages as AI-generated, AI-refined or human-written.
* [Grammarly AI Detector](https://www.grammarly.com/ai-detector) - Free AI checker built into Grammarly's writing suite, complemented by its Authorship feature that records how a document was composed.

## Image, video and audio deepfake detection

* [AI or Not](https://www.aiornot.com/) - Detects AI-generated and deepfake images, video, audio and text, with free checks and a commercial API used by newsrooms and businesses.
* [Hive AI-Generated Content Detection](https://hivemoderation.com/ai-generated-content-detection) - Enterprise APIs for detecting synthetic text, images, video, audio and AI-generated music at moderation scale, with a free web demo.
* [Sensity AI](https://sensity.ai/) - Forensic-grade deepfake detection platform for video, images and audio, deployed by governments and law enforcement in over 30 countries.
* [Reality Defender](https://www.realitydefender.com/) - Enterprise platform for real-time deepfake detection across audio, video and images in communication channels, with a free tier of 50 scans per month.
* [Resemble Detect](https://www.resemble.ai/detect/) - Real-time deepfake detection by Resemble AI covering audio, video and images, claiming coverage of over 250 generative models.
* [Pindrop](https://www.pindrop.com/) - Voice security platform whose Pulse product detects synthetic audio and deepfake callers in contact centers and video meetings within seconds.
* [ElevenLabs AI Speech Classifier](https://elevenlabs.io/ai-speech-classifier) - Free tool that estimates whether an audio sample was generated with ElevenLabs' own voice models.
* [Sightengine AI Image Detection](https://sightengine.com/detect-ai-generated-images) - Developer-oriented API that detects images generated by DALL-E, Midjourney, Stable Diffusion, Flux and others without relying on metadata or watermarks.
* [Illuminarty](https://illuminarty.ai/) - Free AI image detector that identifies synthetic images and deepfakes and can point to the generating model, with paid tiers adding localized detection and API access.
* [DeepFake-o-Meter](https://zinc.cse.buffalo.edu/ubmdfl/deep-o-meter/home) - Free, open academic platform from the University at Buffalo Media Forensics Lab that runs uploaded images, video and audio through many third-party deepfake detection algorithms.
* [isthisaigenerated.app](https://isthisaigenerated.app/site/) - Free, no-account checker for warning signals in images, text, documents and sampled video, with published limitations and downloadable reports.
* [TrueMedia.org](https://www.truemedia.org/) - Non-partisan deepfake detector for images, audio and video; the original service shut down in January 2025, open-sourced its [models](https://github.com/truemediaorg/ml-models), and has been revived at Georgetown University (closed beta).

## Watermarking and content provenance

* [SynthID](https://deepmind.google/models/synthid/) - Google DeepMind's watermarking technology that embeds imperceptible watermarks into AI-generated images, audio, text and video from Google models.
* [SynthID Detector](https://blog.google/innovation-and-ai/products/google-synthid-ai-content-detector/) - Google's verification portal (launched May 2025) that checks uploaded images, audio, video and text for SynthID watermarks.
* [SynthID Text](https://huggingface.co/blog/synthid-text) - Open-source release of Google DeepMind's text watermarking, integrated into Hugging Face Transformers for watermarking and detecting LLM-generated text.
* [C2PA](https://c2pa.org/) - Coalition for Content Provenance and Authenticity — the open technical standard behind Content Credentials, steered by Adobe, Google, Meta, Microsoft, OpenAI, Sony, TikTok and others.
* [Content Credentials Verify](https://verify.contentauthenticity.org/) - Free web tool from the Content Authenticity Initiative for inspecting a file's Content Credentials (C2PA provenance metadata) to see how it was made and edited.
* [Meta Video Seal](https://github.com/facebookresearch/videoseal) - Meta's open-source (MIT-licensed) invisible watermarking models for images and video, with training code and checkpoints.
* [MarkLLM](https://github.com/THU-BPM/MarkLLM) - Open-source toolkit (EMNLP 2024) implementing roughly 20 LLM watermarking algorithms with unified visualization and evaluation pipelines.
* [lm-watermarking](https://github.com/jwkirchenbauer/lm-watermarking) - Reference implementation of "A Watermark for Large Language Models" (ICML 2023), embedding and detecting statistical watermarks via a Hugging Face logit processor.

## Tutorials (e.g. YouTube)

* [How Do AI Detectors Work?](https://gptzero.me/news/how-ai-detectors-work/) - GPTZero's explainer of AI-detection techniques such as perplexity, burstiness and trained classifiers, including their limitations (vendor-authored).
* [Tips and Trends: AI Text Detectors](https://acrl.ala.org/IS/tips-and-trends-ai-text-detectors/) - Overview from the American Library Association's ACRL Instruction Section covering how AI text detectors work, their documented accuracy problems and academic-integrity implications.
* [AI-Detectors Biased Against Non-Native English Writers](https://hai.stanford.edu/news/ai-detectors-biased-against-non-native-english-writers) - Stanford HAI article on research showing AI detectors flagged over 61% of TOEFL essays by non-native English speakers as AI-generated.

## Research papers

* [DetectGPT: Zero-Shot Machine-Generated Text Detection using Probability Curvature](https://arxiv.org/abs/2301.11305) - Mitchell et al. (ICML 2023) show that LLM-generated text occupies negative-curvature regions of the model's log-probability function, yielding a zero-shot detection criterion.
* [Spotting LLMs With Binoculars: Zero-Shot Detection of Machine-Generated Text](https://arxiv.org/abs/2401.12070) - Hans et al. (ICML 2024) detect machine-generated text by contrasting perplexity against cross-perplexity between two closely related language models, with no training data.
* [Fast-DetectGPT: Efficient Zero-Shot Detection of Machine-Generated Text via Conditional Probability Curvature](https://arxiv.org/abs/2310.05130) - Bao et al. (ICLR 2024) replace DetectGPT's perturbation step with conditional probability curvature sampling for a 340x speedup and higher accuracy.
* [A Watermark for Large Language Models](https://arxiv.org/abs/2301.10226) - Kirchenbauer et al. (ICML 2023) promote a pseudo-random "green list" of tokens during sampling, so watermarked text is detectable from a short span without model access.
* [Can AI-Generated Text be Reliably Detected?](https://arxiv.org/abs/2303.11156) - Sadasivan et al. show recursive paraphrasing breaks detectors including watermarking and retrieval-based schemes, and derive theoretical limits tied to the overlap between human and AI text distributions.
* [A Survey on LLM-Generated Text Detection: Necessity, Methods, and Future Directions](https://arxiv.org/abs/2310.14724) - Wu et al. (Computational Linguistics 2025) review watermarking, statistical and neural detection methods along with open challenges such as distribution shift and evaluation gaps.
* [RAID: A Shared Benchmark for Robust Evaluation of Machine-Generated Text Detectors](https://arxiv.org/abs/2405.07940) - Dugan et al. (ACL 2024) evaluate open and commercial detectors on 6M+ generations and find most fail under adversarial attacks and unusual decoding strategies.
* [GLTR: Statistical Detection and Visualization of Generated Text](https://arxiv.org/abs/1906.04043) - Gehrmann, Strobelt and Rush (ACL 2019) introduce per-token probability visualization that raises human detection rates of generated text.
* [Glimpse: Enabling White-Box Methods to Use Proprietary Models for Zero-Shot LLM-Generated Text Detection](https://arxiv.org/abs/2412.11506) - Bao et al. (ICLR 2025) estimate full output distributions from partial API observations so white-box detectors can score text under proprietary models such as GPT-4.
* [Diversity Boosts AI-Generated Text Detection](https://arxiv.org/abs/2509.18880) - Basani and Chen (TMLR 2026) introduce DivEye, detecting AI text via surprisal-based features that capture fluctuations in lexical and structural unpredictability.

## Obsolete (no more valid)

* [AI Text Classifier](https://openai.com/index/new-ai-classifier-for-indicating-ai-written-text/) - OpenAI's own AI-written-text classifier, discontinued on July 20, 2023 due to its low rate of accuracy **(from OpenAI)**.
* [GPT-2 Output Detector Demo](https://huggingface.co/spaces/openai/openai-detector) - Online demo of the GPT-2 output detector model based on RoBERTa; the Hugging Face Space is now paused and the model long superseded.

## Contributing

Contributions are welcome! Found a great detector, model, dataset or paper that's missing — or a link that has gone stale? Open an issue or a pull request — see the [contribution guidelines](CONTRIBUTING.md).
