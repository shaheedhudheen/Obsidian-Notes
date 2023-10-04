### What is an API?

In order to have consistent ways of interacting with data, a back-end will often include a _web API_.

API stands for **A**pplication **P**rogramming **I**nterface and can mean a lot of different things,

 a _web API_ is a collection of predefined ways of, or rules for, interacting with a web application’s data, often through an HTTP request-response cycle.

Unlike the HTTP [requests](https://www.codecademy.com/resources/docs/javascript/requests) a client makes when a user navigates to a website’s URL,

this type of ***request*** indicates how it would like to interact with a web application’s data *(create new data, read existing data, update existing data, or delete existing data)*, and it receives some data back as a ***response***.

Eg:

When a user presses the button to submit an order,
that will trigger a request to send them to a different view of the website,
an order confirmation page,
but an additional request will be triggered from the front-end,
unseen by the user, to the web API so that the database can be updated with the information from the order.

![[Node_5v2__Updated_1.gif]]
