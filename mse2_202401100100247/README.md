# KIET MSE-II Docker Practical — Set A

**Student:** SHUBHAM KUMAR  
**Roll number:** 202401100100247  
**Institution:** KIET Group of Institutions

## Starter-file limitation

The repository did not include the examination's original starter files. This is a clearly identified practice reconstruction: the final Dockerfile and Compose file below are corrected configurations, not the original files with the four examination mistakes. No original error output is reproduced or claimed. Capture Q1(a–d) E1 from the real supplied starter files if they become available; otherwise report that original E1 evidence could not be collected.

## Q1 — Four debugging concepts

For each item, E1 must be an actual error/output or other problem evidence from the original starter file. The original source is unavailable here, so do not substitute invented output. The explanations below are original descriptions; E3 commands validate the corresponding corrected setup.

| Item | E1 — problem evidence | E2 — explanation | E3 — correction and verification |
|---|---|---|---|
| (a) Misspelt Compose keyword | Not reproducible without the original Compose file and its actual output. | Compose only recognizes its defined keys. A misspelling can prevent the file from being interpreted as intended, so use the exact keys `services`, `build`, `image`, `container_name`, `ports`, and `restart`. | Use the corrected `docker-compose.yml`; run `docker compose config --quiet` and then `docker compose up -d`. |
| (b) Misspelt Dockerfile image-reference word | Not reproducible without the original Dockerfile and its actual build output. | The `FROM` line must name a valid base image. A misspelt image reference does not select the intended Nginx image; the corrected reference is `nginx:alpine`. | Use `FROM nginx:alpine`; run `docker compose build`. |
| (c) Incorrect `COPY` source filename | Not reproducible without the original Dockerfile/build context and its actual build output. | `COPY` reads its source from the build context. If that filename is wrong or absent, the page cannot be copied into the image; the source here is `index.html`. | Use `COPY index.html /usr/share/nginx/html/index.html`; run `docker compose build`. |
| (d) Incorrect port mapping | Not reproducible without the original mapping and observed connection result. | Port mapping is written host-side first and container-side second. Nginx listens on container port 80, so the requested host mapping is `8047:80`. | Use `8047:80` (parameterized here as `${HOST_PORT}:80`); run `docker compose up -d` and `curl http://localhost:8047`. |

## Run and verify the practical

From the project directory, set the requested terminal variables and prompt:

```bash
export ROLL_NO=202401100100247
export HOST_PORT=8047
export SECOND_PORT=8048
export PS1='[$ROLL_NO \t] \w $ '
```

These exports affect only the current terminal. The Compose environment uses `ROLL_NO` from `.env`; do not hardcode it in Compose.

### Q1 — corrected setup

```bash
docker compose config --quiet
docker compose build
docker compose up -d
curl http://localhost:8047
```

### Q2 — second container (manual Docker run, not Compose)

Run this after the image has been built. Capture the terminal output and screenshots before cleanup.

```bash
docker run -d --name second-202401100100247 -p 8048:80 web-202401100100247:v1
curl http://localhost:8048
docker ps
```

After capturing Q2 evidence, remove only the Q2 container:

```bash
docker rm -f second-202401100100247
```

### Q3(i) — bind-mounted page

`site/index.html` is the original page copied into `site/` with the requested paragraph added. The bind mount is already configured in Compose.

```bash
docker compose up -d
curl http://localhost:8047
```

Confirm the response contains `Edited without rebuild`. Do not run a build for this check.

### Q3(ii) — Compose environment variable

```bash
docker compose up -d
docker exec web-202401100100247 printenv STUDENT_ROLL
```

Expected value: `202401100100247`.

### Q4 — health check

```bash
docker compose up -d
sleep 20
docker compose ps
```

The health check runs inside the web container, where Nginx listens on port 80, so it probes `127.0.0.1:80`. `HOST_PORT` is the host-side published port and is not the port the container uses to reach its own Nginx process.

### Final verification

```bash
docker images
docker ps
docker compose ps
curl http://localhost:8047
docker exec web-202401100100247 printenv STUDENT_ROLL
```

The Compose-managed container is named `web-202401100100247` and uses image `web-202401100100247:v1`. The site bind mount intentionally serves `site/index.html`, including `Edited without rebuild`.

## Codespaces port forwarding

In the Codespaces **Ports** panel, forward port **8047** for the main website. Forward **8048** only while the Q2 second container is running. Keep both ports **Private** unless public access is explicitly required. Open the forwarded port's **Open in Browser** link (or copy its forwarded URL) to view the site; the 8048 URL works only during Q2.

## Evidence and completion

See [evidence/README.md](evidence/README.md) for the screenshot checklist, capture points, and the Q1 evidence limitation. Do not present terminal examples or this reconstruction as evidence from the missing original starter files.

## Verification completed in this Codespace

Compose configuration validation and image build succeeded. The main website responded on port 8047, the manually started second container responded on port 8048, the bind-mounted response contained `Edited without rebuild`, and `STUDENT_ROLL` was `202401100100247`. After the 20-second health-check wait, `docker compose ps` reported the main service as healthy.

The Q2 second container is intentionally still running so its real `docker ps` and port-8048 evidence can be captured. After taking the Q2 screenshots, run `docker rm -f second-202401100100247`. The original Q1 E1 errors remain unavailable because the exam starter files were not present.
