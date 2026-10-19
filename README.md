# Hamplard — Frontend Repo

> **Next.js 14 frontend for Africa's practical skills online learning platform**

This is **Repo 3 of 3** in the Hamplard project:

| Repo | Description |
|------|-------------|
| `hamplard-contract` | Soroban smart contract — course payments + certificates |
| `hamplard-backend` | NestJS API — content, progress, users |
| `hamplard-frontend` ← you are here | Next.js 14 — student and instructor portal |

---

## Pages

| Route | Auth | Description |
|---|---|---|
| `/` | — | Public course marketplace with search and category filters |
| `/auth/login` | — | Freighter wallet connect with student/instructor role selection |
| `/dashboard/courses` | ✓ | Student: enrolled courses. Instructor: redirects to instructor dashboard |
| `/dashboard/courses/:id` | — | Course detail page — overview, curriculum, enroll button |
| `/dashboard/courses/:id/learn` | ✓ | Video player with lesson sidebar, progress tracking, completion |
| `/dashboard/courses/create` | ✓ INSTRUCTOR | Create course form with on-chain registration |
| `/dashboard/instructor` | ✓ INSTRUCTOR | Revenue stats + my courses list |
| `/dashboard/certificates` | ✓ | Student's earned certificates with copy + share links |
| `/certificates/:id` | — | **Public** certificate verification page (no login needed) |
| `/notifications` | ✓ | Notification feed with colour-coded types |

---

## Design System

Hamplard's foundational token system is documented in:

- `src/styles/tokens.css` (source of truth for CSS variables)
- `design-system-tokens.md` (hex/RGB usage notes + WCAG checks)
- `typography-system.md` (modular type scale and semantic text roles)

**Typography:**
- Display headings: Playfair Display (serif)
- Body: DM Sans
- Code/IDs: JetBrains Mono

---

## Key Features

**Public course marketplace** (`/`) — browse, search, and filter active courses by category and level without signing in. The homepage shows a category pill bar with all eight Hamplard skill areas.

**Role-aware login** (`/auth/login`) — the login page has a student/instructor toggle. First-time users pick their role here and it is set on their account.

**Course learn page** (`/dashboard/courses/:id/learn`) — full-screen layout with a lesson sidebar (modules expanded/collapsed, completed lessons marked with checkmarks) and a main content area with the video player. Students click "Mark complete" after each lesson. Progress percentage updates live.

**Certificate verification page** (`/certificates/:id`) — a public, shareable page showing a gold certificate with the student's name, course title, instructor, issue date, and blockchain verification status. Uses server-side rendering for fast sharing.

**Instructor course creation** — three-step flow: fill in course details → upload thumbnail → register on Stellar via Freighter → submit for admin review. The form generates a unique `courseId` automatically.

---

## Setup

```bash
cp .env.example .env.local   # fill in contract ID + backend URL
npm install
npm run dev                   # → http://localhost:3001
```

