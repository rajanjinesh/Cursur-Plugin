---
name: promo-analysis
description: Read one competitor promo image and return only competitor, offer, and threat. Use when the user shares a single competitor promotion image, screenshot, or creative and wants those three fields. Read the image before classifying. Do not search, add fields, build a dashboard, use Mixpanel, or write to Supabase.
---

# Promo analysis

Read one competitor promo image, then classify it. Work from what is visible in that image.

## Order

1. Read the image.
2. Fill the three fields from what you saw.
3. Return only those fields.

Do not search. Do not infer a brand, price, or offer that the image does not show.

## Fields

Return exactly these fields:

- **competitor**: who the promo is from.
- **offer**: the promo in one line.
- **threat**: `low`, `medium`, or `high`.

If a field is not visible, write `unknown`. Do not invent it.

## Threat

Judge threat only after reading the image.

- **low**: a small or routine discount.
- **medium**: a clear price or offer a product manager should notice.
- **high**: a sharp price cut, a flagship promo, or something that could move customers.

If the image does not show enough to choose one of those, set threat to `unknown`.

## Output

Return only the three fields. No extra fields, no commentary, no search, no dashboard, and no Mixpanel.

```
competitor: <name or unknown>
offer: <one line or unknown>
threat: <low | medium | high | unknown>
```

## Data

The table `competitor_offers` already exists. Do not create or alter it. Do not write to Supabase from this skill.
