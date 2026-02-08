# sample-static-spring-kotlin

**One repo: static frontend + Spring Boot (Kotlin/Gradle) API.**

## Build & run

**With [OctoPilot pipeline tools](https://github.com/octopilot/octopilot-pipeline-tools) (`op`)** — recommended for local/Mac:

```bash
docker run -d -p 5001:5000 --restart=unless-stopped --name registry registry:2  # once
op build-push
docker run -p 8081:8080 sample-static-spring-kotlin-api
docker run -p 8080:8080 -e PORT=8080 sample-static-spring-kotlin-frontend
```

Or with Skaffold: `skaffold build` then the two `docker run` lines above.

Open http://localhost:8080. Set API URL to `http://localhost:8081`.

## Deploy

`skaffold build --file-output build.json` or `op push` (set `--default-repo` or use a `.registry` file).
