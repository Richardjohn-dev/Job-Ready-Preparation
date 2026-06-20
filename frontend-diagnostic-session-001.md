# Frontend Diagnostic Session 001

Status: Completed

- Date: 2026-06-19 to 2026-06-20
- Project: RefineBridge
- Repository inspected read-only: `F:\Projects\Repos\Private\Scraper-To-CRM`
- Target role: Backend-leaning .NET/full-stack product engineer with Nuxt/Vue capability
- Mode: Live frontend diagnostic with repository verification
- Format: One question at a time

## Protocol

Questions were labelled as one of:

- Historical implementation
- Hypothetical design
- Retrospective
- Code-reading/debugging

Scoring dimensions were kept separate:

1. Interview answer quality: clarity, completeness, and concision.
2. Frontend engineering judgment: concepts, decisions, proportionality, and tradeoffs.
3. Project-specific recall: categorical verification only, except during the explicitly labelled code-reading task.

Implementation drift was treated as a project-reacclimation gap, not a frontend-knowledge failure. Missing file-path recall was not tested or scored.

## Repository Evidence Used

- `src/Frontend/nuxt.config.ts`: Nuxt 4 application composed from feature-oriented layers.
- `src/Frontend/app/middleware/auth.global.ts`: layout assignment, protected routes, role checks, and early-access routing.
- `src/Frontend/app/layouts/dashboard.vue`: authenticated shell, navigation, loading fallback, account/admin surfaces.
- `src/Frontend/layers/core/composables/useApiFetch.ts`: typed `ApiResult<T>` API wrapper, shared errors, retry handling, and `401` refresh flow.
- `src/Frontend/layers/auth/stores/authStore.ts`: session, roles, account/plan, credits, and freshness state.
- `src/Frontend/layers/bridges/pages/bridges/index.vue`: import-flow loading, explicit empty states, errors, local refs, and clickable cards.
- `src/Frontend/layers/bridges/components/bridge-definition/BridgeCreationModal.vue`: multi-step form, parent-owned state, computed gates, connection checks, and server error display.
- `src/Frontend/layers/bridges/stores/bridgeTaskRealtimeStore.ts`: feature-level realtime task/run state.
- Frontend test inventory: 70 `*.spec.ts` files found; no end-to-end framework visible in `package.json`.

No `.env` contents, credentials, customer data, private account details, or live URLs were inspected or recorded.

## Questions, Raw Answers, And Scores

### Q1 — Frontend overview

Type: Historical implementation

Question:

> Walk me through RefineBridge's frontend at a high level. What are its main user workflows, how is the Nuxt application organized conceptually, and how do you decide what belongs in a page, feature component, or shared component?

Raw answer:

> At a high level from memory, I tried to architect things in terms of features / slices and tried to best match the backend. I learned about Nuxt layers and thought this was a good fit to keep things in separate sections in the project. If it was a destination or something a user in the UI would navigate to in the browser, e.g. going from a dashboard to a detail page, these go in separate `.vue` pages. As pages grew, things would get separated out into components in logical folder positions within their layers.

- Interview answer quality: 2/4
- Frontend engineering judgment: 2/4
- Project-specific recall: Broadly verified.
- Notes: Correct feature/page/component concepts; main workflows, shared-component boundary, and tradeoffs were initially omitted.

Follow-up raw answer:

> The first workflow is logging into the SPA. Before every route I believe we were checking cookie access which queries the backend to check the auth is valid. After logging in, the first screen would have been the integrations table, where you can see from a higher level the different integrations created, or create a new one. From the grid you can navigate to the different areas which are grouped by the integration ID, e.g. event mappings or synchronization mappings.

- Interview answer quality: 2/4
- Frontend engineering judgment: 2/4
- Project-specific recall: Cookie/session concept verified; current entry/list details partly outdated. Treated as reacclimation, not lack of frontend knowledge.

### Q2 — Data fetching and state

Type: Retrospective

Question:

> For an import-flow listing page, how would you separate API data, global application state, feature state, local UI state, and URL state? Explain when you would use `useAsyncData`, a composable, Pinia, component refs, or route query parameters.

