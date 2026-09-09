# Case-study image sources — re-capture manifest

Updated: 2026-09-09

Every case-study screenshot, classified by where a higher-resolution replacement
has to come from. Drop replacements into `assets/img/` with the **same filename**
and I'll update the intrinsic `width`/`height` and re-encode.

**Target:** capture / export at **2×** the size it's displayed. Displayed widths:
full-width shots ~1040 px → export **≥ 2080 px**; paired shots ~510 px → export
**≥ 1040 px**; trio / mosaic ~340–480 px → export **≥ 960 px**.

## Legend

| Tag | Meaning | How to get a replacement |
|-----|---------|--------------------------|
| 🌐 **Public** | Live public page, current design still matches your screenshot | Re-screenshot at 2× — browser DevTools **device toolbar → responsive → set DPR 2**, or a full-page screenshot extension (GoFullPage, Firefox built-in), or macOS screen capture at 2× |
| 🔒 **Auth** | A signed-in / logged-in state on a public site | Re-capture while logged in, or export the frame from Figma |
| 🏢 **Internal** | Staff intranet / admin / internal platform — not on the public web at all | Figma export only |
| 📱 **Kiosk / app** | Not a website (kiosk hardware, mobile app) | Figma / prototype export |
| 🖼️ **Graphic** | A logo or a photo, not a UI screenshot | Supply the vector / original hi-res file |
| ⚠️ | Screenshot also has a **content bug baked into the pixels** (see `ENHANCEMENTS.md`) — the real product/design needs fixing *before* a fresh capture is worth taking |

---

## ✅ Best candidates — public, design confirmed current (I checked the live sites)

### case-qnl — qnl.qa  *(6 of 7 re-capturable)*
| File | Screen | Source |
|------|--------|--------|
| 035 | Main portal homepage | 🌐 `qnl.qa/en` |
| 036 | Circulation & Borrowing Dept homepage | 🌐 Departments → Circulation & Borrowing |
| 037 | Media gallery viewer | 🌐 Media → Photos & Videos |
| 038 | All News grid | 🌐 News → View All |
| 039 | Single news article + Latest News carousel | 🌐 any current article (content will differ from the original) |
| 040 | Shared documents listing | 🌐 if still public; 🔒 if moved behind login |
| 043 | "Request deleted" confirmation | 🏢 internal staff tool |

### case-grsia — daman.gov.qa  *(all 8 re-capturable)*
| File | Screen | Source |
|------|--------|--------|
| 049 | Homepage — "Connecting Generations" | 🌐 |
| 050 | FAQ (nine categories + Sara assistant) | 🌐 |
| 051 | Media Center — List of News | 🌐 Media Center → News |
| 052 | Media Center — List of Albums | 🌐 Media Center → Multimedia → Albums |
| 053 | News article (Key Points / Article Summary) | 🌐 (content differs) |
| 054 | Magazine detail + edition selector | 🌐 Media Center → Magazine |
| 055 | El Safwa retiree discounts marketplace | 🌐 El Safwa |
| 056 | Magazines archive grid | 🌐 Media Center → Archive |

### case-clayton — claytonarthouse.com  *(all 8 re-capturable — design confirmed current)*
| File | Screen | Source |
|------|--------|--------|
| 160 | Homepage (hands-in-clay hero → events preview) | 🌐 |
| 161 | Workshops grid (10 categories) | 🌐 Workshops |
| 162 | Workshop detail — Candle-making | 🌐 Workshops → Candle-making |
| 163 | All Events | 🌐 Events |
| 164 | Our History | 🌐 Our Journey |
| 165 | Studio — "Calm & Destress" candle photography | 🌐 Studio |
| 166 | About Us — colour-banded sections | 🌐 About us — ⚠️ footer still shows `info@grsia.gov.qa` / `info@squareevents.com` / Lorem ipsum (site-builder placeholder — fix or crop out) |
| 167 | Contact — booking / enquiry form | 🌐 Contact |

