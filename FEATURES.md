# Batchline feature inventory

The items below are implemented in the browser prototype. Sample suppliers, lots, checks, batches, and destinations are fictional; this is not a hosted production system.

## Workspace and navigation

1. Eight connected hash-routed pages.
2. Responsive desktop, tablet, and phone layouts.
3. Persistent operations sidebar with active-page state.
4. Mobile slide-in navigation.
5. Thane field-edition workspace labeling.
6. Local-device storage indicator.
7. Search dialog across lot, batch, and supplier records.
8. Recent activity feed.
9. Live count of tracked ingredient lots.
10. Reduced-motion support.
11. GSAP entrance transitions when the library is available.
12. Three.js mixing-vessel scene with illustrated fallback.
13. Drag-to-orbit the vessel.
14. Vessel motion pause and resume.
15. Reset vessel orientation.
16. Vessel zoom by scroll.

## Ingredient receiving and stock

17. Search inventory by lot, ingredient, supplier, or allergen.
18. Filter all lots, available, low-stock, expiring-soon, and on-hold.
19. Receive an ingredient with required name and quantity.
20. Auto-generate an internal lot ID or enter one manually.
21. Detect duplicate internal lot IDs.
22. Record supplier and supplier lot code.
23. Record receipt and expiry dates.
24. Record quantity with a unit.
25. Record optional per-unit cost in rupees.
26. Record storage location.
27. Record multiple allergen and cross-contact notes.
28. Record packaging or receiving context.
29. Link inventory lots to the supplier directory.
30. Display current quantity and status.
31. Trace an ingredient lot forward from inventory.
32. Mark fully consumed lots depleted when a production run uses them.

## Production and dispatch

33. Filter runs by all, released, on-hold, or dispatched status.
34. Search production runs by batch code or product.
35. Create a production record with product name and output quantity.
36. Auto-generate a batch code or set one manually.
37. Detect duplicate batch codes before stock changes.
38. Record output unit.
39. Record waste or rejected quantity.
40. Choose a manual demo run status.
41. Select one or more available ingredient lots.
42. Enter the quantity consumed from each selected lot.
43. Validate entered consumption against current lot quantity.
44. Deduct used quantities from inventory.
45. Preserve ingredient lot IDs and consumed quantities on the batch.
46. Record a production note or recipe revision note.
47. Add a dispatch note for a released batch.
48. Validate dispatch quantity against produced units, waste, and prior dispatches.
49. Record a trade destination without individual customer contact data.
50. Record dispatch date and delivery reference.
51. Reconcile units sent against batch output.
52. Mark a fully dispatched batch as dispatched.
53. Browse a destination-level dispatch ledger.
54. Trace a batch backward to its input lots.
55. Trace a lot forward to all linked production runs.
56. Display connected dispatch notes during a trace.
57. Run a mock trace exercise using a sample ingredient lot.
58. Clearly label mock trace as local-only with no messages sent.

## Quality, suppliers, and records

59. Record fridge/freezer, packaging, sanitation, inspection, release, or other checks.
60. Record a reading or free-text result.
61. Attach a check to a batch or keep it general.
62. Record a result label and shift note.
63. Move a linked batch to on-hold when a failed/hold check is recorded.
64. Browse local quality records in a table.
65. Export the quality log as CSV.
66. Browse suppliers and their linked receiving records.
67. Add a supplier record with optional contact.
68. Show sample verification labels as unverified demo placeholders.
69. Export a JSON workspace backup with schema and timestamp.
70. Restore a compatible JSON backup after confirmation.
71. Restore the fictional starter workspace after confirmation.
72. Maintain a capped local activity log for key changes.
73. Show an empty-state or no-match message when filtered data has no results.
74. Warn that local trace records are not a compliance or recall submission.