Raw answer:

> API data used a shared composable for most backend requests, so requests, responses, and errors could be handled consistently. Global state used separate, mostly single-purpose stores such as auth and domain. Feature stores tracked things such as job state and SignalR updates. I was unsure what feature state and URL state meant. Local UI state was often described as page-specific Pinia state. The consistent pattern was page -> component -> feature-specific composable -> API composable, with the composable updating its store. Pages should not update stores directly.

Clarification supplied during the session:

> We did lots in component refs in the actual page, with computed properties for dynamic values and logic. Tabs and filters were mixed between parameters and refs. This was Vue 2.

- Interview answer quality: 2/4
- Frontend engineering judgment: 2/4
- Project-specific recall: Shared API client, dedicated stores, feature composables, SignalR state, and extensive local refs verified. `useAsyncData` is used selectively. Current code also uses query parameters for shareable tab and workflow state.
- Notes: Needs a cleaner distinction between server data, global durable state, feature coordination state, ephemeral component state, and shareable URL state.

### Q3 — Forms and validation

Type: Historical implementation

Question:

> How would you design validation for a multi-step import-flow form? Cover field validation, cross-field rules, server validation, preserving progress between steps, submission errors, and preventing duplicate submissions.

Raw answer:

> I built custom logic in logical groups, for example `step1Valid` and `step2Valid`, with branching computed properties. Granular forms handled required fields, lengths, and selections, then emitted whether the step was valid to the parent. Separate step components could use refs, while the parent held the overall object submitted to the backend. UI validation prevented proceeding until required fields were completed. Duplicate submissions were checked using a unique integration title.

- Interview answer quality: 2/4
- Frontend engineering judgment: 2/4
- Project-specific recall: Multi-step forms, parent refs, computed gates, connection checks, and displayed server errors verified. Duplicate-by-title handling was not verified.
- Notes: Strong computed-rule decomposition. Client validation cannot replace server validation. The original operational constraint was one trusted internal operator, so full idempotency infrastructure would have been disproportionate; a pending guard plus backend uniqueness could be sufficient for that context.

Timeout follow-up raw answer:

> API errors were displayed in the UI. If resubmitting and the form data remained, it should be possible. If the backend received the object and the integration title was unique, it should work. Some integrations required additional steps and might need restarting, such as preserving an external-provider auth token.

Operational clarification:

> This was mostly managed internally with one logged-in person setting up integrations. Idempotency was not considered necessary for that use case.

- Interview answer quality: 2/4 after operational context was stated.
- Frontend engineering judgment: 2/4. The tradeoff was proportionate for a single trusted operator; timeout recovery remained implicit.
- Project-specific recall: UI error display and retained parent form state verified. External-provider token detail treated as credible prior implementation context whose current-repository relevance was not verified.

### Q4 — Loading, error, empty, and stale states

Type: Hypothetical design

Question:

> An import-flow list loads from an API and later receives realtime updates. Describe proportionate UI handling for initial loading, empty results, request failure, background refresh, stale data, and realtime disconnection. How should users recover from each?

Raw answer:

> Initial loading can use a boolean set before and after the request. API calls return `Result<T>` and callers check success or failure. An empty list could render nothing. Request failures go through the shared API composable, which handles known status codes, returns errors, or emits an error event into a global store. Potentially stale data can have a refresh button. SignalR connection state can be watched and reconnection triggered.

- Interview answer quality: 2/4
- Frontend engineering judgment: 2/4
- Project comparison: Typed results, centralized API errors, local loading, explicit empty states, and realtime state are present.
- Notes: Page-specific loading should normally remain local. Empty results need an explicit explanation/action. Background refresh should preserve existing data and distinguish stale-but-usable from unavailable.

Follow-up raw answer:

> Known backend error codes could be handled separately. Global failures were shown globally. If the backend was not responding, an authentication check could run and log the user out if that also failed.

