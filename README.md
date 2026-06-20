# docker-voicebox

Automatically tracks releases of [jamiepine/voicebox](https://github.com/jamiepine/voicebox), builds CPU Docker images, and pushes them to GHCR.

## Image Registry

```
ghcr.io/<your-username>/docker-voicebox:latest
ghcr.io/<your-username>/docker-voicebox:<tag>   # e.g., v0.5.0
```

## Usage

```bash
docker pull ghcr.io/<your-username>/docker-voicebox:latest
docker run -p 17493:17493 ghcr.io/<your-username>/docker-voicebox:latest
```

Then visit http://localhost:17493

## Triggering Build

This repository uses **manual trigger**. When a new release is published upstream:

1. Subscribe to upstream notifications: On [jamiepine/voicebox](https://github.com/jamiepine/voicebox), click Watch → Custom → Releases.
2. After receiving an email notification, go to the Actions page of this repository.
3. Select **Build voicebox CPU image** → Run workflow.

The workflow will automatically check if a new version needs to be built. Previously built versions will be skipped.

## Notes

- Source code is cloned directly from the upstream specified tag, no forks, avoiding merge conflicts.
- The build artifact is a CPU-only image (based on the upstream original Dockerfile).
- Built tags are tracked in the `.last-built-tag` file.
- Follows the upstream MIT License.