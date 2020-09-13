# Introduction

Welcome to Carebnb API!

The Carebnb API is organized around [REST](https://en.wikipedia.org/wiki/Representational_state_transfer).
Our API has predictable resource-oriented URLs, accepts [form-encoded](https://en.wikipedia.org/wiki/POST_(HTTP)#Use_for_submitting_web_forms) request bodies, returns [JSON-encoded](http://www.json.org/) responses, and uses standard HTTP response codes, authentication, and verbs.

## Access

To have access to our API, you will need partner credentials.
These credentials are granted to hosting businesses that use our automation services.

If you're not a partner yet, but see yourself as a good candidate, please contact us through the email [host@carebnb.app](mailto:host@carebnb.app)

## Lifecycle

We integrate with each of our clients and partners uniquely.
Our team of experts knows each system has its particularity.
We can mold events triggering and callback calls,
depending on each integrated system,
to better attend to our clients and partners specific needs.

Our system is pluggable to an already existing system in two different ways:

* Subscribe to Kafka topics (preferable);
* Call rest API callbacks.

### Event detection / Carebnb triggering

Carebnb relies on 5 different inputs.
Our clients and partners must trigger them all.

1. New reservation occurs.
2. A reservation is updated.
3. A reservation is cancelled.
4. A guest sends a message to a host.
5. A host sends a message to a guest.

<aside class="notice">
  Any of these events must be triggered from the client or partner side.
</aside>

### Carebnb calls callbacks

After any of these events triggers carebnb,
our system will immediately returns a response saying it received and validated the call.
The real return, with relevant response data is given by each of our services individually.

For example, let's consider one of our clients or partners got a new reservation from one of its hosts...

1. Guest books a place
  * If is from a partner, their 3rd party system triggers Carebnb, passing a json object with the reservation details.
  * If is from a client, Airbnb triggers Carebnb directly.
2. Carebnb detects what services that specific property is set to work with. Lets say it uses "**Automatic check in check out**" and "**Custom access codes**" services.
3. Each Carebnb service handle this new reservation.
  * **Automatic check in check out** sends o introduction message right away.
  * **Custom access codes** creates temporary access codes and send them to the guest.
4. Each Carebnb service sends callback feedbacks.
  * If is to a partner, will call a rest API or write to a Kafka topic.
  * If is to a client, will email and report to our report solution.

<aside class="notice">
  Summary: Carebnb is triggered by your 3rd party system, and returns to a rest API or Kafka topic afterwards. 
</aside>