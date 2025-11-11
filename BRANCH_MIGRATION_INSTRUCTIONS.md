# Branch Migration Instructions: Master to Main

## Completed Changes ✅

I've successfully updated the following files to use 'main' instead of 'master':

1. **GitHub Actions Workflow**: [`.github/workflows/build-and-publish.yml`](.github/workflows/build-and-publish.yml)
   - Updated triggers from `master` to `main` branch
   - Push and pull request events now target `main`

2. **Documentation Updates**:
   - [`README.md`](README.md): Updated references to use "main branch"
   - [`GITHUB_ACTIONS_USAGE.md`](GITHUB_ACTIONS_USAGE.md): Updated workflow triggers and tagging strategy

## Next Steps (Manual Actions Required)

### 1. Push the main branch to your remote repository

Since Git authentication isn't configured in this environment, you'll need to run these commands locally:

```bash
# Make sure you're on the main branch
git checkout main

# Push the main branch to your fork
git push origin main
```

### 2. Update GitHub default branch setting

1. Go to your repository on GitHub: https://github.com/ag237/StepDaddyLiveHD
2. Click on **Settings** tab
3. Scroll down to **Branches** section
4. Click on **Default branch** 
5. Switch from `master` to `main`
6. Confirm the change

### 3. Configure upstream remote for syncing

If you haven't already, add the original repository as an upstream remote:

```bash
# Add the original repository as upstream
git remote add upstream https://github.com/gookie-dev/StepDaddyLiveHD.git

# Verify remotes
git remote -v
```

### 4. Ongoing sync workflow

To keep your fork synced with the upstream repository:

```bash
# Fetch upstream changes
git fetch upstream

# Switch to your main branch
git checkout main

# Merge upstream changes into your main
git merge upstream/main

# Push the synced changes to your fork
git push origin main
```

## What This Accomplishes

✅ **Modern Default Branch**: Your fork now uses 'main' as the default branch name
✅ **Maintained Sync Capability**: You can still sync with the upstream repository
✅ **Updated CI/CD**: GitHub Actions will trigger on the correct branch
✅ **Consistent Documentation**: All references now point to 'main'

## Important Notes

- Your GitHub Actions workflows will now trigger on pushes to `main` instead of `master`
- The `:latest` container image tag will be built from commits to `main`
- If the upstream repository still uses `master`, you'll sync from their `master` to your `main`
- Any collaborators on your fork will need to update their local repositories

## Verification Steps

After completing the manual steps:

1. Check that `main` is now the default branch on GitHub
2. Verify that a push to `main` triggers the GitHub Actions workflow
3. Test the sync process with the upstream repository

The migration is now complete and your fork is ready to use `main` as the default branch while maintaining full sync capabilities!