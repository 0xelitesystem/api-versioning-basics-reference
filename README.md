# API Versioning Basics

A plain-language reference on versioning APIs: why versioning exists, how to expose versions, how to decide what counts as a breaking change, and how to retire old versions without stranding the people who depend on you. It covers URL versus header versioning, semantic versioning, breaking versus non-breaking changes, and deprecation and sunset policies.

## The core idea

API versioning is the practice of letting an API change over time without breaking the clients already calling it, by exposing distinct versions that callers can choose. The central rule is that a published contract should not change in ways that break existing callers; when you must make a breaking change, you ship it under a new version and leave the old one running. Versions are usually exposed in the URL path (`/v2/orders`) or in a request header, and the hard part is not the mechanism but deciding what is breaking, communicating deprecation early, and giving a clear sunset date.

## What is inside

- `01-why-version-apis.md` the problem versioning solves.
- `02-where-to-put-the-version.md` URL versus header approaches.
- `03-breaking-vs-non-breaking.md` what counts as a breaking change.
- `04-semver-for-apis.md` semantic versioning applied to APIs.
- `05-deprecation-and-sunset.md` retiring old versions responsibly.

## The stance

This reference treats versioning as a promise to your callers, not a technical formality. The goal is to evolve the API while honoring the contract people already built against, which means being conservative about breaking changes and generous with notice when you make them.

## License

MIT. Copyright 0xelitesystem 2026.
