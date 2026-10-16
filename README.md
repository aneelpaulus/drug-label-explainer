# Drug Label Explainer

Type the name of a prescription drug, maybe one you saw in a TV ad, and read its official FDA label in plain English.

**[Try it live](https://aneelpaulus.github.io/drug-label-explainer/)**

I built this after someone whose father had cancer told me she wished she could type in a drug's name and quickly see what it's approved for, what the studies behind its approval showed, and whether it works for someone his age. That information is all in the FDA label. It's just written for doctors.

## What you get

- **What it's approved for**, as a short list.
- **What the main studies found.** These are the studies the FDA reviewed, with the key numbers pulled out: overall survival, progression-free survival, response rate, duration of response, blood sugar change, heart events, and so on. Each hazard ratio and median gets a plain-English note ("a hazard ratio of 0.68 means about 32% lower risk..."). Results from smaller sub-analyses are labeled so they aren't mistaken for the main finding. The results tables and full text are one tap away.
- **What the label says about age.** Enter an age and you'll see the label's section on older adults or children, the ages of the people in each study, and questions to ask the doctor. The tool never says whether a drug will help a particular person, because the label can't answer that.
- **Most common side effects** and the boxed warning, if there is one.
- **A report for your AI assistant.** One click downloads a text file with the label and instructions asking the AI to explain it simply, using only what the label says. Upload or paste it into ChatGPT, Claude, Gemini, or Copilot. Visitors with their own Claude API key can also get the summary right on the page.
- **A short glossary** of terms like median, hazard ratio, and confidence interval. Dotted terms show a definition when tapped.

It works for any prescription drug with an FDA label, whether for diabetes, arthritis, skin conditions, or cancer. Survival and response cards appear when the label reports them.

## Where the information comes from

| What | Source |
|---|---|
| The label itself | FDA drug labels via [openFDA](https://open.fda.gov) |
| First approval date | Drugs@FDA via openFDA |
| Link to the full official label | [DailyMed](https://dailymed.nlm.nih.gov) (National Library of Medicine) |
| Optional AI summary | Anthropic's Claude API, using the visitor's own key |

The page runs in your browser and has no server. Drug names go only to openFDA. If someone uses the AI button, the label text and their key go only to Anthropic. Nothing is stored.

## How it handles the messy parts

- **Several versions of one drug.** Typing "Keytruda" finds both Keytruda and Keytruda Qlex, and typing a generic name like "semaglutide" finds Ozempic and Wegovy. You pick from the versions found.
- **Repackaged copies.** Many companies re-list a drug under their own name. The tool prefers the manufacturer's own label.
- **Labels with missing name tags.** Some labels, such as Darzalex's, lack the FDA's standard name tags, so the tool also searches the label text itself.
- **Long labels.** Keytruda's label covers more than 20 cancers. A filter narrows the studies (for example "lung"), and the AI report follows the same filter.

## Limitations

- **Key results are pulled out automatically.** The tool can miss a number or pick a less important one. Each study card links to the full text and tables.
- **Labels describe groups, not individuals.** A result from a study population doesn't predict what will happen to one person.
- **The label isn't the latest data.** It covers what the FDA reviewed. Newer study results presented at medical meetings may not be in it yet.
- **Very long labels make long reports.** The AI report is capped at about 90,000 characters. Filtering by condition keeps it focused.

## Run your own copy

The whole tool is one file, `index.html`. To host it free on GitHub:

1. Create a new public repository and upload `index.html`, `README.md`, and `LICENSE`.
2. In the repository, open **Settings**, then **Pages**.
3. Under "Build and deployment", choose **Deploy from a branch**, select `main` and `/ (root)`, and save.

## Disclaimer

For education only. This is not medical advice, and it doesn't replace a conversation with a doctor who knows the person's full situation. Not affiliated with the FDA, the National Library of Medicine, or any drug maker.

## License

MIT. See `LICENSE`.

Built by Aneel Paulus, MD, MS.
