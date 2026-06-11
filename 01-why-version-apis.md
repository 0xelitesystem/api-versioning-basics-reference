# Why version APIs

You version an API so it can change over time without breaking the clients already calling it. Once another team or another company writes code against your endpoints, that code depends on the exact shape of your responses and the exact behavior of your requests. Versioning gives you a way to ship changes while leaving the existing contract intact for everyone who relied on it.

## The contract problem

An API is a contract. When a client sends a request, it expects a specific response shape, specific field names, specific status codes, and specific behavior. The moment you rename a field, remove one, change a type, or alter what an endpoint does, you risk breaking every client coded against the old behavior. You usually cannot coordinate a synchronized update with all of them, because you often do not control or even know who they are.

## Why you cannot just change it

The naive instinct is to edit the endpoint in place and tell callers to update. This fails at any real scale. Clients deploy on their own schedules, some are mobile apps shipped to users who update slowly or never, and some integrations are maintained by people who left long ago. A change that looks small to you, like dropping an unused field, can crash a parser somewhere downstream. Versioning lets old clients keep hitting old behavior while new clients opt into the new one.

## What versioning buys you

Versioning buys you the freedom to evolve. You can introduce a redesigned response, a cleaner resource model, or a fixed mistake under a new version, and roll it out without a flag day where everyone must switch at once. It also buys you honesty with your callers: a version number is a clear marker of what they are building against and a signal of when they will need to move. The cost is real, since every live version is something you must keep running and supporting, which is why good versioning is also about retiring old versions, not just adding new ones.

## When you do not need it yet

If your API has exactly one internal caller that you deploy together, you may not need formal versioning at all, because you can change both sides in lockstep. Versioning earns its complexity the moment callers and producers deploy independently. Knowing where you are on that line keeps you from adding ceremony too early or, more dangerously, skipping it once you genuinely have external dependents.