- Interview answer quality: 1/4
- Frontend engineering judgment: 2/4
- Project comparison: Current code refreshes authentication on `401`; general backend failures return typed errors and do not automatically log the user out.
- Notes: Network failure must not imply authentication failure. Keep valid older data visible, show a non-blocking warning and retry, and reserve logout for an actual authentication signal.

### Q5 — Authentication and account boundaries

Type: Historical implementation

Question:

> How did authentication, protected routes, roles, and account boundaries work in the frontend you built? Distinguish frontend user-experience enforcement from backend security enforcement.

Raw answer:

> The backend served HTTP-only cookies with a JWT payload containing the user's role. At the time everything was admin. More roles could be checked through middleware guards. The backend used .NET Identity role checks and controller role attributes. Cookies were included with requests through the shared API composable. Frontend middleware controlled appropriate page access, while the backend attributes protected endpoints.

- Interview answer quality: 2/4
- Frontend engineering judgment: 3/4
- Project-specific recall: Cookie sessions, credentialed shared API access, route middleware, and Admin/Owner checks verified. “Everything was admin” describes an earlier phase.

Account-boundary follow-up raw answer:

> There was only one login and nobody owned integrations. Admin could log in and manage everything. If multi-user ownership were needed, an integration could have an `ownerUserId` and a service could return only integrations belonging to that user.

- Interview answer quality: 3/4
- Frontend engineering judgment: 2/4
- Project-specific recall: Credible earlier single-admin design. Current backend ownership enforcement was outside this frontend-only inspection.
- Notes: Multi-user isolation would require server-side scoping for every query, command, guessed identifier, and nested resource—not only list filtering.

### Q6 — TypeScript

Type: Retrospective

Question:

> How did you use TypeScript in Vue/Nuxt, where did it prevent real mistakes, and where did the code still weaken type safety? What would you improve now?

Raw answer:

> I did not use TypeScript in the Vue 2 project. I did not know how useful it was then. I have since used it extensively in my Nuxt 4/Vue 3 SaaS and would not build frontend code without it now. Coming from C#, the syntax and type safety pair well and make breaking changes easier to spot.

- Interview answer quality: 2/4
- Frontend engineering judgment: 2/4
- Project-specific recall: Current Nuxt 4/Vue 3 code uses TypeScript extensively; earlier Vue 2 project did not.

Follow-up raw answer:

> Property renames have exposed missed updates. Running real TypeScript builds also makes mistakes easier for LLM-assisted work to find. Incorrect Visual Studio/project settings once reported that code was fine when it was not, and I trusted that result. API composables use a stable `ApiResult<T>` matching the backend, but everything can compile while the runtime result or property names are still wrong.

- Interview answer quality: 3/4
- Frontend engineering judgment: 3/4
- Project-specific recall: Typed `ApiResult<T>` and a `nuxt typecheck` command verified.
- Notes: Good recognition that generic types express expectations but do not validate runtime payloads. Compiler settings and CI typechecks are part of the safety boundary.

### Q7 — Frontend testing

Type: Historical implementation

Question:

> What frontend testing did you actually use: unit, component, integration, end-to-end, or manual? What did you choose to test, what remained untested, and why?

Raw answer:

> This was a big weakness at the time. I did zero testing because it was not in my arsenal on that project. I have since learned and added unit tests, especially with LLM-assisted development, because core domain logic needs guardrails. Testing remains something I need to improve.

- Interview answer quality: 3/4
- Frontend engineering judgment: 2/4
- Project-specific recall: Current frontend contains 70 Vitest spec files. No end-to-end framework is visible in `package.json`.
- Notes: Honest baseline and real later progress. Still needs a deliberate unit/component/integration/E2E strategy and a repeatable full-suite command.

### Q8 — Accessibility

Type: Hypothetical design

Question:

> For a multi-step modal form and a clickable import-flow card grid, what accessibility concerns would you check? Cover keyboard use, focus, labels, errors, status changes, and screen readers.

Raw answer:

> Each step should show its own errors, such as required-field messages. The UI should make the next action visually obvious and disable invalid actions. Async-loaded fields could use a shake/emphasis animation so new content is noticed. Status changes should use clear colors, such as red for problems. Screen readers were not considered historically because one trusted admin used the application.

