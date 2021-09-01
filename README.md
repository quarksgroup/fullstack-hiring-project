# Fullstack Hiring Project
Interviews suck. It's why we prefer a more practical approach. We try to immerse you in the kind of work we think you will be doing as early as possible But we also have to balance with how much time we have to spend on each candidate. It's hard to evaluate which candidates are really interested in the role so we have had that rather unfortunate but necessary first challenge which was rather random given the kind of work we do.

## Our Stack

It's probably a dangerous oversimplification but this role mainly involves fetching data from a bunch of APIs and displaying it neatly in the browser. Most of our work revolves around our main product [paypack](https://payment.paypack.rw/) and since it's proabably going to affect everything you do we should describe it's stack first and foremost.

You should probably [register](https://payment.paypack.rw/register) and take it for a test drive. Paypack is Rwanda's first developer focused payment platform. You have heard all about Mobile Money and all the good it brings. Take that and add all the good the internet brings and you have paypack. We want to make as easy as possible to integrate Mobile Money payment into existing/new internet services. 

This is mostly me advocating but we believe first and formost into simplicity. Paypack is just 2 layers that may or may not be expanded:

1. First layer: a statically compiled binary that serves both our frontend and backend. Yes we love our monoliths and we don't see much need to destructre things as of now. For this we chose [Go](https://golang.org/) specifically because it compiles to a single artefact that we can move wherever. And go1.16 brought static assets and since then we have been able to deploy not go binary and html/css/javascript assets but a go binary that contains the compiled results of `npm build`.
2. Middleware: We go evern further to facilidate the deployment process by creating a Dockerfile that can be deployed on all Container platforms from Google Apps to Heroku going through fly.io which is where we live now.
3. Second layer: We've made sure to make our application layer stateless following the famous [12 factor methodology](https://12factor.net/). And our data lives in a postgres database. The database currently also serves as our event system but that may change soon. Somewhere in the middle lives a very small redis deployment that stores frequently read dataa such as user sessions.
4. Frontend: Now, yes our frontend lives in a go binary but during development you will only meet is as a very lightweight  [vue.js](https://vuejs.org/) Single Page Application. Yet again in the spirit of keeping our stack in a single brain without 100 of documents explaining what the hell is going on we chose vue for everything. And we do you use [SASS](https://sass-lang.com/) for our CSS. But don't worry about that.

For this role you will be dealing directly with the last layer and calling internal API but also sometimes external ones but we try to minimize scattered external calls by abstracting them with our own internal APIs.

For maximum effort you should probably do both challanges starting with the first one.

## First Challenge: Product pages
The simple idea behind product pages is to eliminate the need for bloated e-commerse websites. With product pages a merchant signs up and and starts creating custom pages for their products and different marketing media like short videos and photos. And at checkout their client will pay with mobile money sending cash to the merchant's paypack account. For reference checkkout https://paystack.com/commerce and 

### Requirements

- [ ] A registration and a login page.
- [ ] Add new product page.
- [ ] Product presentation page. Chedckout this example https://paystack.com/buy/onyx-polish .
- [ ] Create a paypack account for new users(behind the scenes).
- [ ] Display their sales and transactions.
- [ ] Paypack branding must somehow appear somewhere.
- [ ] Should be lightweight(load in less than 500ms).
- [ ] We insist beauty lies in minimalism.

## Second Challenge: Checkout page
The second challenge is rather simple and could be included as a requirement into the first one. For reference https://stripe.com/docs/payments/checkout and https://flutterwave.com/gb/checkout should be enough.

- [ ] Paypack branding must be visible somewhere but don't let that limit your creativity.
- [ ] Payment options avaialble should be Airtel and MTN mobile money.
- [ ] Should be lightweight(load in less than 200ms)
- [ ] Keep it simple, remember a good UX shouldn't be distractive. I came to checkout, not view cat videos.


## Resources

Paypack api documentation: https://payment.paypack.rw/api
