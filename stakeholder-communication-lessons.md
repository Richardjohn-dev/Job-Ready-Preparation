# Stakeholder Communication Lessons

Current as of 2026-05-30.

## Main Lesson

The problem was not that you were wrong to estimate honestly.

The problem was that the work was invisible.

When you work alone and nobody reviews the code, stakeholders only see:

> "Add another integration."

They do not see:

- Authentication differences.
- Permission model differences.
- Folder structure differences.
- Metadata/schema differences.
- Upload/download API differences.
- Token/session behavior.
- Rate limits.
- Late-discovered transfer behavior, such as chunked downloads.
- Provider bugs or undocumented behavior.
- UI configuration changes.
- Background job/retry/logging changes.
- Testing against real accounts.
- Regression risk to existing integrations.

So an honest two-month estimate can sound inflated unless the hidden work is made visible.

## Better Framing

Weak:

> This integration will take two months because every provider has quirks.

Stronger:

> The reusable pipeline is already there, but this provider still needs discovery and implementation across auth, permissions, folder model, metadata mapping, upload/download behavior, UI configuration, background processing, failure handling, and real-account testing. Based on previous providers, I estimate around two months unless the API is simpler than expected. I would also keep a risk buffer because some provider behavior only appears late, when we test real files, real folders, and real permissions.

Concrete example:

> During the Autodesk integration, a late-stage discovery was that drawings were downloaded in chunks rather than as a simple file download. That added several extra implementation steps near the end. There were also folder-level permission checks when creating destination folders. Those risks were not obvious from "implement Autodesk" at the start.

## Estimate Breakdown Template

Use this before giving a timeline:

```text
Goal:
Add [provider] support for [Form Events / Synchronization / both].

Reusable:
- Existing integration pipeline
- Existing mapping model
- Existing background queue/status patterns

Provider-specific unknowns:
- Authentication/session model
- Permission model
- Folder model
- Metadata schema
- Upload/download behavior
- Chunked/streamed transfer behavior
- Per-folder permission behavior
- Rate limits/API constraints
- Error responses/failure handling
- Late behavior only visible with real provider data

Implementation work:
- API client/service
- Credential setup
- Mapping/config UI
- Vendor strategy/handler
- Metadata/folder path mapping
- Background task integration
- Logs/status/results

Validation:
- Real account testing
- Permission edge cases
- Folder creation under different permission levels
- Large file/bulk sync cases
- Chunked/streamed download cases
- Failed upload/download cases
- Regression check against existing vendors

Estimate:
- Best case:
- Expected:
- Risk case:
- Explicit discovery/risk buffer:
```

## How To Say It To A Developer Manager

> If this were just another implementation of a stable interface, it would be faster. The reason I am estimating longer is that the interface itself tends to change when a new provider exposes a different auth model, folder model, permission model, metadata schema, transfer model, or failure mode. Some work is reusable, but each provider has historically forced at least some architecture adjustment, and some issues only appear once we test real files and real account permissions.

## How To Say It To A Business Stakeholder

> The visible feature is "add provider X", but the real work is making sure files land in the right place, with the right metadata, under the right permissions, and that failures are visible and recoverable. That is what protects customer workflows from silent document loss or bad organization.

## Personal Lesson

Your honesty was not the issue.

The upgrade is:

- Do not give only a duration.
- Give the decomposition.
- Separate known work from unknown risk.
- Show what is reusable versus provider-specific.
- Explain what failure would look like if rushed.
- Include a contingency for late provider discoveries.
- Offer scope cuts: "Form Events first, Synchronization later" or "basic upload first, metadata/folder automation second."

## Interview Version

> I learned that solo ownership requires making invisible engineering work visible. In DataBridge, stakeholders could see "add another provider," but not the provider-specific auth, permissions, metadata, folder model, transfer behavior, testing, and reliability work underneath. For example, during the Autodesk integration, we discovered late that drawing downloads required chunked handling and extra folder-permission checks. Over time I learned to explain estimates by decomposing the reusable pipeline work from the provider-specific risk and explicitly calling out discovery buffer.
