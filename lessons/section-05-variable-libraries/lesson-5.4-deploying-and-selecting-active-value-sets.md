# Lesson 5.4: Deploying and Selecting Active Value Sets

## Why This Lesson?

You said you don’t want to modify Test/Prod by hand—which is the right instinct.

That means:

- We edit the variable library in Dev
- We deploy changes forward through the deployment pipeline
- We configure each stage to use the correct **active value set**

Once that’s done, updates flow forward by automation.

---

## Overview

In this lesson, you will:

- Deploy the variable library and notebook to Test and Prod
- Set the active value set in each stage (`Test` uses `Test`, `Prod` uses `Prod`)
- Run the notebook in each stage and verify different behavior

**Estimated Time:** 10-15 minutes

**Prerequisites:**
- Completed Lessons 5.1–5.3
- A deployment pipeline with Dev → Test → Prod configured

---

## Deploy the Changes Forward

1. Open your deployment pipeline
2. Make sure the following items are included in the deployment:
   - `EnvConfig` variable library
   - Your updated notebook (`01-hello-fabric`)
3. Deploy from **Dev → Test**
4. Deploy from **Test → Prod**

> ✅ After deployment, the variable library item should exist in each stage’s workspace.

---

## Set the Active Value Set Per Stage

Now we tell each stage which value set to use.

1. In the **Test** stage workspace:
   - Open `EnvConfig`
   - Set the active value set to `Test`
   - Save
2. In the **Prod** stage workspace:
   - Open `EnvConfig`
   - Set the active value set to `Prod`
   - Save

> 💡 The active value set is stage configuration. Deployments generally don’t overwrite which set is selected.

> 💡 **Compare tip:** Changing which value set is active typically does *not* show up as “different from source” in deployment pipeline comparisons. But adding/removing variables or value sets (or renaming/reordering them) will.

---

## Run and Verify in Each Stage

1. In the **Test** stage workspace:
   - Open the notebook
   - Run the cell that generates/writes data
   - Verify the output shows `RunLabel = test` and writes to the `workshop_seed_test` table
2. In the **Prod** stage workspace:
   - Repeat
   - Verify `RunLabel = prod` and the output table is `workshop_seed_prod`

> ✅ Same notebook code, different behavior—driven by the stage’s active value set.

---

## What Changes Going Forward?

From here on out, treat the variable library like any other artifact:

- Update values in Dev (and commit)
- Deploy forward
- Don’t hand-edit Test/Prod

> ⚠️ If someone hand-edits variables or value sets in Test/Prod, your deployment pipeline comparisons may show the library as “different from source.” That’s a signal you’ve drifted.

---

## Summary

In this lesson, you:

- ✅ Deployed the variable library + notebook through Dev → Test → Prod
- ✅ Set `Test` and `Prod` as the active sets in their stages
- ✅ Verified stage-specific behavior without changing code

---

**Previous:** [Lesson 5.3: Using Library Variables in a Notebook](lesson-5.3-using-library-variables-in-a-notebook.md)  
**Next:** [Workshop Outline](../../README.md)