### case-qpmc — qpmc.qa (Al-Awalia)  *(all 15 re-capturable)*
| File | Screen | Source |
|------|--------|--------|
| 107 | Full homepage | 🌐 |
| 108 | Homepage with cookie-consent banner | 🌐 (clear cookies / private window for first-visit state) |
| 109 | Hero article + detail component | 🌐 |
| 110 | About Us (عن الأولية) | 🌐 |
| 111 | Company / team page | 🌐 |
| 112 | Gabbro product detail (per-ton pricing) | 🌐 Products → Gabbro |
| 113 | Washed sand product detail | 🌐 Products → Washed Sand |
| 114 | Recycled aggregate pricing table | 🌐 |
| 115 | Ports Management page | 🌐 |
| 116 | Locations page — interactive map | 🌐 — ⚠️ **map shows San Francisco, not Qatar** — fix the map data first |
| 117 | Tenders listing (countdown timers) | 🌐 Tenders |
| 118 | Tender detail (bank-transfer instructions) | 🌐 any open tender |
| 119 | Report a Violation form | 🌐 |
| 120 | Request Info — success confirmation | 🌐 (submit the form to reach this state) |
| 121 | Media gallery / photo album | 🌐 Media |

### case-joodeskan — joodeskan.sa  *(6 of 9 re-capturable)*
| File | Screen | Source |
|------|--------|--------|
| 076 | Homepage | 🌐 |
| 077 | Beneficiary Services (3-step eligibility) | 🌐 |
| 078 | Partner association profile page | 🌐 Partner Associations → any association |
| 079 | Partner Associations directory | 🌐 |
| 080 | Jood 365 recurring-giving page | 🌐 |
| 082 | Report a Problem support form | 🌐 |
| 083 | Donor dashboard (donation-history chart) | 🔒 logged-in donor account |
| 084 | My Contributions tab | 🔒 logged-in donor account |
| 085 | Guinness World Records recognition | 🖼️ award-ceremony press image — supply the original hi-res photo |

### case-mehrab — me7rab.sa  *(7 of 9 re-capturable)*
| File | Screen | Source |
|------|--------|--------|
| 096 | Public homepage | 🌐 |
| 097 | Sign-in screen | 🌐 |
| 099 | Donor's Reports Log — list view | 🔒 logged-in donor account |
| 100 | Reports Log — donation chart | 🔒 logged-in donor account |
| 101 | Nationwide case browser | 🌐 |
| 103 | Public statistics dashboard (region map) | 🌐 |
| 104 | News section | 🌐 |
| 105 | Contact Us (form + map) | 🌐 |
| 106 | Our Services catalogue (7 need-categories) | 🌐 |

### case-surah — web.surahapp.com  *(7 of 8 re-capturable)*
| File | Screen | Source |
|------|--------|--------|
| 134 | Official logo lockup | 🖼️ supply the vector / hi-res PNG |
| 135 | Homepage — Surahs / Juzas grid | 🌐 |
| 136 | Reading mode — two-page mushaf (Al-Fatiha) | 🌐 |
| 137 | Translation mode — Saheeh International | 🌐 |
| 138 | Tafsir mode — Tafsir al-Mukhtasar | 🌐 |
| 139 | Word-level study panel | 🌐 (tap a word) |
| 140 | Settings panel | 🌐 |
| 141 | Public landing page (platform badges) | 🌐 surahapp.com |

### Single public shots
| File | Case | Screen | Source |
|------|------|--------|--------|
| 059 | case-saso | SASO public homepage + service catalogue | 🌐 `saso.gov.sa` |
| 067 | case-mcit | MCIT official ministry website | 🌐 `mcit.gov.qa` |
| 072 | case-mcit | Job vacancies list | 🌐 careers — ⚠️ vacancy copy is oil-&-gas (TRAGS) lorem; fix the listing data |
| 073 | case-mcit | "Create your account" registration | 🌐 — ⚠️ field placeholders read "Select the reporting month" |
| 074 | case-mecc | Permits portal homepage | 🌐 `mecc.gov.qa` |
| 075 | case-mecc | "How the platform works" | 🌐 |
| 090 | case-trags | Corporate homepage | 🌐 `tragsqatar.com` |
| 122 | case-ccq | Public Community Services landing (logged out) | 🌐 `community.edu.qa` |
| 124 | case-ccq | Service Catalog (Student / Faculty toggle) | 🌐 or 🔒 (may need login) |
| 058 | case-qu | "Assistant widget" | 🌐 low-priority single element |

