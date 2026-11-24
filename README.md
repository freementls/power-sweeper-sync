# Power Sweeper live-site mirror

One push from the work computer updates ScottBrooks4, Azure, and freementls.

On the work computer, `origin` is `ScottBrooks4/power_sweeper`. Push the live site branch:

```bash
git push origin from-azure
```

That push does three things:

1. Updates `ScottBrooks4/power_sweeper` branch `from-azure`.
2. Starts **Build and deploy PHP app to Azure Web App - powersweeperfree** on that branch. The runner deploys to the `powersweeperfree` app, so the work network does not need to reach Azure.
3. This repository's mirror job then force-updates `freementls/power_sweeper` branch `azure-live` to that same commit.

`azure-live` is the live wwwroot snapshot. It is not `freementls/power_sweeper` `main`, and this job never pushes `main`.

GitHub checks Scott about every five minutes, and the job can also be run by hand with **Mirror live site to freementls**.
