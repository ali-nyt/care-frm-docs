---
layout: default
title: Account and Subscription
parent: Sugar
nav_order: 1
permalink: /sugar/account-subscription
---

# Account and Subscription Issues

---

**Issue:** When attempting to save or cancel a customer, sending a request to Plato to cancel the subscription, free or paid, can fail with a ```"Precondition Failed"``` error
{: .fs-5 }

| Action/Solution | Details |
|---|---|
| The most common case for receiving this error message is when a new digital subscription that is attempting to be created has overlapping entitlements with an existing digital subscription. In some cases, the digital account can be in a frozen state, which Sugar will reflect with the message "Updating credit card info is currently frozen". The digital account will need to be unfrozen first, then the save or cancel can occur. | |

Needs more detail
{: .label .label-yellow .m-0 }

---

**Issue:** Customers accidentally purchased more than one gift subscription
{: .fs-5 }

| Action/Solution | Details |
|---|---|
| Refund the sub (tag The Hive so they can help us with this) | Alterinatively, there is an [API solution](https://docs.google.com/document/d/1_zYZ6Mgl12U-n5M6FkdTi8ULBMjOJTWMEcG77VIoPAk/edit?usp=sharing) |

---

**Issue:** Unable to process product change or cancellation on a digital accounts - receiving the following error message: ```"DGT Subscription ID is required"```
{: .fs-5 }

| Action/Solution | Details |
|---|---|
| Search for the error string in sugar codebase - indicates that this account was already canceled. | |

---

**Issue:** Agent unable to process an order for a separate entitlement (Crosswords) with current active subscription, due to Sugar not having any products available.
{: .fs-5 }

| Action/Solution | Details |
|---|---|
| Either the customer can be product switched into an ADA_CR bundle from their XPASS sub or a standalone paid Crosswords offer needs added. This is something the agents can do. | |

---

**Issue:** Updating an email in general (on a regi)
{: .fs-5 }

| Action/Solution | Details |
|---|---|
| Use the ```https://ce-lire-prd.dv.nyt.net/int/lire/account/email/set-address``` endpoint with the ```regiID```, ```emailAddress```, and ```source``` in the body | |

---

**Issue:** "User with such email already exists" when trying to use LIRE to update an .edu (or any) email address
{: .fs-5 }

| Action/Solution | Details |
|---|---|
| If the existing account with the target email address does not have an active subscription: Use the same LIRE endpoint (```ce-lire-prd.dv.nyt.net/int/lire/account/email/set-address``` with the regiID, emailAddress, and source in the body), change the email address for the old account that does not have an active subscription to something else (```disabled-email-<random-10digit-number>@nytimes.ccd.nytimes.com```). This should resolve the error when attempting to use the correct email address for the active account. If the existing account with the target email address DOES have an active subscription: tag the hive and ask how they want us to handle it | |

---

**Issue:** HD Premium account was cancelled due to the suspension with no restart date. When restarted, the DGT is no longer Premium Access
{: .fs-5 }

| Action/Solution | Details |
|---|---|
| Check with Aristo or Plato team to look into this. This can happen when the customer goes into Non-Payment (NN) stop state for HD subscription. If HD subs is NN stopped, then corresponding premium would be auto cancelled." | |

---
