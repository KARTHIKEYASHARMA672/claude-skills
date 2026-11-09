---
name: ig-nikil-video-skill
description: Replicates Nikil's signature AI product-ad prompt-writing style (used with tools like Google Flow/Omni Flash, Higgsfield, etc.) for turning a product image into two ready-to-use prompts — a cinematic "story book prompt" and a panel-by-panel "video prompt". Use this skill whenever the user uploads or references a product image and asks for video ad prompts, story book prompts, panel prompts, or wants a product turned into an AI-generated ad in "my style" / "IG nikil style". Always trigger when the user mentions Flow.ai, Omni Flash, Higgsfield, or asks to "replicate my style" on a new product. Do not wait for the user to explain the format — infer everything from the product image and name, and produce both prompts by default.
---

# IG Nikil Video Skill

Turns a single product photo into two ready-to-paste AI video generation prompts, written in Nikil's exact voice and structure. Works for any product category (supplements, skincare, food, gadgets, etc.) — the skeleton stays the same, only the product-specific sensory details and beats change.

## Workflow

1. **Look at the uploaded product image carefully.** Note: pack/bottle shape, color palette, material (matte/glossy/metallic), any visible text/claims/certifications, logo, and the general "personality" of the brand (clinical & pure vs. bold & energetic vs. premium & luxe, etc.).
2. **Identify the product category** and pick the most natural "hero action" for that category (see Category Action Bank below) — this replaces the whey-protein-specific "scoop + shake" beat.
3. **Generate BOTH prompts** every time, in this order: story book prompt first, then video prompt. Don't ask the user which one they want — always give both.
4. **Do not ask clarifying questions before generating.** Infer USPs/claims from whatever text is visible on the pack in the image, or from general knowledge of that product type if nothing is visible. If the user gives a product name/brand only with no visible claims, invent 2-3 plausible, generic, non-medical claims that fit the category (avoid fabricating specific certifications or numbers you can't see on the pack).
5. After generating, briefly ask if they want the color grade, pacing, or hero action swapped — but give the full output first, don't gate it behind questions.

## Output Format 1: Story Book Prompt

A single unbroken paragraph (not bullet points), describing a 9-10 second ad as one continuous cinematic sequence, broken into second-by-second parenthetical timestamps. Structure to follow exactly:

- **(0-1s)** Establishing/mood shot — soft ambient environment shot related to product's natural context (kitchen, bathroom counter, vanity, desk, etc.), product visible in soft light, sets the mood.
- **(1-2s)** Slow push-in reveal of the packaging on a clean surface, studio light sweeping across it.
- **(2-3s)** A sensory "hero particle" burst moment specific to the product (see Category Action Bank) drifting in slow motion against a solid color backdrop that matches brand color.
- **(3-4s)** Macro close-up of the product's core texture/action (scoop, drop, spray, swipe, pour — whatever fits the category), in slow motion.
- **(4-5s)** Pack tilts/rotates to reveal glowing callout icons/text for 2-3 key claims, animating out from the panel.
- **(5-6s)** A trust/credibility beat — certification seal, "clean label," dermatologist-tested, lab-tested, etc. glowing on a colored panel with a supporting text line.
- **(6-7s)** Product being prepared/activated in its real use context (mixed, poured, applied, opened) — a human hand present but shown naturally.
- **(7-8s)** The product mid-use, held/worn/applied by a hand, in an active, real-life adjacent setting relevant to the category, with 1-2 lifestyle props blurred in the background.
- **(8-9s)** Quick cross-dissolve to a clean hero product shot on a pedestal against a soft brand-color gradient.
- **(9-10s)** Final brand lock: brand logo, product sub-name, key one-line tagline, pack centered on light background.

End the paragraph with a style tag line covering: transition style (cross-dissolve/whip-pan), color grade (named after the brand's dominant color + white), camera movement style (cinematic slow push-ins, subtle parallax), mood adjectives (3-4 words, e.g. "clean pure trustworthy energetic"), duration ("10s"), and "brand reveal at end: [Brand Name]".

## Output Format 2: Video Prompt (Panel Format)

Break the same story into 9 named panels. Format for each panel:

`Panel N "Two-to-Three Word Title": [shot description], [product/subject details], [camera angle], [lighting setup], [background/setting detail].`

Panel arc to follow (rename titles per product, but keep this narrative shape):
1. **Establishing/Silhouette** — atmospheric intro, product entering frame slightly out of focus, rack-focus into sharpness, subtle rim-light.
2. **Meet [Product]** — full hero shot of the pack/bottle standing upright, low-angle, three-point studio lighting, tagline copy referenced.
3. **Pure & Simple / Sensory Burst** — macro shot of the category's signature particle/texture (powder, mist, liquid droplet, cream swirl) floating/swirling around the product.
4. **Texture Action** — macro of the core interaction moment (scoop, drop, pump, pour), crisp texture, slight motion blur, overhead or close angle.
5. **Key Claim Highlight** — pack shown side-on or three-quarter with claim callouts glowing/highlighting in sequence, soft gradient background matching brand color.
6. **Trust/Certification Beat** — close-up on the certification/quality-seal area of the pack, subtle light flare, static macro, conveys purity/trust.
7. **Preparation/Activation** — lifestyle shot of the product being prepared for use (mixed, applied, opened), natural daylight, realistic setting (kitchen, bathroom, desk).
8. **Active Use** — close-up of hands using/holding/wearing the product mid-action, gentle motion blur, relevant lifestyle props softly blurred in background, bright airy light, dynamic diagonal composition.
9. **Brand Lock** — centered brand lock-up shot: full product on soft brand-color gradient, wordmark, subtext, tagline, high-key even lighting, static symmetrical hold.

Close with two lines:
- `Overall mood: [3-5 mood adjectives].`
- `Motion arc across panels: [short arrow-chained summary of the visual journey, e.g. "slow push-in → texture macro → claim highlight → trust beat → activation → active use → static logo lock"].`

## Category Action Bank

Use this to swap the "hero sensory action" and texture beats to fit whatever product is uploaded, instead of defaulting to powder/scoop:

- **Protein/supplement powders**: powder burst, scoop, shaker mix, gym-adjacent use.
- **Skincare (serum/cream/oil)**: liquid droplet fall, dropper release, cream swirl macro, dab/massage into skin, bathroom vanity setting.
- **Haircare**: pump dispense, foam/lather macro, application through hair strands, shower or vanity setting.
- **Beverages/drink mixes**: liquid pour, splash/bubble macro, glass fill, condensation droplets, kitchen or outdoor lifestyle setting.
- **Food/snacks**: ingredient close-up (nuts, grains, chocolate shards), plating or unwrapping moment, bite or crunch macro, kitchen/table setting.
- **Gadgets/tech**: light/reflection sweep across surface, UI glow macro, hand interaction (tap/press/unbox), desk or on-the-go setting.
- **Fragrance/cosmetics**: mist/spray burst, cap-off reveal, swipe/application macro, vanity or going-out setting.

If the uploaded product doesn't clearly fit one of these, invent a sensible equivalent — the point is always: burst/texture macro → interaction macro → claim highlight → trust beat → real-life use → brand lock.

## Brand Color Matching

Always pull the dominant pack color(s) from the image and use that as the backdrop/gradient color throughout (both prompts), the way lavender was used for The Whole Truth. Never default to a generic color — match the actual product packaging.

## Notes

- Keep both prompts as prose/panel text, not JSON or bullet lists with sub-bullets — this matches Nikil's original raw format that pastes directly into Flow/Omni Flash/Higgsfield.
- Keep total ad duration at 9-10 seconds unless the user specifies otherwise.
- Don't include people's faces prominently — hands and partial-body lifestyle framing only, matching the reference examples.
- Always give both outputs back-to-back in one response: story book prompt, then video prompt, clearly labeled.
