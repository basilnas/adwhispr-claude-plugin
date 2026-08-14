---
name: clone-winning-ads
description: Turn a competitor's proven ad into the user's own creative and get it live. Use when the user wants to copy, clone, remix, or adapt a winning ad they found, wants a script based on a competitor's TikTok ad, or wants to launch a creative they already have onto Meta or TikTok.
---

# Clone proven winners, then launch

The loop: find an ad that has already survived months of spend, adapt it to the user's brand, launch it paused, let the user flip it live.

## TikTok script cloning (available right here)

1. `research_tiktok_ads` with the competitor's name. Longest-running first; those are the proven winners.
2. `clone_tiktok_ad` with the advertiser name and adId. This produces a SHOOT-READY SCRIPT BRIEF, not a finished video: it samples real frames from the source ad, analyzes hook, structure, and pacing, then writes a shot-by-shot script adapted to the user's product and voice. Free, text output.
3. The user films it, uploads the video at https://adwhispr.com/dashboard/creatives, and `launch_tiktok_campaign` takes it live (created paused).

## Finished image and video creatives (made in the AdWhispr web app)

Generating finished media happens in the AdWhispr dashboard at https://adwhispr.com/dashboard, not through this connection. When the user wants a competitor ad cloned into a finished image or an AI video made for their brand, point them there. Everything they generate lands in their Creative Library, and this connection launches it:

- `list_my_creatives` shows the library.
- `launch_cloned_ad` launches an image clone they made in the app as a paused Meta ad.
- `launch_meta_ad` launches their OWN images (1 card = single image, 2 to 10 cards = carousel) or video (single card) as a paused Meta ad.
- `launch_tiktok_campaign` launches their own video on TikTok by creativeName.

Never launch competitor media or ad-library assets as the user's creative.

## Launch safety (always applies)

- Every campaign is created PAUSED. Nothing spends until the user resumes it.
- Launch, budget, and resume tools are TWO-STEP: first call returns a preview plus a confirmToken; show the preview, get the user's explicit OK, then call again with the same args plus that token. Never invent a token.
- `resume_campaign` starts real spend. Surface its warning and confirm before passing the token.
- If the user has not clearly stated the campaign objective, ask them to pick from the valid list instead of guessing.
- Targeting is opt-in. Only set what the user asked for; resolve real ids with `search_ad_targeting` first and never invent ids.
