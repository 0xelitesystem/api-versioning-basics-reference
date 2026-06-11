# Where to put the version

The two common places to expose a version are in the URL path, like `/v2/orders`, or in a request header, like `Accept: application/vnd.api.v2+json`. URL versioning is visible and simple; header versioning keeps URLs stable and treats the version as metadata. Both work, and the choice is mostly about whose convenience you optimize for.

## URL path versioning

Putting the version in the path, such as `/v1/users` or `/v2/users`, is the most widely used approach because it is obvious. Anyone can see the version by looking at the URL, it is trivial to test in a browser or with curl, and routing to the right code is straightforward. The tradeoff is philosophical: a strict reading of REST says the URL identifies a resource, and `/v1/users` and `/v2/users` are arguably the same resource at two versions, not two resources. In practice most teams accept that tradeoff for the clarity it gives.

## Header versioning

Header versioning sends the version in a request header, often a custom header or a structured `Accept` header using a vendor media type. The appeal is that the URL stays clean and stable, pointing at the resource itself, while the version travels as metadata about the representation. The cost is discoverability: the version is now invisible in the URL, harder to test casually, and easier for a caller to forget to set. Header versioning suits APIs with sophisticated clients and a strong commitment to REST purity.

## Query parameter and other variants

Some APIs version with a query parameter, like `/users?version=2`, which is easy but muddies the line between a version and an actual query filter. Others version per resource or per field rather than globally, evolving pieces independently. These exist and can be appropriate, but they add cognitive load. For most teams, a single global version in the URL path is the path of least surprise.

## Picking one and being consistent

The most important decision is not which scheme but that you pick one, document it, and apply it consistently across the whole API. A mix of path and header versioning, or versions that jump schemes between endpoints, confuses callers more than any single approach ever would. Choose based on your callers: URL versioning for broad, varied, casual consumers, header versioning for a controlled set of careful clients. Then make the choice predictable everywhere.
