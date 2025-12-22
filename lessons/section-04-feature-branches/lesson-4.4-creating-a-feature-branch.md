# Lesson 4.4: Creating a Feature Branch

## Why This Lesson?

You've protected `main`, so you can't commit directly anymore. Now you need to create a feature branch—and a workspace connected to it—so you can actually get work done.

The good news? Fabric makes this easy with the **Branch out** feature.

---

## Overview

In this lesson, you will:

- Create a feature branch using Fabric's "Branch out" feature
- Get a new workspace connected to your branch
- Make changes and commit to your branch
- Create a pull request to merge back to `main`

**Estimated Time:** 15-20 minutes

**Prerequisites:**
- Completed Lesson 4.3 (branch protection configured)

---

## Create a Feature Branch

Let's create a branch to work on a new feature—we'll add a small enhancement to our notebook.

1. Go to your **Development** workspace (`FabricDevOps-Workshop-Dev`)
2. Click **Source control** in the top menu
3. Click **Branch out** (or look for the branch icon/dropdown)
4. Enter the following:
   - **Branch name**: `feature-add-greeting`
   - **Workspace name**: Fabric will suggest a name (you can shorten it)
5. Click **Branch out** to create the branch and workspace

> ✅ Fabric creates both the Git branch AND a new workspace connected to it—in one step!

Verify you're in your new workspace:
- Check the **Source control** panel—it should show you're on the `feature-add-greeting` branch
- Your workspace has copies of all the items from `main`

---

## Make Your Changes

Now let's make a change in our feature branch.

1. In your new workspace, open the `01-hello-fabric` notebook
2. Add a new cell at the top of your notebook with this code:

   ```python
   # Display a greeting
   print("Welcome to the Fabric DevOps Workshop!")
   print("=" * 40)
   ```

3. Run the new cell to make sure it works—you should see your greeting message

> 💡 **This is your inner loop!** You're working in isolation—nobody else is affected by your changes.

---

## Commit to Your Branch

Now let's save our work to Git.

1. Click **Source control** in the top menu
2. You should see your notebook has uncommitted changes
3. Enter a commit message: `Add greeting message to notebook`
4. Click **Commit**

> ✅ You've successfully committed to a feature branch. The `main` branch is unchanged.

---

## Create a Pull Request

Your feature is complete. Time to merge it back to `main`.

> 💡 **Pull requests are a Git concept, not a Fabric feature.** Everything in this section happens in GitHub (or Azure DevOps), not in Fabric. PRs work the same way whether you're merging Fabric items, Python code, or any other files tracked in Git. This is the universal workflow for collaborating with Git.

1. Open [GitHub](https://github.com) in your browser and navigate to your repository
2. GitHub may show a banner: "feature-add-greeting had recent pushes" with a **Compare & pull request** button—click it
   
   Or manually: Click **Pull requests** > **New pull request** > set **base**: `main` and **compare**: `feature-add-greeting`

3. Add a title: `Add greeting message to notebook`
4. Click **Create pull request**
5. Review the **Files changed** tab to see your changes
6. Click **Merge pull request**, then **Confirm merge**

> 💡 **This is where code reviews happen.** In a team environment, you'd configure branch policies to require approvals before merging. Teammates would review the **Files changed** tab, leave comments, and approve (or request changes). We skipped that setup for this workshop, but this is the step where that review process would occur.

> ✅ Your changes are now in `main`!

7. Click **Delete branch** (optional but recommended—the branch served its purpose)

---

## Sync the Dev Workspace

Your changes are in `main`, but the Dev workspace doesn't know yet.

1. Navigate back to your original **Development** workspace (`FabricDevOps-Workshop-Dev`)
2. Click **Source control**—you should see the workspace is behind the Git repo
3. Click **Update all** (or **Pull**) to sync the changes
4. Open the `01-hello-fabric` notebook and verify your greeting message is there

> ✅ The Dev workspace now has your merged changes.

---

## Clean Up Your Feature Workspace

Your feature workspace was temporary—you can delete it now.

1. Go to **Workspaces** in the left navigation
2. Find your feature workspace and click **...** → **Workspace settings**
3. Scroll down and click **Delete this workspace**
4. Confirm the deletion

> 💡 **Workspaces are cheap to create and delete.** Don't keep old feature workspaces around—they clutter your environment.

---

## The Complete Flow

Here's what you just did:

```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                     │
│   1. BRANCH OUT           2. DEVELOP            3. MERGE            │
│   ┌─────────────────┐    ┌─────────────────┐   ┌─────────────────┐  │
│   │ Create branch   │    │ Work in your    │   │ Create PR       │  │
│   │ + workspace     │───►│ feature         │──►│ Merge to main   │  │
│   │ (Branch out)    │    │ workspace       │   │ Delete branch   │  │
│   └─────────────────┘    └─────────────────┘   └─────────────────┘  │
│                                                                     │
│   4. SYNC                 5. CLEAN UP                               │
│   ┌─────────────────┐    ┌─────────────────┐                        │
│   │ Update Dev      │    │ Delete feature  │                        │
│   │ workspace       │    │ workspace       │                        │
│   └─────────────────┘    └─────────────────┘                        │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Summary

In this lesson, you:

- ✅ Created a feature branch using Fabric's **Branch out** feature
- ✅ Made changes in your isolated workspace
- ✅ Committed to your feature branch
- ✅ Created a pull request and merged to `main`
- ✅ Synced the Dev workspace with the merged changes
- ✅ Cleaned up the feature workspace

### Key Takeaways

1. **Branch out does the heavy lifting** — Creates branch + workspace in one step
2. **Work in isolation** — Your changes don't affect anyone until you merge
3. **Pull requests are the gateway** — All changes to `main` go through PRs
4. **Clean up after yourself** — Delete feature branches and workspaces when done

---

**Previous:** [Lesson 4.3: Configuring Branch Policies](lesson-4.3-configuring-branch-policies.md)  
**Next:** Lesson 4.5 *(Coming Soon)*
