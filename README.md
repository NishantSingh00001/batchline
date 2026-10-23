# Batchline — Micro-producer traceability workbench

Batchline links ingredient lots to small production runs, quality notes, and trade dispatches. The workflow is designed for a one-to-ten-person producer who needs to answer “which batches used this lot?” and “where did that batch go?” without maintaining a complex enterprise system.

## Run and deploy

This is a static site. Open `index.html` directly or deploy this folder to Vercel with no build command and no environment variables. Three.js and GSAP load from public CDNs for the mixing-vessel scene and entrance motion. If Three.js is unavailable, an inline illustrated vessel is used. No paid service or API key is required.

## What works in the browser demo

- Eight connected pages cover overview, ingredient lots, production runs, trace and recall exercises, dispatch, quality checks, suppliers, and records.
- Ingredient lots, production runs, dispatch notes, quality checks, supplier records, and activity are saved to this browser's local storage.
- Recording a production run deducts the entered quantities from selected ingredient lots and creates a bidirectional lot-to-batch trace link.
- Dispatch notes link a batch to a trade destination and quantity. A trace view shows connected dispatches without storing end-customer names or contact details.
- A mock trace exercise computes connected batches and sample dispatches from local records. It does not send recall messages.
- Quality logs and manually entered release states are stored locally. The app does not determine food safety or compliance.
- Archive metadata can be exported as JSON, restored from JSON, and quality logs as CSV. No data is sent anywhere unless you export and share it.
- Starter records and trade destinations are fictional examples for Thane. They are not verified suppliers, businesses, recipes, food-safety checks, or actual transactions.

## Scope and limits

This is a portfolio prototype, not a food-safety certification or a complete production system. It has no user accounts, shared database, cloud sync, sensor or POS connections, supplier verification, customer notifications, or AI model. Browser storage is device-specific and is not an encrypted long-term archive. Labels such as “Released” are operator-entered demo states. Review your food-safety processes with qualified people before using any production system for real operations.

Food traceability already has established software products, including systems aimed at smaller producers. Batchline explores a narrower, low-friction workflow for micro-producers rather than claiming the general category is untouched.

## Files

- `index.html` — app shell and eight-page navigation
- `styles.css` — dark stainless-and-citrus visual system, responsive layout
- `app.js` — local data model, trace paths, forms, and Three.js vessel scene
- `FEATURES.md` — capability inventory and demo boundaries
