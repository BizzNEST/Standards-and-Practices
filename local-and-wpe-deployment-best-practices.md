# Best Local and WPE Deployment Practices

### Please be sure to talk to a lead or senior before pushing to any environment.

## Purpose of this Document

- To outline best practices for setting up, maintaining, and deploying WordPress projects both locally and to WP Engine (WPE). 
- By following these guidelines, developers can ensure consistent and efficient workflows, maintain high code quality, and minimize issues during deployment.

## When to Push / Pull from WPE to Local (Vice Versa)?


### Differences Between Development, Staging, and Production Environments

#### Development:

##### Purpose:

* Used by developers to build and test new features or fixes.
* Focuses on rapid iteration and experimentation.
*  When you need to edit plugins, themes, or custom code.
*  If there's an error that cannot be resolved within WP Admin.
*  To test plugins that could potentially disrupt production, development, or staging environments.

##### Characteristics:

* Code: Often includes the latest, sometimes unstable code changes.
* Data: Typically uses mock or sample data, not real user data.
* Access: Usually has fewer security restrictions; accessible by the development team.
* Configuration: This may vary greatly from one developer’s setup to another and from other environments.

##### When to Push to Staging:

* Code Freeze: The code is stable, with new features implemented and bugs fixed.
* Feature Complete: All planned features for the current development cycle are implemented.
* Internal Testing: Initial testing has been completed and significant issues have been resolved.

#### Staging:

##### Purpose:

* Acts as a final testing ground before code is deployed to production.
* Mimics the production environment as closely as possible to catch issues that might not appear in development.

##### Characteristics:

* Code: Should mirror the code that is intended for production, with final versions and bug fixes applied.
* Data: Uses data that is similar in structure to production data, but often anonymized or scrambled.
* Access: Generally accessible by QA teams and sometimes stakeholders for testing.
* Configuration: Configured to closely resemble the production environment to ensure that tests are accurate.

##### When to Push to Production:

* Successful Testing: All tests in staging pass, including integration, performance, and user acceptance tests.
* Bug Fixes Applied: Any issues identified during staging testing have been resolved.
* Approval: Stakeholders or project managers have reviewed and approved the release.
* User Readiness: Ensured that the code and system are ready for real-world use and user data.

#### Production:

##### Purpose:

* The live environment where the application is available to end users.
* Must be stable, secure, and performant.

##### Characteristics:

* Code: Includes thoroughly tested and stable code that has been through development and staging.
* Data: Contains real user data; data integrity and security are crucial.
* Access: Restricted to authorized personnel to ensure security and maintain the integrity of the live system.
* Configuration: Highly optimized for performance and reliability; issues in this environment can directly affect end users.

### Connecting To Local

- Once you log in, you can connect to your WPE account.

![image](https://github.com/user-attachments/assets/154d516d-e829-4c07-9769-cc1289e27c81)


![image](https://github.com/user-attachments/assets/4911c6cb-f70f-40fd-a8f4-e39d500137b2)

### Connecting to a Website

- You can create a site from a WPE account and pull all the website files (make sure to pull the database as well)
  
![image](https://github.com/user-attachments/assets/1f5a706f-07dc-4e26-ae2e-19cab6a7ecc0)

- Pulling can take some time, especially if it's your first time pulling a site. Local will generate an SSH key for WPE, so you will likely receive an email regarding this.

![image](https://github.com/user-attachments/assets/3ee4b35e-e624-4dcc-9996-470a5e271953)

### Pulling + Pushing Sites

- Once the site is successfully pulled, you can click on the VS Code button, and VS Code will open with all of the WordPress files.

![image](https://github.com/user-attachments/assets/df66ffb9-01a6-4d99-8d72-8e7a68089c08)

- After making changes to the codebase, you can pull/push from Local.

![image](https://github.com/user-attachments/assets/48ce547f-7ab6-42c5-bdad-4567a135780d)

- Before pushing anything to an environment, make sure to confirm / seek approval of the changes with a Lead and the team. Additionally, ensure you do not push your local database to the remote site (outlined in red as unchecked).

<img width="362" alt="Screen Shot 2024-08-22 at 10 48 44 AM" src="https://github.com/user-attachments/assets/f0729e09-855a-4261-8497-14a4c8ca3e9a">
<img width="362" alt="Screen Shot 2024-08-22 at 10 41 44 AM" src="https://github.com/user-attachments/assets/49d803be-64b9-4442-a829-96147812e67e">

- The same pulling/pushing process can be done through WPE as well. This is usually done when you need to push from one environment to another, but typically we pull from backups created from these environments. (Make sure to get approval from a Lead)

<img width="1341" alt="Screen Shot 2024-08-22 at 10 57 20 AM" src="https://github.com/user-attachments/assets/635e06e8-4d80-4689-b48b-c33c199af363">
