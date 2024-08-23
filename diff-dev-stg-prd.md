# Differences Between Development, Staging, and Production Environments

### Please be sure to talk to a lead or senior before pushing to any environment.

## Development:

#### Purpose:

* Used by developers to build and test new features or fixes.
* Focuses on rapid iteration and experimentation.

#### Characteristics:

* Code: Often includes the latest, sometimes unstable code changes.
* Data: Typically uses mock or sample data, not real user data.
* Access: Usually has fewer security restrictions; accessible by the development team.
* Configuration: This may vary greatly from one developer’s setup to another and from other environments.

#### When to Push to Staging:

* Code Freeze: The code is stable, with new features implemented and bugs fixed.
* Feature Complete: All planned features for the current development cycle are implemented.
* Internal Testing: Initial testing has been completed and significant issues have been resolved.

## Staging:

#### Purpose:

* Acts as a final testing ground before code is deployed to production.
* Mimics the production environment as closely as possible to catch issues that might not appear in development.

#### Characteristics:

* Code: Should mirror the code that is intended for production, with final versions and bug fixes applied.
* Data: Uses data that is similar in structure to production data, but often anonymized or scrambled.
* Access: Generally accessible by QA teams and sometimes stakeholders for testing.
* Configuration: Configured to closely resemble the production environment to ensure that tests are accurate.

#### When to Push to Production:

* Successful Testing: All tests in staging pass, including integration, performance, and user acceptance tests.
* Bug Fixes Applied: Any issues identified during staging testing have been resolved.
* Approval: Stakeholders or project managers have reviewed and approved the release.
* User Readiness: Ensured that the code and system are ready for real-world use and user data.

## Production:

#### Purpose:

* The live environment where the application is available to end users.
* Must be stable, secure, and performant.

#### Characteristics:

* Code: Includes thoroughly tested and stable code that has been through development and staging.
* Data: Contains real user data; data integrity and security are crucial.
* Access: Restricted to authorized personnel to ensure security and maintain the integrity of the live system.
* Configuration: Highly optimized for performance and reliability; issues in this environment can directly affect end users.
