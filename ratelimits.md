[//]: # (Title: Ratelimits - Nekosia API Docs)
[//]: # (Description: Learn about the rate limits for Nekosia and how they work. Find out what happens if you exceed the limits and how to avoid it.)
[//]: # (Tags: ratelimits, nekosia api ratelimits, nekosia api docs ratelimits, nekosia api rate limits, nekosia api rate limiting)
[//]: # (Canonical: ratelimits)
[//]: # (Creation date: 2024-07-29)
[//]: # (Last update: 2024-08-25)
[//]: # (Contributors: Sefinek)

# Rate Limits {#ratelimits}
The Nekosia API applies rate limits to ensure the stability and security of the services.
These limits are designed to prevent server overload and ensure equal access to resources for all users.
Below are the detailed limits for different parts of the service.

## nekosia.cat {#nekosia-cat}
- **Main**: A maximum of `96 requests` to the server within `140 seconds`.
- **Comments**: A maximum of `3 requests` to the server within `30 seconds`.

## api.nekosia.cat {#api-nekosia-cat}
- A maximum of `320 requests` to the server within `5 minutes`.

## cdn.nekosia.cat {#cdn-nekosia-cat}
- A maximum of `620 requests` to the server within `6 minutes`.

# Cloudflare Rate Limits {#cloudflare-ratelimits}
We use Cloudflare to ensure the security and stability of our services.
Therefore, Cloudflare may apply its own request limits.
If these limits are exceeded, the user will receive an HTTP status code 429.

# HTTP 429 Response {#http-429}
If the rate limits are exceeded, the server will return an `HTTP 429` response, which means `Too Many Requests`.

# What Next? {#what-next}
Hmm... So, what now...

## Consequences of Exceeding Limits {#consequences}
Exceeding the limits results in temporary blocking of access to the API for the user or server from which the request originated.
The block may last from a few minutes to a few hours, depending on the severity of the limit violation.
In the case of repeated violations, the user may be permanently blocked.
Such actions will be treated as an attempt to overload the server or a DDoS attack. Attack incidents will be reported to [abuseip.com](https://www.abuseip.com).

## Contact and Support {#contact-support}
If you have any questions or issues related to rate limits, contact us by sending an email to support@nekosia.cat.

## Rate Limit Changes {#rate-limit-changes}
We recommend regularly checking the API documentation, as limits may sometimes be changed by the team.