- Interview answer quality: 2/4
- Frontend engineering judgment: 1/4
- Project-specific recall: Current forms use labelled UI components. Current import-flow cards expose a keyboard/semantic gap.
- Notes: Visible validation and async feedback help. Color and motion must not be the only signals; reduced-motion preferences, focus management, keyboard operation, status announcements, and semantic controls remain gaps.

### Q9 — Interactive-card code reading

Type: Code-reading/debugging

Context shown before answering:

```vue
<UCard
  v-for="bridge in bridges"
  :key="bridge.id"
  class="cursor-pointer"
  @click="$router.push(`/bridges/${bridge.id}`)"
>
  ...
  <div @click.stop>
    <UDropdownMenu :items="bridgeMenuItems(bridge)">
      <UButton icon="i-lucide-ellipsis-vertical" />
    </UDropdownMenu>
  </div>
</UCard>
```

Question:

> Identify the main keyboard, semantic, and nested-interaction problems. How would you fix them without making the dropdown trigger navigate to the detail page?

Raw answer:

> There are two clicks, one on the outer `UCard` and one in the inner `div`. They could overlap, and I was unsure which would win. I was not familiar with `@click.stop`. I would reconsider the interaction and move navigation from the whole card to a dedicated header or clear button, leaving the dropdown as a separate control.

- Interview answer quality: 3/4
- Frontend engineering judgment: 2/4
- Repository code-reading: 2/4
- Notes: The proposed dedicated native link/button is sound. `@click.stop` stops propagation, so dropdown clicks do not reach the card handler. The main missed issue was that `UCard` plus `@click` is not inherently a focusable semantic link.

Keyboard follow-up raw answer:

> I was not sure how accessibility worked and assumed this meant a user without a mouse. I would show clear focus through an outline, color, or emphasis and aim for consistent navigation inside cards across the project. I considered a “step into” mechanism for the card's controls, but acknowledged this was not something I currently considered while coding.

- Interview answer quality: 3/4
- Frontend engineering judgment: 1/4
- Repository code-reading: 1/4
- Notes: Visible focus and consistency are useful. A custom “step into” interaction is unnecessary. Richard declined an immediate re-answer because it would test parroting, not retained understanding. Score intentionally unchanged.

Coaching reference — not yet demonstrated by Richard:

> Prefer a real `NuxtLink` or button for navigation so it is focusable and activates with standard keyboard behavior. Keep the dropdown trigger as a separate button and never nest it inside a link. Give both controls visible `:focus-visible` styles. The simplest design is a linked title or explicit “View details” action plus the independent dropdown; avoid making a non-semantic card imitate a link.

### Q10 — Feature-layer tradeoffs

Type: Retrospective

Question:

> Why did feature-oriented Nuxt layers fit RefineBridge, what problems did they solve, and what costs or complexity did they introduce? What would you keep or simplify today?

Raw answer:

> Layers gave the project a repeatable, consistent structure and broadly aligned the frontend with the backend modular-monolith/vertical-slice design. Authentication could stay within its module. Preventing boundaries from bleeding remained difficult. Explicit imports made dependencies more visible but more verbose. I would keep the structure because RefineBridge extends a reusable SaaS template and new features can be added as layers. Admin placement was less clear: central `/admin` versus feature-owned admin areas. This was manageable solo but needs consistent team rules.

- Interview answer quality: 3/4
- Frontend engineering judgment: 3/4
- Project-specific recall: Feature layers, backend alignment, and explicit cross-layer imports verified. Component auto-discovery remains configured, so “turned off auto imports” was partly outdated or imprecise.

Follow-up raw answer:

> A central admin layer makes sense for a distinct area such as `/admin/dashboard`. Admin pages and components can live there, but core logic and transformations should remain in the domain-owning layer, such as jobs. Admin may depend on several feature modules. Basic admin-specific queries and dashboard aggregations can remain in admin. Core business rules belong to their owning domain and admin points to them.

