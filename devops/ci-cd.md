# CI/CD Pipeline

## CI CI Pipeline

### Continuous Integration
  * Automated process for devs where new code changes to an app are regularily: *built, tested, and merged* to a shared branch in a repo
    * As opposed to where code from multiple branches that may conflict with each other are merged in a process that takes a long time
  * Process
    * Push to repo
    * Static analysis 
      * done on the code base without running the software
      * checks for bugs and ensures code conforms to standard formatting and styling
    * Packaging and deployment
      * built, packaged, and sent to a test or staging environment (that mimics production)
  * Requirements
    * Write automated tests for each new feature, improvement, or bug fix
    * CI server to monitor the main repo and run tests automatically for every new commits pushed
    * Merging changes to the repo often as possible
      * small, frequent changes are easier to test and refactor than large code commits

### Testing
  * Unit tests
    * Verifies the behavior of individual methods and functions
  * Integration tests
    * makes sure multiple components behave correctly together
  * Acceptance tests
    * Similar to integration tests, but focuses on business cases rather than components
  * UI tests
    * makes sure the application functions correctly from the user perspective

* Continous Delivery
  * where code is automatically released to repository or container registry
    * code in this stage is always ready for deployment to production environment
  * Requirements
    * CI that tests code for bugs
    * Setup deployment to be automated
    * Implement feature flags so incomplete features don't affect production

* Continuous Deployment
  * where code from repository is automatically deployed to production where its usable by customers
  * Requirements: same as the ones in delivery

* Continuous Testing
  * Executed in the CI/CD pipeline

### Process (in stages):
* Build
* Test
* Release (to repository)
* Deploy (to prodcution)

## CI/CD tools
* Jenkins
* CircleCI
* AWS
* CodeBuild
* DevOps
* Bamboo
* Travic CI
