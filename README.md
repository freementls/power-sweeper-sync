# Power Sweeper live-site mirror

One push from the work computer updates ScottBrooks4, Azure, and freementls.

On the work computer, `origin` is `ScottBrooks4/power_sweeper`. Push the live site branch:

```bash
git push origin from-azure
```

That push does three things:

1. Updates `ScottBrooks4/power_sweeper` branch `from-azure`.
2. Starts **Build and deploy PHP app to Azure Web App - powersweeperfree** on that branch. The runner deploys to the `powersweeperfree` app, so the work network does not need to reach Azure.
3. The home server copies that same commit onto `freementls/power_sweeper` branch `azure-live` within a minute (`scripts/mirror_azure_live.sh` in the private repo).

`azure-live` is the live wwwroot snapshot. It is not `freementls/power_sweeper` `main`, and the copy never pushes `main`.

GitHub Actions on the freementls account are locked because of a billing issue, so this repository's workflow cannot run the copy yet. After that lock is cleared, run **Mirror live site to freementls** here. The workflow is the same copy.
