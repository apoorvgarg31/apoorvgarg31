# Trigger Profile Update from Other Repos

Add this workflow to any repo to trigger a profile update on push:

```yaml
# .github/workflows/update-profile.yml
name: Trigger Profile Update

on:
  push:
    branches: [main, master]

jobs:
  trigger:
    runs-on: ubuntu-latest
    steps:
      - name: Trigger profile update
        uses: peter-evans/repository-dispatch@v2
        with:
          token: ${{ secrets.PROFILE_UPDATE_TOKEN }}
          repository: apoorvgarg31/apoorvgarg31
          event-type: update-profile
```

## Setup

1. Create a Personal Access Token (PAT) with `repo` scope
2. Add it as a secret named `PROFILE_UPDATE_TOKEN` to any repo you want to trigger updates from
3. Add the workflow above to that repo

The profile will update:
- Every 30 minutes automatically
- On push to any repo with the trigger workflow
- Manually via GitHub Actions UI
