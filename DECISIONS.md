# Technical decisions

What we chose, what we assumed about knitting, why these providers, and how Assignment A keeps numbers honest.

## Choices and trade-offs

- **Notebooks, not a full app.** That is what the test asked for. The same Python can move into an API later.
- **Tool calling, not “do the math in the prompt”.** The model fills in width, yarn, stitch, then repeats Python’s answer. If the model did arithmetic, we could not prove it was right.
- **A mock path in Assignment A.** The tests must run with no API key. The mock still calls the same Python functions.
- **Disk cache in Assignment B.** Same swatch spec hashes to the same file, so we do not regenerate.
- **Pillow if images fail.** Missing key, network error, or DALL·E unavailable still shows a colour-correct stitch picture — not an error screen.
- **Ravelry is optional.** Real pattern photos are a check, not required to run the notebook.

## Domain assumptions and sources

- **Needles:** Craft Yarn Council standard yarn weights (`YARN_STANDARDS`). Firm = a bit smaller than the published range; drapey = a bit larger; balanced = the range as published.
- **Yarn meters:** area (cm²) × yarn rate × stitch factor. Balls assume **100 m each**, plus **1 spare**. That assumption is printed in the answer.
- **Stitch factors** are our table (stockinette 1.0 up to cable 1.40), not lab measurements. Unknown yarn or stitch returns an error, not a guess.
- **Gauge:** stitches per 10 cm. More stitches than the pattern means too tight (go up a needle). Fewer means too loose.
- **Swatch text:** stitch, weight, and fiber phrases are locked in dictionaries so the image prompt stays consistent.

## Why GPT-4o mini and DALL·E 3

**GPT-4o mini** — cheap enough for a 15-question test, good at calling tools, one OpenAI key shared with images. A bigger model would not make the math more correct; Python already does the math.

**DALL·E 3** — what Assignment B asked for, and it follows a detailed fabric prompt. If the account does not offer that model, we still show a Pillow swatch. That is the intended product behaviour, not a crash.

Ravelry is only for side-by-side real knits when keys exist. We do not generate swatches from it.

## How Assignment A keeps numbers accurate

1. **The LLM never calculates.** It only extracts arguments and quotes the tool result.
2. **Three Python functions own the numbers:** yarn quantity, needle size, tension. Assert tests run before the assistant.
3. **The scorecard re-runs those same functions.** Pass means the reply contains those numbers (or a required refuse).
4. **No API key still uses Python.** Offline does not change meters, balls, mm, or % off gauge.

Limit: if the model picks the wrong stitch name, the math is still consistent — just for the wrong input. That is a routing bug, not bad arithmetic.
