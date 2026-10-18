# AGENTS.md — Lexus Lavalink Container

## Project map
- Small container/deployment repository with a `Dockerfile` and `application.yml` for running Lavalink.
- Keep the container image, Java runtime, Lavalink artifact, configured server port, and deployment environment aligned.

## Docker and Lavalink rules
- Read both files before changing either one; settings can be coupled across the image and runtime configuration.
- Check the official Lavalink release/configuration documentation before changing Java compatibility, artifact download URLs, plugins, or configuration keys.
- Prefer reproducible, version-pinned artifacts when feasible. If following the latest release is intentional, explain the trade-off and check compatibility.
- Keep the container's exposed/listening port consistent with `application.yml` and the hosting platform.
- Never bake production passwords or API credentials into image layers or commit them to YAML. Use supported environment-variable configuration and deployment secrets.
- Enable audio sources and local-file access only when the deployment actually needs them.
- Do not change the container base image or Java major version without verifying Lavalink requirements.

## Validation
- Validate YAML syntax and use `docker build` or equivalent only when Docker is available.
- A successful image build does not prove Lavalink starts, authenticates, or can reach an audio source. State which checks were actually performed.