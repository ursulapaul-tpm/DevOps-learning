# My First Deployment Experience

**Date:** 28th May 2026
**Environments:** Production (prod) and Demo
**Tools used:** GitHub Actions, ArgoCD, Lens
**Type:** Manual Deployment by Tag

---

## Tools Overview

**GitHub Actions** — triggers and runs the deployment workflow
**ArgoCD** — monitors and syncs the deployment to the cluster
**Lens** — Kubernetes dashboard used to check logs and pod health

---

## Step by Step Deployment Process

### Step 1: Create a Release Tag
1. Go to **Code** tab in GitHub
2. Click **Tags** → **Releases**
3. Copy the previous version as a reference
4. Click **"Draft a new release"**
5. Select tag e.g. `v0.0.20-feature-name`
6. Select the target branch
7. Fill in the release title
8. Click **"Generate release notes"**
9. Click **"Publish release"**

### Step 2: Trigger the Deployment
1. Go to **Actions** tab in GitHub
2. Select the **"app build push deploy"** workflow
3. Click **"Run workflow"**
4. Fill in the form details
5. Click **"Push"**

### Step 3: Verify the Deployment
1. Wait for the GitHub Actions workflow to complete ✅
2. Open **ArgoCD** and check the app is synced and healthy ✅
3. Check **Lens** for pod logs and health ✅

---

## Key Concepts Learned

**Tag based deployment** — deployments are triggered by 
release tags, not just branch pushes. This gives better 
version control and traceability.

**Release notes** — auto generated notes that track what 
changed in each deployment. Important for audit trails.

**ArgoCD** — a GitOps tool that watches your repo and 
makes sure what's running in the cluster matches 
what's in GitHub.

**Lens** — a Kubernetes IDE that gives a visual view 
of your cluster, pods, and logs.

---

## What Went Well
- Deployment went through successfully on first attempt ✅
- Both prod and demo environments updated ✅
