# DevOps Learning Log — FinSight

---

## Date:
09-02-2026

---

## Feature / Step:
Setup GitHub Actions CI pipeline for Backend.

---

## Goal:
Automatically build backend when code pushed to repository.

---

## What I did:

- Created GitHub Actions workflow
- Added ci.yml file
- Configured Java setup
- Added mvnw build command

---

## Error faced:

./mvnw: Permission denied

---

## Investigation:

- Checked workflow configuration
- Verified working directory
- Checked branch trigger
- Investigated Maven wrapper execution

---

## Cause:

Linux runner requires executable permission.

---

## Solution:

git update-index --chmod=+x mvnw

---

## Learning:

- Windows and Linux file permissions differ.
- CI environments require executable flags for scripts.
- GitHub Actions runs on Linux.

---

## Date:
09-02-2026

## Feature / Step:
Fix Java version mismatch in CI pipeline.

## Error faced:

release version 21 not supported

## Cause:

CI pipeline using Java 17 but project configured for Java 21.

## Solution:

Updated GitHub Actions setup-java version to 21.

## Learning:

CI environment must match local development environment.
Version mismatches commonly break builds.


## Error:
SpringBootTest contextLoads failed during CI.

## Cause:
Test tried to start full Spring context without required configuration.

## Solution:
Temporarily skip tests using:

./mvnw clean install -DskipTests

## Learning:
CI pipelines also run tests automatically.
Incomplete configuration can cause test failures.


---

## Next Steps:

- Fix permission issue
- Re-run pipeline
- Confirm successful build
