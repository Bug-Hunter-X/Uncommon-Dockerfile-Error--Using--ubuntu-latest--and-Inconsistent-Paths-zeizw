# Uncommon Dockerfile Error: Using `ubuntu:latest` and Inconsistent Paths

This repository demonstrates a common but subtle error in Dockerfiles: using `ubuntu:latest` and potential path inconsistencies.  The original `Dockerfile` shows these issues. The `DockerfileFixed` demonstrates the corrected version.

**Problem:**
*   Using `ubuntu:latest` is bad for production; it can change, breaking your builds.
*   The original Dockerfile incorrectly uses `/app/main.py` which might not match the application's actual location.

**Solution:**
*   Use a specific image version like `ubuntu:22.04` for better reproducibility.
*   Clearly define the application location and path to the main script in the Dockerfile.

**How to Reproduce:**
1.  Clone this repository.
2.  Build the original Dockerfile: `docker build -t faulty-app .`
3.  Attempt to run the faulty container.  You'll likely run into issues.
4.  Build the corrected Dockerfile: `docker build -t fixed-app -f DockerfileFixed .`
5.  Run the corrected container.  This should run without errors.
