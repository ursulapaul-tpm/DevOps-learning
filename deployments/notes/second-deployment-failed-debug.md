# Deployment Experience — Failed & Debugged

**Date:** 29th May 2026
**Environment:** Demo
**Status:** Failed → Fixed → Redeployed Successfully
**Tools used:** GitHub, GitHub Actions, ArgoCD

---

## What Happened
Deployment to demo failed because a developer forgot to 
add an application dependency. Docker could not run 
because a required file was missing from the container.

---

## How I Debugged It
1. Opened the deployment logs on GitHub
2. Read the error message carefully
3. Identified the missing file causing Docker to fail
4. Spoke to the developer responsible
5. Developer added the missing file
6. Deleted the failed release and tag
7. Created a new release and tag
8. Redeployed successfully ✅

---

## Full Deployment Process

### Step 1: Developer Setup
- Developers are given a dedicated branch
- All their changes go into that branch

### Step 2: Create a Tag and Release
1. Select the developer branch as the target
2. Create a tag e.g. `v0.0.21-feature-name`
3. Create a release from that tag
4. Generate release notes
5. Publish the release

### Step 3: Trigger Deployment
1. Go to **Actions** tab
2. Select **"app build push deploy"** workflow
3. Click **"Run workflow"**
4. Fill in the form
5. Click **"Push"**

### Step 4: Verify
1. Check GitHub Actions workflow completes ✅
2. Check **ArgoCD** for pod health ✅
3. Notify developer to test their changes ✅

---

## What I Learned

**Reading logs is a superpower** — the error message 
told me exactly what was wrong. Learning to read logs 
quickly is one of the most valuable DevOps skills.

**Docker basics** — Docker packages an application and 
all its dependencies into a container. If something is 
missing the container cannot start and the deployment fails.

**Always verify before redeploying** — confirm the fix 
is in place before creating a new release and tag.

**Communication is key** — quickly identifying who owned 
the missing file and communicating clearly got this 
resolved fast.

---

## Key Concepts From This Experience

| Concept | What it means |
|---------|--------------|
| **Docker** | Packages app and dependencies into a container |
| **Missing dependency** | A required file/package not included in the build |
| **Pod health** | ArgoCD shows if the app is running correctly |
| **Rollback** | Deleting a bad release and redeploying a good one |
| **Log reading** | Finding error messages to identify root cause |

---

## Questions to Explore Next
- How do we catch missing dependencies before deployment?
- Can we add automated checks before a release is published?
- What does a healthy vs unhealthy pod look like in ArgoCD?
- How do we set up alerts for failed deployments?