- Interview answer quality: 3/4
- Frontend engineering judgment: 3/4
- Project-specific recall: Consistent with current central admin surfaces and feature-owned job/domain code.

## Confirmed Improved Frontend Answer

This answer was genuinely produced by Richard in Q10 after the weaker Q1 overview. It was not a model answer repeated back immediately.

> I used feature-oriented Nuxt layers to give the frontend a repeatable structure that broadly matched the backend modular-monolith boundaries. Pages and admin surfaces could remain easy to navigate, while domain logic stayed with the feature that owned it. The main tradeoff was dependency discipline: cross-layer imports became more explicit and verbose, and admin ownership could be ambiguous. The rule I landed on was that the central admin layer owns admin navigation, pages, and admin-only aggregation, while core business rules and transformations remain in their domain layer. I would keep that structure today, but document those ownership rules for a team.

Assessment:

- Interview answer quality: 3/4
- Frontend engineering judgment: 3/4
- Improvement demonstrated: clearer problem, decision, tradeoff, ownership rule, and team impact than Q1.

## Strengths Observed

- Honest separation of historical implementation, current capability, and hypothetical design.
- Strong feature/domain organization instincts and good page/component/composable boundaries.
- Correct distinction between frontend route guards and backend authorization.
- Practical use of typed API results, feature composables, Pinia, refs, computed state, and SignalR.
- Good willingness to state missing experience rather than invent implementation facts.
- Proportionate reasoning improved when real operational constraints were made explicit.

## Weak Spots

- Semantic HTML and accessibility: native links/buttons, keyboard focus, nested controls, screen-reader announcements, color-independent status, and reduced motion.
- State taxonomy: distinguish server data, global durable state, feature coordination state, local UI state, and URL/shareable state.
- Loading/recovery UX: explicit empty states, stale-but-usable data, non-blocking refresh failures, and realtime-disconnection behavior.
- Testing strategy: move from isolated unit guardrails toward explicit component/integration/E2E boundaries and a reliable full-suite command.
- Runtime trust boundaries: TypeScript and `ApiResult<T>` do not validate external JSON at runtime.
- Multi-user/account authorization: current explanation is strongest for the historical single-admin constraint; tenant isolation requires comprehensive server-side enforcement.
- Project reacclimation: current RefineBridge workflows differ from older Vue 2/RDrive structures.

## Next Practice Actions

1. Independently explain and repair an interactive-card pattern using semantic links/buttons, keyboard focus, and independent nested controls.
2. Produce a one-page state-placement table with examples for server, global, feature, local, and URL state.
3. Design stale-data behavior for a list with background refresh and SignalR disconnection.
4. Classify five existing frontend tests as unit, component, integration, or source-structure tests; identify one missing E2E path.
5. Explain when runtime validation is needed at an API boundary despite TypeScript generics.
6. Reacclimate to current RefineBridge terminology: dashboard, connected accounts, import flows, tasks/runs, account/subscription, and admin operations.

## Privacy And Claim Boundaries

- No credentials, `.env` contents, customer data, private accounts, live URLs, or customer details recorded.
- Older Vue 2/RDrive behavior is labelled historical rather than asserted as current RefineBridge behavior.
- Current implementation claims were limited to code inspected read-only.
- No changes were made to the RefineBridge repository.

## Issue #14 Acceptance Criteria

- Complete: One live frontend diagnostic session completed.
- Complete: Confirmed RefineBridge path and inspected frontend code read-only.
- Complete: Session note contains date, target role, project, questions, raw answers, scores, code references, and notes.
- Complete: Covered structure, data/state, forms/validation, loading/error/empty states, auth/account boundaries, TypeScript, testing, and accessibility.
- Complete: Included a repository-grounded interactive-card code-reading/debugging task.
- Complete: Richard genuinely improved the feature-layer explanation during the session.
- Complete: Frontend weak spots and practice actions recorded for tracker update.
- Complete: Session prepared for practice-log update.
- Complete: Privacy and implementation-claim boundaries enforced.
- Complete: RefineBridge repository remained unmodified.

Issue status intentionally unchanged. No commit or issue-closing action performed.
