# CI/CD Complete implementation
Build Pipeline and Deployment Pipeline

![image](https://github.com/user-attachments/assets/516fa81f-9da1-4b8e-b678-2ad6122eb577)

## Traditionals Builds
The traditional builds make the QA to spend more time to find bugs and the release is delay cause the code had an issue and it's also impossible to send back the code to the dev to fix it and respect the release delay.

![image](https://github.com/user-attachments/assets/ed780624-2133-4851-a923-b150d104bc0e)

Our goal is to be able to write the code and then send it to the QA and if there is an issue to be able to send it back immeditaly to the dev to fix it without impacting the release delay or without cause more problems.

## Continuous Integration
CI is a practice that helps to frequently integrate code changes into a central repository and then automate the Builds.

Here after a dev build his code we give immediatly to the build and it failed we send it back immeditaly to the dev in order to fix it and if it succeed, we send it to the QA and this allow the QA to find bugs faster, faster release, and improves the quality

![image](https://github.com/user-attachments/assets/90165fee-5804-4349-9ee0-50c1284d0208)

The first i do when i build a pipeline is to configure my Build so it trigger the code everytime a dev is writing a code and check for issue before moving to the QA

### Production Grade DevSecOps Build Pipeline
Now let's go deeper to the real workflow of the build pipeline
As of now in the market , this is a standard for the build pipeline in the devsecops

![image](https://github.com/user-attachments/assets/df020ca9-9af6-449c-8e95-ee353de77d93)

I- Stage 1: Build & Unit Test
- Generate Artifacts
- Unit test
- Tools: Maven
  
![image](https://github.com/user-attachments/assets/40808781-9c2a-4558-b2c1-811c5d81d56f)

II- Stage 2: Code Coverage
- How many lines of codes i tested?
- Unused code
- Tools: Jacoco

![image](https://github.com/user-attachments/assets/87bd1054-e296-4e34-bac8-337070ac4e52)

III- Stage 3: Software composition analysis
- Identify Vulnerabilities introduced by open-source or 3rd party libraries used in code
- Tools: OWASP Dependency-check

![image](https://github.com/user-attachments/assets/57dea6b1-58b1-4207-aee5-8fb87c42551d)

IV- Stage 4: Static Application Security Testing (SAST)
- Identify vulnerabilities in proprietary code
- Insecure coding practice
- Tools: Sonarqube

![image](https://github.com/user-attachments/assets/153fef1b-68fa-43d4-b83e-f238a48b040e)

V- Stage 5: Quality Gates
- Check if application meets the quality standards
- Tools: Sonarqube Quaility profile

![image](https://github.com/user-attachments/assets/78e27674-bddc-468d-a954-abeb1f20daf9)

VI- Stage 6: Build Docker Image
- Generate Deployable Artifact
- Tools: Dockerfile

![image](https://github.com/user-attachments/assets/bb3c7a0e-00ac-42a4-82e5-1ff68f776bc1)

VII- Stage 7: Scan Docker Image
- Identify vulnerability in image layers
- Tools: Trivy

![image](https://github.com/user-attachments/assets/0da05528-97a1-43e2-ab9b-7de9a86b88a6)

VIII- Stage 8: Smoke Test
- Verify if the image is built properly
- Determine if image/application is ready for testing
- Tools: Docker Container

![image](https://github.com/user-attachments/assets/8ec293dd-b7e8-4428-ab77-f1797f7b487e)