Install [Freighter](https://freighter.app) and switch it to Testnet.

---

## Testing

### Unit & Component Tests (Vitest)

```bash
npm run test
```

### End-to-End Tests (Playwright)

Run all E2E tests across Chromium, Firefox, and WebKit:

```bash
npm run test:e2e
```

Open the Playwright UI for interactive test authoring and debugging:

```bash
npm run test:e2e:ui
```

### Visual Regression Tests

Visual regression tests use Playwright's `toHaveScreenshot` to catch accidental layout changes on the homepage and course detail page. Baseline screenshots are stored in `e2e/screenshots/`.

#### Run visual tests only

```bash
npx playwright test --project=visual
```

This runs tests tagged with `@visual` across three viewports:
- **Mobile**: 375px × 667px
- **Tablet**: 768px × 1024px
- **Desktop**: 1280px × 800px

#### Update baseline screenshots

After making intentional UI changes, regenerate and commit the new baselines:

```bash
npx playwright test --update-snapshots
```

Then commit the updated files in `e2e/screenshots/` to the repository.

> **Note:** Baseline screenshots must be committed to the repo before CI can pass. Run `--update-snapshots` locally on the same OS/architecture used by CI (Ubuntu Linux) to avoid platform-specific rendering differences.

#### CI Integration

Visual regression tests run automatically in GitHub Actions on every push and pull request. If a visual diff is detected, the CI job will fail and upload:
- The Playwright HTML report (with side-by-side diffs)
- Test traces for debugging

---

## License

MIT
TODO: Add and Configure robots.txt

1. Project Discovery

1. [ ] Inspect the repository structure.
2. [ ] Confirm the project uses Next.js.
3. [ ] Confirm the project uses Next.js 14.
4. [ ] Confirm the project uses the App Router.
5. [ ] Locate the "src/app" directory.
6. [ ] Confirm "src/app" contains the application routes.
7. [ ] Check whether a "robots.ts" file already exists.
8. [ ] Check whether a "robots.txt" file already exists.
9. [ ] Check whether another robots implementation exists elsewhere.
10. [ ] Search for existing Metadata API usage.
11. [ ] Search for existing "MetadataRoute" imports.
12. [ ] Search for an existing sitemap implementation.
13. [ ] Locate "src/app/sitemap.ts" if present.
14. [ ] Review the existing sitemap configuration.
15. [ ] Confirm the canonical site domain.
16. [ ] Confirm the required sitemap URL.
17. [ ] Review the project's route structure.
18. [ ] Identify dashboard routes.
19. [ ] Identify checkout routes.
20. [ ] Identify API routes.
21. [ ] Identify authentication routes.
22. [ ] Identify Next.js internal routes.
23. [ ] Identify public course routes.
24. [ ] Identify category routes.
25. [ ] Identify the about page.
26. [ ] Identify the teach page.
27. [ ] Identify the teams page.
28. [ ] Review existing route conventions.
29. [ ] Review existing tests.
30. [ ] Review existing build scripts.
31. [ ] Review existing development scripts.
32. [ ] Review linting configuration.
33. [ ] Review TypeScript configuration.
34. [ ] Confirm no custom robots middleware already exists.
35. [ ] Confirm no static robots file conflicts with the new route.
36. [ ] Check Git working tree status.
37. [ ] Confirm the task can be implemented without unrelated changes.
38. [ ] Identify the issue number for the PR.
39. [ ] Record the required PR closing statement.
40. [ ] Define the implementation scope.

2. robots.ts Creation

41. [ ] Create a new file at "src/app/robots.ts".
42. [ ] Use the Next.js Metadata API.
43. [ ] Import "MetadataRoute" from "next".
44. [ ] Use the "MetadataRoute.Robots" type.
45. [ ] Define the robots function.
46. [ ] Ensure the function returns the correct robots metadata structure.
47. [ ] Keep the implementation server-side compatible.
48. [ ] Avoid client-side directives.
49. [ ] Do not add unnecessary dependencies.
50. [ ] Do not create a custom API route for robots.txt.
51. [ ] Do not manually construct the robots.txt response.
52. [ ] Use the App Router MetadataRoute implementation.
53. [ ] Keep the file limited to robots configuration.
54. [ ] Add appropriate typing.
55. [ ] Ensure TypeScript can infer the return structure correctly.
56. [ ] Ensure the implementation follows Next.js 14 conventions.
57. [ ] Ensure the generated route is "/robots.txt".
58. [ ] Ensure no additional route handler is required.
59. [ ] Confirm Next.js generates the response automatically.
60. [ ] Keep the implementation readable.
61. [ ] Keep the implementation minimal.
62. [ ] Avoid unnecessary comments.
63. [ ] Avoid hard-coded route logic outside the robots configuration.
64. [ ] Avoid introducing unrelated metadata changes.
65. [ ] Verify the file is located exactly under "src/app".
66. [ ] Verify the filename is exactly "robots.ts".
67. [ ] Verify the file extension is TypeScript.
68. [ ] Verify the implementation exports the robots function correctly.
69. [ ] Verify the implementation uses "MetadataRoute.Robots".
70. [ ] Confirm the basic implementation compiles.

3. Allow Rules

71. [ ] Configure the root path "/" as allowed.
72. [ ] Configure "/courses" as allowed.
73. [ ] Configure "/courses/*" as allowed.
74. [ ] Configure "/categories/*" as allowed.
75. [ ] Configure "/about" as allowed.
76. [ ] Configure "/teach" as allowed.
77. [ ] Configure "/teams" as allowed.
78. [ ] Ensure the root public site remains crawlable.
79. [ ] Ensure the courses landing page remains crawlable.
80. [ ] Ensure course detail pages remain crawlable.
81. [ ] Ensure category pages remain crawlable.
82. [ ] Ensure the about page remains crawlable.
83. [ ] Ensure the teach page remains crawlable.
84. [ ] Ensure the teams page remains crawlable.
85. [ ] Confirm wildcard syntax is represented correctly.
86. [ ] Confirm "/courses/*" covers course detail routes.
87. [ ] Confirm "/categories/*" covers category detail routes.
88. [ ] Avoid accidentally disallowing public pages.
89. [ ] Avoid adding unrelated public routes to the allowlist.
90. [ ] Preserve the exact required allowlist.
91. [ ] Confirm "/" is not accidentally overridden by a broad disallow.
92. [ ] Confirm public pages can still be crawled.
93. [ ] Confirm public course content can be discovered.
94. [ ] Confirm category content can be discovered.
95. [ ] Confirm the allow rules generate valid robots directives.
96. [ ] Confirm rules are compatible with search-engine parsing.
97. [ ] Confirm wildcard behavior is valid.
98. [ ] Ensure no duplicate allow directives are generated unnecessarily.
99. [ ] Ensure the final output reflects the intended public routes.
100. [ ] Document any framework-specific wildcard representation if necessary.

4. Disallow Rules

101. [ ] Configure "/dashboard/*" as disallowed.
102. [ ] Configure "/checkout" as disallowed.
103. [ ] Configure "/api/*" as disallowed.
104. [ ] Configure "/auth/*" as disallowed.
105. [ ] Configure "/_next/" as disallowed.
106. [ ] Ensure dashboard pages cannot be crawled.
107. [ ] Ensure dashboard subroutes cannot be crawled.
108. [ ] Ensure checkout is excluded from crawling.
109. [ ] Ensure API routes are excluded from crawling.
110. [ ] Ensure API subroutes are excluded from crawling.
111. [ ] Ensure authentication routes are excluded from crawling.
112. [ ] Ensure authentication subroutes are excluded from crawling.
113. [ ] Ensure Next.js internal assets are excluded where required.
114. [ ] Confirm the dashboard wildcard is represented correctly.
115. [ ] Confirm the API wildcard is represented correctly.
116. [ ] Confirm the authentication wildcard is represented correctly.
117. [ ] Confirm the "/_next/" path is represented correctly.
118. [ ] Ensure no public route is accidentally disallowed.
119. [ ] Avoid broad disallow rules such as "/".
120. [ ] Avoid disallowing "/courses".
121. [ ] Avoid disallowing "/categories".
122. [ ] Avoid disallowing "/about".
123. [ ] Avoid disallowing "/teach".
124. [ ] Avoid disallowing "/teams".
125. [ ] Confirm the checkout path is specifically excluded.
126. [ ] Confirm dashboard paths are excluded before crawling.
127. [ ] Confirm API paths are excluded before crawling.
128. [ ] Confirm auth paths are excluded before crawling.
129. [ ] Confirm internal Next.js paths are excluded.
130. [ ] Verify disallow rules match the acceptance criteria.

5. User-Agent Configuration

131. [ ] Configure the robots policy for all search-engine crawlers.
132. [ ] Use the appropriate wildcard user-agent configuration.
133. [ ] Ensure the rules apply to general crawlers.
134. [ ] Ensure the rules are not limited to a single search engine.
135. [ ] Ensure the generated output contains the intended user-agent directive.
136. [ ] Avoid creating unnecessary crawler-specific rules.
137. [ ] Avoid duplicate user-agent sections.
138. [ ] Confirm the allow rules apply to the intended crawler group.
139. [ ] Confirm the disallow rules apply to the intended crawler group.
140. [ ] Confirm the output remains standards-compatible.
141. [ ] Keep crawler configuration simple.
142. [ ] Avoid adding unsupported directives.
143. [ ] Avoid adding crawl-delay unless explicitly required.
144. [ ] Avoid adding host directives.
145. [ ] Avoid adding unrelated SEO configuration.
146. [ ] Confirm the user-agent configuration is generated correctly.
147. [ ] Confirm the final output is readable.
148. [ ] Confirm crawlers can interpret the rules.
149. [ ] Confirm the implementation matches Next.js MetadataRoute behavior.
150. [ ] Document the intended crawler scope if project documentation requires it.

6. Sitemap Configuration

151. [ ] Add the sitemap URL to the robots configuration.
152. [ ] Use "https://hamplard.com/sitemap.xml".
153. [ ] Ensure the sitemap URL is absolute.
154. [ ] Ensure the URL uses HTTPS.
155. [ ] Ensure the hostname is exactly "hamplard.com".
156. [ ] Ensure the path is exactly "/sitemap.xml".
157. [ ] Ensure the sitemap directive is generated.
158. [ ] Ensure the sitemap appears in "/robots.txt".
159. [ ] Confirm there are no typos in the domain.
160. [ ] Confirm there is no trailing whitespace.
161. [ ] Confirm the sitemap URL is not relative.
162. [ ] Confirm the sitemap URL is not accidentally duplicated.
163. [ ] Check whether an existing sitemap implementation uses the same domain.
164. [ ] Keep robots and sitemap configuration consistent.
165. [ ] Verify the sitemap directive follows the generated robots syntax.
166. [ ] Confirm search engines can identify the sitemap.
167. [ ] Confirm the sitemap directive is not placed inside an invalid user-agent rule.
168. [ ] Confirm the generated output contains exactly the required sitemap.
169. [ ] Avoid adding unrelated sitemap URLs.
170. [ ] Verify the sitemap requirement is fully satisfied.

7. Local Development Validation

171. [ ] Start the Next.js development server.
172. [ ] Confirm the application starts without errors.
173. [ ] Open "/robots.txt".
174. [ ] Confirm "/robots.txt" returns HTTP 200.
175. [ ] Confirm the response is plain text.
176. [ ] Confirm the generated content is not HTML.
177. [ ] Confirm the user-agent directive exists.
178. [ ] Confirm the root allow rule exists.
179. [ ] Confirm the courses allow rule exists.
180. [ ] Confirm course wildcard behavior is represented.
181. [ ] Confirm categories wildcard behavior is represented.
182. [ ] Confirm "/about" is allowed.
183. [ ] Confirm "/teach" is allowed.
184. [ ] Confirm "/teams" is allowed.
185. [ ] Confirm dashboard is disallowed.
186. [ ] Confirm checkout is disallowed.
187. [ ] Confirm API is disallowed.
188. [ ] Confirm auth is disallowed.
189. [ ] Confirm "/_next/" is disallowed.
190. [ ] Confirm the sitemap URL is present.
191. [ ] Confirm the sitemap URL is correct.
192. [ ] Confirm there are no unexpected directives.
193. [ ] Confirm there are no duplicate directives.
194. [ ] Confirm there are no TypeScript runtime errors.
195. [ ] Confirm hot reload detects changes if applicable.
196. [ ] Confirm the generated robots output updates after changes.
197. [ ] Test the route after restarting the dev server.
198. [ ] Test the route in a clean browser request.
199. [ ] Test the route using an HTTP client if available.
200. [ ] Record the final generated output for review.

8. Automated Testing

201. [ ] Search for existing metadata route tests.
202. [ ] Determine the project's preferred testing approach.
203. [ ] Add a test for "/robots.txt".
204. [ ] Verify the route exists.
205. [ ] Verify the route returns successfully.
206. [ ] Verify the output contains the user-agent directive.
207. [ ] Verify the root path is allowed.
208. [ ] Verify "/courses" is allowed.
209. [ ] Verify course wildcard paths are allowed.
210. [ ] Verify category wildcard paths are allowed.
211. [ ] Verify "/about" is allowed.
212. [ ] Verify "/teach" is allowed.
213. [ ] Verify "/teams" is allowed.
214. [ ] Verify "/dashboard/*" is disallowed.
215. [ ] Verify "/checkout" is disallowed.
216. [ ] Verify "/api/*" is disallowed.
217. [ ] Verify "/auth/*" is disallowed.
218. [ ] Verify "/_next/" is disallowed.
219. [ ] Verify the sitemap URL is included.
220. [ ] Verify the exact sitemap URL.
221. [ ] Verify no required allow rule is missing.
222. [ ] Verify no required disallow rule is missing.
223. [ ] Verify the response format.
224. [ ] Verify the generated robots configuration is deterministic.
225. [ ] Ensure tests do not depend on production infrastructure.
226. [ ] Ensure tests do not require external network access.
227. [ ] Ensure tests are repeatable.
228. [ ] Ensure tests use the project's existing testing conventions.
229. [ ] Add regression coverage for future changes.
230. [ ] Confirm the tests pass locally.

9. TypeScript & Build Verification

231. [ ] Run the project's type-check command.
232. [ ] Confirm "robots.ts" passes TypeScript validation.
233. [ ] Confirm the "MetadataRoute.Robots" type is valid.
234. [ ] Confirm there are no implicit "any" errors.
235. [ ] Confirm there are no unused imports.
236. [ ] Confirm there are no unused variables.
237. [ ] Run the project linter.
238. [ ] Fix any lint errors caused by the new file.
239. [ ] Run formatting checks.
240. [ ] Format the new file according to project standards.
241. [ ] Run the production build.
242. [ ] Confirm the build completes successfully.
243. [ ] Confirm "/robots.txt" is generated correctly by the production build.
244. [ ] Confirm the App Router recognizes the metadata route.
245. [ ] Confirm no route conflicts occur.
246. [ ] Confirm no existing sitemap functionality breaks.
247. [ ] Confirm no existing pages break.
248. [ ] Confirm no unrelated build warnings are introduced.
249. [ ] Review the final build output.
250. [ ] Confirm the implementation is production-ready.

10. Final Review & PR

251. [ ] Review the complete Git diff.
252. [ ] Confirm only intended files were changed.
253. [ ] Confirm "src/app/robots.ts" is included.
254. [ ] Confirm ".env" files were not modified unnecessarily.
255. [ ] Confirm no generated files were accidentally committed.
256. [ ] Confirm no dependencies were added unnecessarily.
257. [ ] Confirm no unrelated refactoring was included.
258. [ ] Confirm the implementation follows Next.js 14.
259. [ ] Confirm the implementation uses "MetadataRoute.Robots".
260. [ ] Confirm App Router requirements are satisfied.
261. [ ] Confirm all public pages are allowed.
262. [ ] Confirm all specified private paths are disallowed.
263. [ ] Confirm the sitemap URL is correct.
264. [ ] Confirm "/robots.txt" works in development.
265. [ ] Confirm "/robots.txt" works in production build validation.
266. [ ] Confirm automated tests pass.
267. [ ] Confirm linting passes.
268. [ ] Confirm type checking passes.
269. [ ] Confirm build passes.
270. [ ] Confirm acceptance criteria are fully satisfied.

11. PR Description

271. [ ] Create the pull request.
272. [ ] Use a clear PR title.
273. [ ] Summarize the robots.txt implementation.
274. [ ] Mention that the App Router Metadata API is used.
275. [ ] Mention the public routes that remain crawlable.
276. [ ] Mention the private routes that are disallowed.
277. [ ] Mention the sitemap configuration.
278. [ ] Mention "/robots.txt" validation.
279. [ ] Mention automated test coverage.
280. [ ] Include the required issue-closing syntax.
281. [ ] Replace "[issue_id]" with the actual issue number.
282. [ ] Ensure the PR description contains "Closes #[issue_id]".
283. [ ] Ensure the closing syntax is not accidentally written as plain placeholder text.
284. [ ] Verify GitHub recognizes the issue-closing syntax.
285. [ ] Include testing performed.
286. [ ] Include build/type-check results.
287. [ ] Include any relevant screenshots or output if required.
288. [ ] Confirm the PR description is concise.
289. [ ] Confirm the PR description accurately describes the changes.
290. [ ] Confirm no unrelated work is mentioned as completed.

12. Final Acceptance Checklist

291. [ ] "src/app/robots.ts" exists.
292. [ ] "MetadataRoute.Robots" is used.
293. [ ] "/robots.txt" returns the expected content.
294. [ ] Dashboard routes are disallowed.
295. [ ] API routes are disallowed.
296. [ ] Authentication routes are disallowed.
297. [ ] Checkout is disallowed.
298. [ ] Public pages are allowed.
299. [ ] "https://hamplard.com/sitemap.xml" is included.
300. [ ] PR description contains "Closes #[issue_id]" and the task is ready for review.
use soroban_sdk::{
    contract, contractimpl, contracttype, symbol_short, Address, Env, Symbol, Vec,
};

const TTL_INITIAL_LEDGERS: u32 = 17_280;
const TTL_MAX_LEDGERS: u32 = 120_960;
const MAX_TERM_LEDGERS: u32 = 10_000_000;

#[contracttype]
#[derive(Clone)]
pub enum ArbiterMembershipKey {
    Admin,
    MembershipTerm,
    Expiry(Address),
    Registered(Address),
    AuditSequence,
}

#[contracttype]
#[derive(Clone, Debug, Eq, PartialEq)]
pub struct MembershipStatus {
    pub arbiter: Address,
    pub registered: bool,
    pub expiry_ledger: u32,
    pub current_ledger: u32,
    pub active: bool,
    pub remaining_ledgers: u32,
}

#[contracttype]
#[derive(Clone, Debug, Eq, PartialEq)]
pub struct TermChangedEvent {
    pub admin: Address,
    pub old_term: u32,
    pub new_term: u32,
    pub ledger: u32,
}

#[contracttype]
#[derive(Clone, Debug, Eq, PartialEq)]
pub struct RenewalEvent {
    pub arbiter: Address,
    pub old_expiry: u32,
    pub new_expiry: u32,
    pub term: u32,
    pub ledger: u32,
}

#[contracttype]
#[derive(Clone, Debug, Eq, PartialEq)]
pub struct RegistrationEvent {
    pub arbiter: Address,
    pub expiry_ledger: u32,
    pub term: u32,
    pub ledger: u32,
}

#[contracttype]
#[derive(Clone, Debug, Eq, PartialEq)]
pub struct MembershipAuditRecord {
    pub sequence: u32,
    pub action: Symbol,
    pub subject: Address,
    pub actor: Address,
    pub old_expiry: u32,
    pub new_expiry: u32,
    pub ledger: u32,
}

#[contract]
pub struct ArbiterMembershipContract;

#[contractimpl]
impl ArbiterMembershipContract {
    pub fn init_membership(
        env: Env,
        admin: Address,
        default_term_ledgers: u32,
    ) {
        admin.require_auth();
        validate_term(default_term_ledgers);

        let admin_key = ArbiterMembershipKey::Admin;
        let term_key = ArbiterMembershipKey::MembershipTerm;

        if env.storage().instance().has(&admin_key) {
            panic!("membership already initialized");
        }

        env.storage().instance().set(&admin_key, &admin);
        env.storage()
            .instance()
            .set(&term_key, &default_term_ledgers);

        emit_initialized(&env, &admin, default_term_ledgers);
    }

    pub fn set_membership_term(
        env: Env,
        admin: Address,
        new_term_ledgers: u32,
    ) {
        admin.require_auth();
        validate_admin(&env, &admin);
        validate_term(new_term_ledgers);

        let old_term = read_term(&env);

        env.storage()
            .instance()
            .set(
                &ArbiterMembershipKey::MembershipTerm,
                &new_term_ledgers,
            );

        emit_term_changed(
            &env,
            &admin,
            old_term,
            new_term_ledgers,
        );

        write_audit(
            &env,
            symbol_short!("term_set"),
            admin.clone(),
            admin,
            0,
            0,
        );
    }

    pub fn register_arbiter(
        env: Env,
        admin: Address,
        arbiter: Address,
    ) {
        admin.require_auth();
        validate_admin(&env, &admin);
        validate_address_not_admin(&env, &arbiter);

        let registered_key =
            ArbiterMembershipKey::Registered(arbiter.clone());

        if env.storage()
            .persistent()
            .get::<_, bool>(&registered_key)
            .unwrap_or(false)
        {
            panic!("arbiter already registered");
        }

        let term = read_term(&env);
        let now = env.ledger().sequence();
        let expiry = checked_add(now, term);

        env.storage()
            .persistent()
            .set(&registered_key, &true);

        env.storage()
            .persistent()
            .set(
                &ArbiterMembershipKey::Expiry(arbiter.clone()),
                &expiry,
            );

        extend_membership_ttl(&env, &arbiter);

        emit_registration(&env, &arbiter, expiry, term);

        write_audit(
            &env,
            symbol_short!("arb_reg"),
            arbiter,
            admin,
            0,
            expiry,
        );
    }

    pub fn renew_arbiter_membership(
        env: Env,
        arbiter: Address,
    ) -> u32 {
        arbiter.require_auth();

        let registered_key =
            ArbiterMembershipKey::Registered(arbiter.clone());

        if !env.storage()
            .persistent()
            .get::<_, bool>(&registered_key)
            .unwrap_or(false)
        {
            panic!("arbiter is not registered");
        }

        let term = read_term(&env);
        let now = env.ledger().sequence();

        let expiry_key =
            ArbiterMembershipKey::Expiry(arbiter.clone());

        let old_expiry = env.storage()
            .persistent()
            .get::<_, u32>(&expiry_key)
            .unwrap_or_else(|| panic!("membership expiry missing"));

        let base = if old_expiry > now {
            old_expiry
        } else {
            now
        };

        let new_expiry = checked_add(base, term);

        env.storage()
            .persistent()
            .set(&expiry_key, &new_expiry);

        extend_membership_ttl(&env, &arbiter);

        emit_renewal(
            &env,
            &arbiter,
            old_expiry,
            new_expiry,
            term,
        );

        write_audit(
            &env,
            symbol_short!("arb_renew"),
            arbiter.clone(),
            arbiter,
            old_expiry,
            new_expiry,
        );

        new_expiry
    }

    pub fn get_arbiter_membership(
        env: Env,
        arbiter: Address,
    ) -> MembershipStatus {
        let registered = env.storage()
            .persistent()
            .get::<_, bool>(
                &ArbiterMembershipKey::Registered(arbiter.clone()),
            )
            .unwrap_or(false);

        let expiry = env.storage()
            .persistent()
            .get::<_, u32>(
                &ArbiterMembershipKey::Expiry(arbiter.clone()),
            )
            .unwrap_or(0);

        let now = env.ledger().sequence();
        let active = registered && expiry > now;

        let remaining = if active {
            expiry - now
        } else {
            0
        };

        MembershipStatus {
            arbiter,
            registered,
            expiry_ledger: expiry,
            current_ledger: now,
            active,
            remaining_ledgers: remaining,
        }
    }

    pub fn is_arbiter_membership_active(
        env: Env,
        arbiter: Address,
    ) -> bool {
        is_active_internal(&env, &arbiter)
    }

    pub fn filter_active_arbiters(
        env: Env,
        candidates: Vec<Address>,
    ) -> Vec<Address> {
        let mut active = Vec::new(&env);

        for arbiter in candidates.iter() {
            if is_active_internal(&env, &arbiter) {
                active.push_back(arbiter);
            }
        }

        active
    }

    pub fn deactivate_arbiter(
        env: Env,
        admin: Address,
        arbiter: Address,
    ) {
        admin.require_auth();
        validate_admin(&env, &admin);

        let registered_key =
            ArbiterMembershipKey::Registered(arbiter.clone());

        if !env.storage()
            .persistent()
            .get::<_, bool>(&registered_key)
            .unwrap_or(false)
        {
            panic!("arbiter is not registered");
        }

        let expiry_key =
            ArbiterMembershipKey::Expiry(arbiter.clone());

        let old_expiry = env.storage()
            .persistent()
            .get::<_, u32>(&expiry_key)
            .unwrap_or(0);

        let now = env.ledger().sequence();

        env.storage()
            .persistent()
            .set(&expiry_key, &now);

        extend_membership_ttl(&env, &arbiter);

        env.events().publish(
            (symbol_short!("arb_deact"), arbiter.clone()),
            now,
        );

        write_audit(
            &env,
            symbol_short!("arb_deact"),
            arbiter,
            admin,
            old_expiry,
            now,
        );
    }
}

fn validate_term(term: u32) {
    if term == 0 {
        panic!("membership term must be positive");
    }

    if term > MAX_TERM_LEDGERS {
        panic!("membership term exceeds maximum");
    }
}

fn validate_admin(env: &Env, caller: &Address) {
    let admin = env.storage()
        .instance()
        .get::<_, Address>(&ArbiterMembershipKey::Admin)
        .unwrap_or_else(|| panic!("membership is not initialized"));

    if admin != *caller {
        panic!("unauthorized administrator");
    }
}

fn read_term(env: &Env) -> u32 {
    let term = env.storage()
        .instance()
        .get::<_, u32>(&ArbiterMembershipKey::MembershipTerm)
        .unwrap_or_else(|| panic!("membership term not configured"));

    validate_term(term);
    term
}

fn validate_address_not_admin(
    env: &Env,
    arbiter: &Address,
) {
    let admin = env.storage()
        .instance()
        .get::<_, Address>(&ArbiterMembershipKey::Admin)
        .unwrap_or_else(|| panic!("membership is not initialized"));

    if admin == *arbiter {
        panic!("administrator cannot be registered as arbiter");
    }
}

fn checked_add(left: u32, right: u32) -> u32 {
    left.checked_add(right)
        .unwrap_or_else(|| panic!("membership expiry overflow"))
}

fn is_active_internal(
    env: &Env,
    arbiter: &Address,
) -> bool {
    let registered = env.storage()
        .persistent()
        .get::<_, bool>(
            &ArbiterMembershipKey::Registered(arbiter.clone()),
        )
        .unwrap_or(false);

    if !registered {
        return false;
    }

    let expiry = env.storage()
        .persistent()
        .get::<_, u32>(
            &ArbiterMembershipKey::Expiry(arbiter.clone()),
        )
        .unwrap_or(0);

    expiry > env.ledger().sequence()
}

fn extend_membership_ttl(
    env: &Env,
    arbiter: &Address,
) {
    let registered_key =
        ArbiterMembershipKey::Registered(arbiter.clone());

    let expiry_key =
        ArbiterMembershipKey::Expiry(arbiter.clone());

    env.storage().persistent().extend_ttl(
        &registered_key,
        TTL_INITIAL_LEDGERS,
        TTL_MAX_LEDGERS,
    );

    env.storage().persistent().extend_ttl(
        &expiry_key,
        TTL_INITIAL_LEDGERS,
        TTL_MAX_LEDGERS,
    );
}

fn emit_initialized(
    env: &Env,
    admin: &Address,
    term: u32,
) {
    env.events().publish(
        (symbol_short!("arb_init"), admin.clone()),
        (term, env.ledger().sequence()),
    );
}

fn emit_term_changed(
    env: &Env,
    admin: &Address,
    old_term: u32,
    new_term: u32,
) {
    let event = TermChangedEvent {
        admin: admin.clone(),
        old_term,
        new_term,
        ledger: env.ledger().sequence(),
    };

    env.events().publish(
        (symbol_short!("term_change"),),
        event,
    );
}

fn emit_registration(
    env: &Env,
    arbiter: &Address,
    expiry: u32,
    term: u32,
) {
    let event = RegistrationEvent {
        arbiter: arbiter.clone(),
        expiry_ledger: expiry,
        term,
        ledger: env.ledger().sequence(),
    };

    env.events().publish(
        (symbol_short!("arb_register"),),
        event,
    );
}

fn emit_renewal(
    env: &Env,
    arbiter: &Address,
    old_expiry: u32,
    new_expiry: u32,
    term: u32,
) {
    let event = RenewalEvent {
        arbiter: arbiter.clone(),
        old_expiry,
        new_expiry,
        term,
        ledger: env.ledger().sequence(),
    };

    env.events().publish(
        (symbol_short!("arb_renew"),),
        event,
    );
}

fn write_audit(
    env: &Env,
    action: Symbol,
    subject: Address,
    actor: Address,
    old_expiry: u32,
    new_expiry: u32,
) {
    let seq_key = ArbiterMembershipKey::AuditSequence;

    let current = env.storage()
        .instance()
        .get::<_, u32>(&seq_key)
        .unwrap_or(0);

    let next = current.checked_add(1)
        .unwrap_or_else(|| panic!("audit sequence overflow"));

    let record = MembershipAuditRecord {
        sequence: next,
        action,
        subject,
        actor,
        old_expiry,
        new_expiry,
        ledger: env.ledger().sequence(),
    };

    env.storage().instance().set(&seq_key, &next);

    env.storage()
        .persistent()
        .set(&(seq_key.clone(), next), &record);

    env.storage().persistent().extend_ttl(
        &(seq_key, next),
        TTL_INITIAL_LEDGERS,
        TTL_MAX_LEDGERS,
    );

    env.events().publish(
        (symbol_short!("arb_audit"),),
        record,
    );
}

pub fn ensure_arbiter_active(
    env: &Env,
    arbiter: &Address,
) {
    if !is_active_internal(env, arbiter) {
        panic!("arbiter membership expired or inactive");
    }
}

pub fn select_active_panel(
    env: &Env,
    candidates: &Vec<Address>,
    required_count: u32,
) -> Vec<Address> {
    if required_count == 0 {
        panic!("panel size must be positive");
    }

    let mut active = Vec::new(env);

    for candidate in candidates.iter() {
        if is_active_internal(env, &candidate)
            && !active.contains(candidate.clone())
        {
            active.push_back(candidate);
        }
    }

    if active.len() < required_count {
        panic!("not enough active arbiters for panel");
    }

    let mut selected = Vec::new(env);
    let mut index = 0;

    while index < required_count {
        selected.push_back(active.get(index).unwrap());
        index += 1;
    }

    selected
}

#[cfg(test)]
mod test_arbiter_membership {
    use super::*;
    use soroban_sdk::testutils::{Address as _, Ledger};

    fn setup() -> (
        Env,
        ArbiterMembershipContractClient<'static>,
        Address,
        Address,
    ) {
        let env = Env::default();
        env.mock_all_auths();

        let contract_id = env.register(
            ArbiterMembershipContract,
            (),
        );

        let client =
            ArbiterMembershipContractClient::new(&env, &contract_id);

        let admin = Address::generate(&env);
        let arbiter = Address::generate(&env);

        client.init_membership(&admin, &100);

        (env, client, admin, arbiter)
    }

    #[test]
    fn registration_starts_active_membership() {
        let (env, client, admin, arbiter) = setup();

        client.register_arbiter(&admin, &arbiter);

        let status = client.get_arbiter_membership(&arbiter);

        assert!(status.registered);
        assert!(status.active);

        assert_eq!(
            status.expiry_ledger,
            env.ledger().sequence() + 100,
        );

        assert_eq!(status.remaining_ledgers, 100);
    }

    #[test]
    fn membership_expires_at_expiry_ledger() {
        let (env, client, admin, arbiter) = setup();

        client.register_arbiter(&admin, &arbiter);

        env.ledger().set_sequence_number(
            env.ledger().sequence() + 100,
        );

        assert!(
            !client.is_arbiter_membership_active(&arbiter)
        );

        let status = client.get_arbiter_membership(&arbiter);

        assert!(!status.active);
        assert_eq!(status.remaining_ledgers, 0);
    }

    #[test]
    fn renewal_extends_expiry() {
        let (_env, client, admin, arbiter) = setup();

        client.register_arbiter(&admin, &arbiter);

        let old = client
            .get_arbiter_membership(&arbiter)
            .expiry_ledger;

        let new_expiry =
            client.renew_arbiter_membership(&arbiter);

        assert_eq!(new_expiry, old + 100);

        assert!(
            client.is_arbiter_membership_active(&arbiter)
        );
    }

    #[test]
    fn late_renewal_starts_from_current_ledger() {
        let (env, client, admin, arbiter) = setup();

        client.register_arbiter(&admin, &arbiter);

        let old_expiry = client
            .get_arbiter_membership(&arbiter)
            .expiry_ledger;

        env.ledger().set_sequence_number(old_expiry + 5);

        let new_expiry =
            client.renew_arbiter_membership(&arbiter);

        assert_eq!(new_expiry, old_expiry + 5 + 100);

        assert!(
            client.is_arbiter_membership_active(&arbiter)
        );
    }

    #[test]
    fn expired_arbiter_is_removed_from_candidates() {
        let (env, client, admin, arbiter) = setup();

        let second = Address::generate(&env);

        client.register_arbiter(&admin, &arbiter);
        client.register_arbiter(&admin, &second);

        let expiry = client
            .get_arbiter_membership(&arbiter)
            .expiry_ledger;

        env.ledger().set_sequence_number(expiry);

        let candidates = Vec::from_array(
            &env,
            [arbiter.clone(), second.clone()],
        );

        let active = client.filter_active_arbiters(&candidates);

        assert_eq!(active.len(), 1);
        assert_eq!(active.get(0).unwrap(), second);
    }

    #[test]
    fn query_reports_expiry_for_registered_arbiter() {
        let (env, client, admin, arbiter) = setup();

        client.register_arbiter(&admin, &arbiter);

        let status = client.get_arbiter_membership(&arbiter);

        assert_eq!(status.arbiter, arbiter);

        assert_eq!(
            status.current_ledger,
            env.ledger().sequence(),
        );

        assert!(
            status.expiry_ledger > status.current_ledger
        );
    }

    #[test]
    #[should_panic(expected = "membership term must be positive")]
    fn zero_term_is_rejected() {
        let env = Env::default();
        env.mock_all_auths();

        let contract_id = env.register(
            ArbiterMembershipContract,
            (),
        );

        let client =
            ArbiterMembershipContractClient::new(&env, &contract_id);

        let admin = Address::generate(&env);

        client.init_membership(&admin, &0);
    }

    #[test]
    #[should_panic(expected = "arbiter is not registered")]
    fn unregistered_arbiter_cannot_renew() {
        let (_env, client, _admin, unknown) = setup();

        client.renew_arbiter_membership(&unknown);
    }

    #[test]
    #[should_panic(expected = "arbiter already registered")]
    fn duplicate_registration_is_rejected() {
        let (_env, client, admin, arbiter) = setup();

        client.register_arbiter(&admin, &arbiter);
        client.register_arbiter(&admin, &arbiter);
    }

    #[test]
    #[should_panic(expected = "membership already initialized")]
    fn initialization_cannot_run_twice() {
        let (_env, client, admin, _arbiter) = setup();

        client.init_membership(&admin, &100);
    }
}
