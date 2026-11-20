# Temporary University PC — Safe Resume and Shutdown Workflow

**Assumption:** The computer's local files, Antigravity installation and session history may be removed at logout/restart. Check university IT policies before installing software or storing account credentials. This document does not claim the IDE itself will persist.

## Start a fresh session
1. Confirm the PC allows personal GitHub/Antigravity access and remote repositories.
2. Install/open Antigravity only in accordance with local admin/IT policies. Git does not back up the IDE's installation or global settings.
3. Open a terminal and choose a permitted scratch workspace. If your repo is not present:

```powershell
git clone https://github.com/SalmanAhmed11/Antiburnouttracker.git
cd Antiburnouttracker
```

4. If the repo is present, avoid cloning another copy. Review:

```powershell
git status
git remote -v
git branch -a
git pull --ff-only origin main
```

5. Open the **repository root** in Antigravity, not the parent directory. `AGENTS.md` should load automatically; read `docs/operations/CURRENT_STATE.md` and `docs/product/DECISION_REGISTER.md` explicitly.
6. If continuing an unmerged topic branch, use `git fetch --all --prune` and check out the matching remote branch rather than continuing work on the wrong branch.
7. Use the approved prompt under `prompts/` to start the next narrowly scoped task; check its stated gate against CURRENT_STATE.

## During the session
- Use a **topic branch** for each document review / implementation slice, not direct updates to `main`.
- Never paste personal API keys into an agent chat or check them into GitHub; use project-specific secret management outside repo.
- Preserve decisions in the decision register and supporting rationale/test evidence, not solely the chat.
- Keep relevant assets versioned in the approved design source and maintain stable links in docs.
- Don't automatically save full raw chat transcripts to a public repository. Store sanitised summaries, prompts that matter and change/evidence links.

## End every session before the PC resets

```powershell
git status
git add <reviewed-paths>   # Replace with explicit filenames, don't accidentally stage secrets
git diff --cached
git commit -m "docs: describe reviewed project decisions"
git push -u origin <your-topic-branch>
git status
```

- Verify that your latest commit and files are actually visible on GitHub. A local commit without a successful push is **not** protected from a PC reset.
- Update `docs/operations/CURRENT_STATE.md`, any changed decision/roadmap item and a short session note.
- Check whether the institution requires deleting local project copies or logging out; sign out of GitHub/Google/Antigravity browser accounts and remove stored credentials under institutional policy.
- Don't save browser or CLI tokens on a shared computer. Enable account 2FA. Do not upload university/user personal data to a public repository.

## Alternatives
- **GitHub Codespaces** offers a cloud-hosted environment accessible through the browser; GitHub personal accounts have limited included usage. It is an optional fallback for documentation/general code and is not Antigravity IDE itself, nor does it automatically solve native mobile emulator/device support.
- **github.dev** allows light GitHub repository editing in a browser, but is not a full Android/iOS build environment.
- For eventual device testing, a persistent authorised personal development machine or appropriate hosted build infrastructure may be more practical.

## Recovery if you forgot to push
Check remote branches/PRs from GitHub first. Git can recover only work present in a remote commit; content that existed exclusively in an erased workspace may be unrecoverable.
