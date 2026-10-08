# Native GitHub achievement roadmap

Verified against the public [Achievements view](https://github.com/mehmeterendereli?tab=achievements) on **2026-10-08**. This is an engineering roadmap, not a badge display: it does not reproduce achievement artwork or claim unearned levels.

GitHub's official [profile documentation](https://docs.github.com/articles/about-your-profile) confirms that achievements are native profile elements, but GitHub does not publish the complete tier threshold table. Thresholds below are therefore labeled **community-observed** and linked to their sources.

## Verified inventory and next honest step

| Achievement | Publicly verified state | Next condition | Concrete work | State |
|---|---|---|---|---|
| **Pull Shark** | Visible, **x3** | x4 is community-observed at 1,024 merged pull requests; exact current count is **UNKNOWN** | Prioritize real, maintainable fixes in projects already used; never split work merely to increase PR count | WORKING |
| **Pair Extraordinaire** | Visible, **x2** | x3 is community-observed at 24 coauthored merged pull requests; exact current count is **UNKNOWN** | Credit a human coauthor only when authorship is real and the shared change is merged | OPPORTUNISTIC |
| **Quickdraw** | Visible | No tier target | No optimization needed | VERIFIED |
| **YOLO** | Visible | No tier target | Do not optimize for unreviewed merges; review quality takes priority | VERIFIED |
| **Galaxy Brain** | Not displayed | Base achievement is community-observed at 2 accepted answers in eligible repository Discussions | Prepare accurate answers only where the question can be resolved from evidence; first package below | READY_FOR_USER_APPROVAL |
| **Starstruck** | Not displayed | Base achievement is community-observed at 16 stars in one personal public repository | Make one useful project easier to try and share; current observed baseline is OpenRelax 1, VORMETRA Slice 0 | WORKING |
| **Public Sponsor** | Not displayed | Sponsorship of qualifying open-source work | Excluded: the project rule is no spending for achievements | EXCLUDED |

“Not displayed” means only that the achievement was absent from the public view at verification time. It is not a claim about private history, progress counters or future eligibility.

## First Galaxy Brain answer package

**Target:** [OrcaSlicer Discussion #16164 — “How to close the Top Layer?”](https://github.com/OrcaSlicer/OrcaSlicer/discussions/16164)

**Observed state:** unanswered, zero replies on 2026-10-08.

**Evidence:** OrcaSlicer's current [Top/bottom shells documentation](https://github.com/OrcaSlicer/OrcaSlicer/wiki/strength_settings_top_bottom_shells).

**Limit:** the question does not include a 3MF/project file, so the physical result cannot be reproduced from the available evidence.

### Ready-to-post answer

Changing the number of outer walls will not close a missing top skin; wall loops and top solid layers are separate settings.

1. In **Strength → Top/bottom shells**, set **Top shell layers** to at least 3. As a diagnostic starting point at 0.20 mm layer height, try 4 layers (0.8 mm total).
2. Keep **Top surface density** at 100%.
3. Slice again and use **Preview → Line Type**. If no top-surface toolpaths appear over the opening, the model may be open/non-manifold or that region may not be recognized as a top surface. Repair the mesh or share the 3MF/project so the geometry and settings can be inspected together.
4. If the preview contains complete top-surface paths but the printed part still has small holes, this is more likely a flow, temperature, speed, cooling or insufficient-support-under-the-skin issue than a missing slicer surface. If the holes occur only where the skin meets the perimeter, try the documented **25–30% top/bottom infill-wall overlap** range.

The OrcaSlicer documentation also notes that **Top shell thickness** can force extra top layers when the configured layer count would otherwise produce a thinner shell.

**Publication state:** not posted and not accepted. Posting to a third-party project requires the user's approval. Even if posted, this would be only one candidate answer; an eligible answer must be accepted by the question author before it counts toward Galaxy Brain.

## Threshold references

- [GitHub Docs — About your profile](https://docs.github.com/articles/about-your-profile)
- [GitHub Community — achievement badges discussion](https://github.com/orgs/community/discussions/18190)
- [GitHub Community — achievement thresholds discussion](https://github.com/orgs/community/discussions/209029)
- [Community-maintained achievement reference](https://github.com/christianalberto/github-profile-achievements)

The GitHub Community discussions and the community-maintained reference are observations, not official guarantees. GitHub's own Community Discussions stopped awarding Galaxy Brain in February 2024; eligible repository Discussions remain the intended target.
