# jenkins-student-assignment

Experiment No. 5 – Automated CI/CD Pipeline with Jenkins.

- `index.js` – sample Hello World application
- `Jenkinsfile` – declarative pipeline: Build → Test → Package (+ post success message)

The Jenkins job `Assignment-Pipeline` uses *Pipeline script from SCM* and polls this repo every 2 minutes (`H/2 * * * *`).
