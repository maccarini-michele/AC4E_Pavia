# Cursor Chat Recording

## 2026-06-20 — PR review/merge restrictions

**User:** Wants to be the only person able to review and merge PRs. Also needs this to work for existing PRs.

**User follow-up:** Gets message that the PR creator cannot review the PR.

**Diagnosis:**
- `.github/CODEOWNERS` already assigns all files to `@meleantonio`.
- Branch protection required code-owner review (`require_code_owner_reviews: true`) with `enforce_admins: true`.
- GitHub does not allow PR authors to approve their own PRs.
- With only one code owner who also authors PRs, merges were blocked.

**Fix applied (GitHub branch protection on `main`):**
- Set `enforce_admins: false` so repository admin (`meleantonio`) can merge without self-approval.
- Kept code-owner review requirement for participant PRs (only `@meleantonio` can satisfy approvals).
- Personal repos cannot use user-based bypass/restriction lists via API.

**Note:** Self-approval is still impossible on GitHub; owner merges via admin bypass instead.
