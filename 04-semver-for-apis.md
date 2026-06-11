# Semantic versioning for APIs

Semantic versioning, or semver, expresses a version as MAJOR.MINOR.PATCH, where major means breaking changes, minor means backward compatible additions, and patch means backward compatible fixes. It gives callers a precise, predictable signal about what a version bump means for their code. For APIs, the major number is the one that maps to the versioning you expose to callers.

## The three numbers

In semver, the three parts each carry meaning. You raise the patch number for a backward compatible bug fix, the one that changes nothing a caller depends on except that something now works correctly. You raise the minor number for a backward compatible addition, like a new optional field or endpoint. You raise the major number for a breaking change, the kind that requires callers to update. Reading 2.4.1 to 2.5.0, a caller knows something was added but nothing broke; reading 2.5.0 to 3.0.0, they know to brace for breaks.

## What maps to the URL

For web APIs, the version a caller picks, like `/v2/`, almost always corresponds to the major version only. Minor and patch changes are backward compatible by definition, so callers do not need to opt into them; you ship them within the existing major version and everyone benefits. This is why you see `/v1` and `/v2` but rarely `/v1.4.2`. The major number is the contract boundary; the rest is internal evolution you communicate through changelogs rather than new URLs.

## Why the discipline matters

The value of semver is the promise it encodes. When you honor it, callers can upgrade minor and patch versions confidently and plan deliberately for major ones. When you violate it, slipping a breaking change into a minor bump, you destroy the very predictability that makes the scheme useful, and callers learn they cannot trust your numbers. The discipline is social as much as technical: semver works only if you actually hold the line on what each number is allowed to do.

## Pre-release and stability signals

Semver also has a pre-release notion, like 2.0.0-beta, that signals a version is not yet stable and may still change in breaking ways before release. This is a useful honesty marker for an API you are still shaping: it tells eager adopters they can try it but should not depend on it yet. Once you drop the pre-release tag, you are committing to the contract. Using these signals clearly lets you iterate in the open without surprising the people who build against you.
