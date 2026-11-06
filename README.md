# Sushi Macro Tracker

A phone web app for logging nigiri and sashimi. Switch between **Nigiri** and **Sashimi**, tick the fish you ate, tap **+** for each piece, and see the day's calories, protein, fat, carbs and calories per gram of protein. It works and looks like the Disneyland Macro Tracker, without restaurants or locations.

Live app: https://fox294.github.io/sushi-macro-tracker/

## Requirements
- Android phone with Chrome (desktop Chrome and Edge also install it).
- Internet for the first visit. After that it works offline.

## Install on a phone
1. Open https://fox294.github.io/sushi-macro-tracker/ in Chrome.
2. Tap **Install app** at the top of the page, or Chrome's three-dot menu, then **Install app** (older versions say **Add to Home screen**).
3. Open it once while online so it caches itself for offline use.

## Tabs
- **Menu**: every fish, shellfish, roe and egg topping, plus common sides and sauces (soy sauce, ponzu, eel sauce, spicy mayo, ginger, wasabi, miso soup, edamame, seaweed salad). The **Nigiri / Sashimi** switch at the top sets whether the numbers are per nigiri piece (fish plus rice) or per sashimi slice (fish only). Search by English or Japanese name ("hamachi" or "yellowtail"). Filter by type, and sort by kcal per gram of protein, protein, calories, type or name. Tick what you ate; **+** and **−** count the pieces. On nigiri, **rice on N of M** sets how many of those pieces you ate with their rice: order 8 mackerel nigiri, eat the rice on 2, and pick 2; the other 6 count the fish only. The rice count follows the piece count until you change it. Tap a name to see its parts, grams and source.
- **Rice per nigiri** and **Fish slices** set the portion for new items: rice 15, 22 (default), 28 or 35 g per piece; fish thin (×0.75), standard or thick (×1.33). Change them to match the restaurant. If the day already has items logged at another size, the app offers to switch them to the current sizes.
- **Day log**: the selected day's items and counts, and the MacroFactor Quick Add list. The same **rice on N of M** picker appears under each nigiri item, and the MacroFactor list and copied log show it, for example "Mackerel nigiri x8 (rice on 2 of 8)". **Adjust rice and fish** under a nigiri item scales the rice or fish on every piece of that item, or unticks a part; the change shows in brackets, for example "[rice x0.5]".
- **Recent**: items you've logged before, newest first. Tick to add one to the selected day as 1 piece.
- **History**: one row per logged day with its totals. Tap a day to open it. Backup and restore live here.

## Moving entries into MacroFactor
MacroFactor has no import for food entries, so the Day log tab has an **Enter in MacroFactor** list. In MacroFactor tap + then **Quick Add**; in this app tap each value (calories, protein, fat, carbs) to copy it, paste it into the matching Quick Add field, then tick **Entered**. Changing an item's count clears its tick.

## Where your data lives
| Data | Where it is | In this repo? |
|---|---|---|
| Your daily log | The phone's browser storage for this web address | No. It never leaves the phone. |
| Backups | JSON files you save with **History > Back up log** (to Downloads) | No |
| Fish data and portion assumptions | Built into `index.html` (the `PARTS` and `FOODS` tables) | Yes |

The log belongs to this exact web address. If the app moves to a different address, back up first and use **Restore from backup** there. Clearing Chrome's site data for this address deletes the log.

## About the numbers
Every item is an estimate: the fish weight is assumed, not measured, so treat a piece as plus or minus 20 to 30 percent.
- **Composition** comes from USDA FoodData Central (FDC IDs are in each item's source line), or from Japan's Standard Tables of Food Composition 2020 (8th edition) for items USDA does not cover, such as toro, uni, ikura, unagi kabayaki and tamago. Sauces use the Kikkoman labels.
- **Your macro library**: tuna, seared tuna, salmon, mackerel, shrimp, snapper, yellowtail (farmed hamachi basis) and the seasoned sushi rice use the same values as the October 17, 2026 nigiri estimate in the Food Macro Estimation Project (Z:\collab\macro_project), and are tagged "Your library".
- **Portions**: nigiri default to 15 g of fish (10 to 12 g for shrimp, squid, octopus and thin white fish; 25 g for tamago) on 22 g of rice. Sashimi default to 18 g slices for tuna, salmon and yellowtail and 10 to 15 g for the rest. Restaurants vary: central Tokyo counters use about 10 to 15 g of rice per piece, many US restaurants 25 to 30 g.
- Chutoro has no food-table entry; it is the average of bluefin lean and fatty tuna.
- Each logged item keeps the numbers it had when you logged it, so later corrections to the data don't change past days.

## Files
- `index.html`: the app, with the fish data built in
- `manifest.webmanifest`, `sw.js`, `icon-*.png`, `apple-touch-icon.png`: what Chrome needs to install the app and run it offline
- `.nojekyll`: tells GitHub Pages to serve the files as they are

## Updating
Edit and push to `main`; GitHub Pages republishes within a minute or two. When `index.html` changes, also change `VERSION` in `sw.js` and `APP_VERSION` in `index.html` so installed copies pick up the update. The installed app loads the new version the next time it opens online.

The local copy at `Z:\dev\sushi-macro-tracker` is a Git checkout kept in step by Repo Autosync. Nothing runs from it.

## Removing it
Long-press the app icon and choose Uninstall (or remove it under Chrome's site settings). Uninstalling can delete the log, so back up first.

## Repository visibility
This repo is public, by Mike's choice on November 6, 2026, so GitHub Pages can serve it on a free account. It holds only app code and nutrition data; no personal data or logs.
