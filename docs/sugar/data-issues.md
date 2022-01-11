---
layout: default
title: Sugar Data Issues
parent: Sugar
nav_order: 3
permalink: /sugar/data-issues
---

# Sugar Data Issues

---

**Issue:** Unable to grant account free digital access
{: .fs-5 }

| Action/Solution | Details |
|---|---|
| Remove Inactive Sublink ([instructions here](https://docs.google.com/document/d/16kEVyP4S2ZqN4sIy602ziFsHmeK22H77qPGEFeSwJ5Y/edit?usp=sharing)) | This issue is typically reported by agents unable to grant the free digital access / Free ADA link is broken / Grant Free Digital Access SR is missing in Sugar, etc. |

---

**Issue:** Contact email doesn't match the regi email
{: .fs-5 }

| Action/Solution | Details |
|---|---|
| Update ```regi_email``` in the Sugar DB ([instructions here](https://docs.google.com/document/d/1lAikpli7PLVCR2l0RPPuhyIHw7JFHeNWufwv2CWSG4c/edit?usp=sharing)) | The problem is that if there aren’t any active subscriptions on an account in Sugar and Lire has an updated email address for a regi, Sugar won’t process the updated email address. So, to fix this, we have to go into the Sugar PRD database to update the ‘regi_email’ ourselves. |

---

**Issue:** Unable to grant account free digital access
{: .fs-5 }

| Action/Solution | Details |
|---|---|
| Cannot change email because the new email is attached to another account | Tag care-hive to have them unlink the old and new email addresses to the two accounts. |

---

**Issue:** Account needs to be changed to tax exempt
{: .fs-5 }

| Action/Solution | Details |
|---|---|
| Historically, this has been done directly in the database, can now run [this script](https://docs.google.com/document/d/1D4Dn_anvFSSvC73brsRMzOBDSH94q7SfZW9z1k9NTb4/edit?usp=sharing) via Postman |  |

---

**Issue:** Guaranteed Delivery Time (GDT) and recover times are shown in UTC and not local time
{: .fs-5 }

| Action/Solution | Details |
|---|---|
| No action - The delivery address is not identifiable in SmartyStreets, so we do not get the time zone offset. We default to UTC in those cases. | [Example issue in Slack](https://nytimes.slack.com/archives/C7CKS8NAW/p1532969973000305) |

---

Needs more detail
{: .label .label-yellow .m-0 }

**Issue:** Account number cannot be found in Aristo, but still has "TempStop" status in Sugar, causing a loading error.
{: .fs-5 }

| Action/Solution | Details |
|---|---|
| Change status to "Purged" and refresh the contact. If this doesn't help - mark this record as deleted and refresh the contact as well." | |

---

**Issue:** Cannot find subscription in Sugar, need to import a contact
{: .fs-5 }

| Action/Solution | Details |
|---|---|
| Manually introduce a contact into Sugar [(instructions here](https://docs.google.com/document/d/1Zw0q4vKTN_xUUxH7pGf-45JDNQ2gp0dkktTDxCXBqrc/edit?usp=sharing) |  An example of when we use this is if someone signs up using an email that is not detected as valid in the Sugar UI, such as one with additional characters <example@gmail.com>, the account will not show up in Sugar UI and we need to introduce the contact into Sugar manually rather than through the global search. |

---

**Issue:** Subscriptions missing from a Sugar Contact
{: .fs-5 }

| Action/Solution | Details |
|---|---|
| Link the missing subs in the Sugar PRD database using the script below | |

Needs more detail
{: .label .label-yellow }


```sql
"UPDATE nyt_dgt_subscriptions SET nyt_dgt_contact_id = '<nyt_dgt_contact_id>' WHERE id IN (
 <nyt_dgt_subscriptions_ids>
)

<nyt_dgt_contact_id>
SELECT id FROM nyt_dgt_contacts WHERE regi_id='7753829'

<nyt_dgt_subscriptions_ids>
SELECT id FROM nyt_dgt_subscriptions WHERE contacts_subscriptions_nyt_id IN (
 SELECT id FROM contacts_subscriptions_nyt WHERE contacts_nyt_id = (
  SELECT contacts_nyt_id FROM nyt_dgt_contacts WHERE regi_id='7753829'
 )
)"
```