---

## 🔒 Auth — re-capture logged in, or export from Figma

| Case | Files | Screens |
|------|-------|---------|
| case-saso | 061, 062, 063, 064, 065 | Vehicle / trailer identity-card request flows, pre-filled record, heavy-equipment dashboard, applicant's requests list — behind Nafath / Saudi Business Center login |
| case-ccq | 127, 128, 129, 130, 132, 133 | My Tasks, My Requests, graduation-application flow, advisor review panel, success screen — student & advisor accounts |
| case-mehrab | 099, 100 | Donor Reports Log (list + chart) |
| case-joodeskan | 083, 084 | Donor dashboard, My Contributions |
| case-mecc *(from the artifact's expanded set — not yet on the site)* | — | Requests dashboard, Identity & Account Management (personal + corporate), Create Delegation form, Project Details modal |

---

## 🏢 Internal — Figma export only (not on the public web)

| Case | Files | What it is |
|------|-------|-----------|
| **case-qsl** | 148–155 (all 8) | Qatar Stars League club financial & contract **compliance platform** — internal to the league, not on qsl.qa |
| **case-manateq** | 142–147 (all 6) | Manateq **Partners Portal** dashboards (cheque collection, contractor performance, budget, cash flow, balance sheet, fixed assets) — ⚠️ one billing-table image has Vietnamese placeholder text |
| **case-gama** | 044–048 (all 5) | GAMA **staff intranet** (homepage, medical-services catalogue, service detail, employee directory, department workspace) — ⚠️ 044 + 047 (+3 more) show "© TechCorp / hello@techcorp.com / Silicon Valley" and oil-&-gas lorem — real content must be fixed first |
| **case-trags** | 091, 092, 093, 094, 095 | TRAGS internal EPC portal (business-units nav, signed-in home, Digital Library report + libraries, infrastructure-projects directory) |
| **case-mcit** | 068, 071 | MCIT Calendar internal tool (timeline, "Item Edited" confirmation) |
| **case-qnl** | 043 | "Request deleted" staff-tool confirmation |

---

## 📱 Kiosk / app / composite — Figma / prototype export

| Case | Files | What it is |
|------|-------|-----------|
| **case-joodeskan-kiosk** | 086, 087, 088 *(+ 5 more in the artifact: Arabic idle screen, 5-preset amount screen, contactless mid-flow, thank-you, declined-card)* | Physical donation-kiosk touchscreen — not a website. **Also the biggest content gap: the site shows 3 screens, the artifact has 8.** |
| **case-optimumvision** | 089 | "Onboarding / service categories / booking flow" composite — app screens. Higher-res version may be on your [Behance project](https://www.behance.net/gallery/159732165/OV-Optiumum-Vision-Tourism) |

---

## Summary

| Bucket | Images | Who |
|--------|-------:|-----|
| 🌐 Public — re-screenshot at 2× | ~67 | You (or point me at each URL and I'll note the exact state) |
| 🔒 Auth — logged-in re-capture or Figma | ~19 | You |
| 🏢 Internal — Figma export | ~27 | You |
| 📱 Kiosk / app / composite — Figma export | ~10 | You |
| 🖼️ Graphic — supply original | 3 | You |

**Fastest high-impact batch:** the 🌐 sets for **qpmc (15), grsia (8), clayton (8), surah (7), mehrab (7), joodeskan (6), qnl (6)** — 57 images from 7 sites whose public designs I've confirmed still match. A full-page screenshot extension at 2× DPR gets each one in a few minutes.

**Content bugs to fix at source first** (a fresh capture is wasted otherwise): gama TechCorp/oil-&-gas placeholder · mcit 072 vacancy lorem · qpmc 116 San Francisco map · manateq Vietnamese billing text · clayton 166 footer leftovers.
