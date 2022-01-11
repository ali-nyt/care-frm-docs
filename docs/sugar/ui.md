---
layout: default
title: Sugar UI
parent: Sugar
nav_order: 5
permalink: /sugar/ui
---

# Sugar UI

---

**Issue:** Agent is seeing an outdated Sugar UI prod version.
{: .fs-5 }

| Action/Solution | Details |
|---|---|
| Have agent clear session data, local storage and file cache | Can confirm by asking for the version number in the Sugar footer, it should match the latest commit sha. |

<small> Tip: to clear session data and local storage:
```
1. Open the Google Chrome Console by pressing F12 key.
2. Select “Application” in the console’s top menu.
3. Select “Local Storage” in the console’s left menu.
4. Right click your site(s) and click clear to delete the local storage and session data.
```

<small> To clear out the file cache, press Control+Shift+Del in Chrome should open a menu. Clear "Cached images and files".

---

**Issue:** Sugar frontend is missing styles or label text
{: .fs-5 }

| Action/Solution | Details |
|---|---|
| Inside Sugar go to Administration -> Repair (System Section) -> Click on Quick Repair and Rebuild (Click on Rebuild in that page). Wait until the script is complete, then go Back and refresh the page | |

---
