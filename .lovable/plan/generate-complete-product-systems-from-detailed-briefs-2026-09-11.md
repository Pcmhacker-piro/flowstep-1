## Generate complete product systems from detailed briefs

Detailed requests should produce a coordinated set of separate, usable screens instead of one dashboard with the remaining pages hidden below the canvas.

### What will change

1. **Plan the product before drawing**
   - Convert the brief into a strict screen manifest: information architecture, shared navigation, product identity, design tokens, and the exact content required on each page.
   - Preserve every explicitly requested page and important state. For this Todo brief that includes Dashboard, All Tasks, Today, Upcoming, Completed, Projects, Task Details, Calendar, Analytics, Settings, and Add Task.
   - Share one visual system and realistic data set across the entire screen family so it feels like one shipped product.

2. **Generate one canvas frame per screen**
   - Stream screen-specific HTML as separate events and place each result as its own labeled canvas item in a tidy grid.
   - Render initial placeholders for all planned screens, then progressively replace each placeholder without reloading or blinking.
   - Keep completed screens even if another screen fails, and show a clear per-screen failure state instead of losing the whole generation.

3. **Raise the industry-quality standard**
   - Replace the dashboard-biased prompt with page-specific composition rules for lists, timelines, calendars, analytics, settings, details, and creation flows.
   - Require consistent sidebar/profile treatment, responsive variants, interaction states, dense realistic content, accessibility, dark-mode treatment where requested, and final alignment/overflow checks.
   - Use appropriate generated visual content only when the product needs it; application avatars and profiles should use coherent, purposeful identity elements rather than decorative stock imagery.

4. **Make long briefs reliable**
   - Generate screens in bounded parallel batches so a ten-page request completes progressively without one oversized response being cut off.
   - Use the supported streaming response format, preserve gateway errors, and avoid artificial generation deadlines.
   - Keep simple prompts simple: one requested page remains one frame; multi-page product briefs expand into the full requested set.

### Technical details

- The generation endpoint will emit typed SSE events for `manifest`, `screen-start`, `screen-delta`, `screen-complete`, `screen-error`, and final completion.
- The canvas state will track screen identity and update only the matching frame, preventing cross-screen redraws and flicker.
- Each generated screen remains a self-contained 1440×960 HTML document so existing selection, editing, export, undo, and resizing continue to work.
- The generation request will use the current supported Lovable AI streaming API and model contract.

### Validation

- Run the supplied Todo brief end to end and confirm all named screens appear as distinct frames.
- Inspect desktop and mobile canvas behavior, verify no blinking, clipped text, overlap, or empty unfinished frames, and confirm edits/export still work.
- Test one short prompt to confirm it still creates a single focused design rather than an unnecessary product suite.