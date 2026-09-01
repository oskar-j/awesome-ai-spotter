# Contributing

Thanks for helping keep this list useful and up to date! Contributions of all kinds are welcome: new entries, better descriptions, and reports of dead or outdated links.

## Adding an entry

1. Make sure the resource is **about detecting AI-generated content** (text, image, video, or audio) or about watermarking/provenance of AI content.
2. Add one bullet to the most fitting section of `README.md`, in this exact format:

   ```markdown
   * [Resource Name](https://example.com/) - One-sentence factual description ending with a period.
   ```

3. Keep the description neutral and specific — what it detects, what technique it uses, or what makes it notable (free tier, API, languages, paper venue). Avoid marketing language.
4. Check that the link works and points to the canonical page (project homepage, GitHub repo, arXiv abstract page, or Hugging Face model/dataset page).
5. If you add, rename, or remove a section, update the **Contents** table at the top of the README.

## Quality bar

An entry should be notable and maintained: an actively developed tool, a peer-reviewed or widely cited paper, or a model/dataset people actually use. Please don't submit:

- Tools for **evading** detection (paraphrasers, "humanizers") — this list is about countermeasures, not counter-countermeasures.
- Thin SEO pages that wrap someone else's detector.
- Self-promotion without evidence of adoption or independent coverage.

## Dead or outdated resources

Tools that shut down or no longer work are **moved to the "Obsolete (no more valid)" section**, not deleted — the history of AI detection is part of the story. If you spot a stale link, feel free to open an issue if you'd rather not send a PR.

## Pull requests

- One resource (or one coherent change) per pull request keeps reviews fast.
- A commit message like `Added 'Resource Name'` matches the repo's history.
