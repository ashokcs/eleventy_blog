---
title: Finding Security issues in web apps
banner: /img/security.jpeg
---

<h2>Unprivileged users were able to access the Corporate Card transactions.</h2>
OWASP Category: IDOR <a href="https://portswigger.net/web-security/access-control/idor">IDOR OWASP </a>

Its a famous Expense reporting app for Corporates and Enterprises. Which had an api https://exp.company.com/api/v1/banks that gives the list of integrated payment banks associated to the particular company. It also has a query string called entity which was the gateway to the vulnerability that I found.

The general value of the entity query string was bank. I ensured the same api with the query striing value card. I nailed it!! I  fetched the list of card ids related to the Corporate account successfully. Still one more step to complete the hacking. We are yet to see the list of transactions for the unprivileged access the user like me.

I thoroughly scanned the app access for the particular api. With tired less analysis and hardwork I finally found the api.
https://exp.company.com/api/v1/trans?account_id={card_id}
It shows me the list of expenses that I were not supposed to view, which means it left the Company transactions access to simple staff user. My hard work paid off in form of big bounty.