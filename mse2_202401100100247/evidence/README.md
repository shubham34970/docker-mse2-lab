# Evidence checklist

Save genuine screenshots in this directory using the suggested filenames. Include the relevant command and its actual output in each capture. Do not create or edit screenshots to imply a result that was not observed.

| Suggested screenshot | Capture point / contents | Status |
|---|---|---|
| `S0-initial-files.png` | Show the created practice project files `.env`, `index.html`, `Dockerfile`, and `docker-compose.yml`. | Ready to capture; these are reconstructed files, not originals. |
| `Q1-a-E1-original-error.png` | Actual Compose error/problem from the original starter file. | Unavailable: original starter file was not in the repository. Do not fabricate. |
| `Q1-a-E2-explanation.png` | Your explanation of the misspelt Compose keyword. | Capture after writing/submitting your explanation. |
| `Q1-a-E3-correction.png` | Corrected Compose keys and successful `docker compose config --quiet`. | Configuration validation succeeded; capture the real terminal output. |
| `Q1-b-E1-original-error.png` | Actual Docker build error/problem from the original image reference. | Unavailable: original starter file was not in the repository. Do not fabricate. |
| `Q1-b-E2-explanation.png` | Your explanation of the misspelt image reference. | Capture after writing/submitting your explanation. |
| `Q1-b-E3-correction.png` | `FROM nginx:alpine` and successful `docker compose build`. | Image build succeeded; capture the real terminal output. |
| `Q1-c-E1-original-error.png` | Actual Docker build error/problem from the original `COPY` source. | Unavailable: original starter file was not in the repository. Do not fabricate. |
| `Q1-c-E2-explanation.png` | Your explanation of the incorrect `COPY` source filename. | Capture after writing/submitting your explanation. |
| `Q1-c-E3-correction.png` | Correct `COPY index.html ...` line and successful build. | Image build succeeded; capture the real terminal output. |
| `Q1-d-E1-original-error.png` | Actual problem evidence from the original port mapping. | Unavailable: original starter file was not in the repository. Do not fabricate. |
| `Q1-d-E2-explanation.png` | Your explanation of host-to-container port mapping. | Capture after writing/submitting your explanation. |
| `Q1-d-E3-correction.png` | Corrected `8047:80` mapping and successful `curl http://localhost:8047`. | Main page responded; capture the real terminal output. |
| `Q2-docker-run.png` | Successful `docker run` command/output for `second-202401100100247`. | Container is running; capture now, before cleanup. |
| `Q2-curl.png` | Successful `curl http://localhost:8048` response. | Verified; capture now, before cleanup. |
| `Q2-docker-ps.png` | `docker ps` showing both required container names. | Both containers were shown; capture now, before cleanup. |
| `Q3-i-volume-curl.png` | Compose volume entry and curl response containing `Edited without rebuild`; no image rebuild for this check. | Verified; capture the configuration and response. |
| `Q3-ii-environment.png` | Compose interpolation `${ROLL_NO}` and `docker exec ... printenv STUDENT_ROLL` output. | Verified expected value; capture the configuration and output. |
| `Q4-healthcheck.png` | Healthcheck configuration and `docker compose ps` showing the service as healthy after the wait. | Reported healthy after 20 seconds; capture configuration and status. |
| `codespaces-ports.png` | Ports panel showing forwarded ports and Private visibility. | Capture after configuring the Ports panel. |

Q1 E1 evidence is conditional on receiving the original examination starter files. The corrected reconstruction and its successful checks do not reproduce the original mistakes or their error messages.
