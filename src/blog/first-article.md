---
title: Finding Security issues in web apps
banner: /img/security.jpeg
---

<h2>Secret way for Unprivileged user to see all Corporate Card transactions through a vulnerable api.</h2>
OWASP Category: IDOR <a href="https://portswigger.net/web-security/access-control/idor">IDOR OWASP </a>

There is a famous Expense reporting app for Corporates and Enterprises. It had an api
https://expense.company.com/api/v1/banks

that gives the list of banks associated to the particular organization. It also had a parameter called entity which was the gateway to the vulnerability that I found.

The typical value of the entity parameter was bank. I checked the same api with the param value card. It worked!! I successfully retried the list of card ids related to the Corporate account. Still one more way to complete the hack. We haven’t seen the list of transactions for the unprivileged the user like me.

I completely scanned the application for the particular api. With tired less analysis and hardwork I finally found the api.
https://expense.company.com/api/v1/transactions?account_id={card_id}
It gives me the list of corporate expenses that I was not supposed to view. That left the Company transactions exposed to simple staff user. Hard work paid off in form of bounty.