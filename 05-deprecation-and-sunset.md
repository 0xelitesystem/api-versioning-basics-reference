# Deprecation and sunset

Deprecation is announcing that a version or endpoint is on its way out; sunset is the date it actually stops working. Adding versions is easy, but every live version costs maintenance, so a healthy API also retires old ones, which you do by giving callers clear, early notice and a firm but fair deadline. Retiring versions badly is one of the fastest ways to lose caller trust.

## Deprecate before you remove

Deprecation marks something as still working but discouraged, with removal coming later. You never just delete a live version; you first mark it deprecated, announce it, and let callers migrate. Communicate it in multiple channels: changelogs, documentation banners, email to known consumers, and machine readable signals like a `Deprecation` header or a `Sunset` header carrying the planned shutdown date. The goal is that no caller is surprised, because surprise is what turns a routine retirement into an outage and a support storm.

## Give a real timeline

A deprecation without a deadline tends to be ignored forever, so deprecation should come with a sunset date that is firm enough to be taken seriously and far enough out to be fair. The right window depends on your callers: public APIs with mobile clients often give six to twelve months or more, while internal APIs can move faster. Whatever you choose, state it plainly, hold to it, and remind callers as the date approaches. A clear deadline respects callers more than a vague intention does.

## Make migration easy

Callers are more likely to move on time if you make moving easy. Provide a migration guide that maps old behavior to new, call out exactly what changed and why, and where possible offer overlap where both versions run so callers can switch incrementally rather than all at once. The harder you make migration, the more callers will cling to the old version past its deadline, and the more pressure you will feel to extend it. Smoothing the path serves both sides.

## Sunset with care

When the sunset date arrives, retire the old version deliberately rather than abruptly. Consider monitoring remaining traffic so you know who is still affected, and reaching out to stragglers before you pull the plug. Some teams use a brownout, briefly returning errors before the final shutdown, to wake up callers who ignored every notice. The principle throughout is that retiring a version is a promise kept on a schedule, not a surprise sprung on people, and handling it with care is what lets you keep evolving without burning the trust your API depends on.
