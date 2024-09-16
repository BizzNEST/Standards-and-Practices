# Best Local and WPE Deployment Practices

## Purpose of this Document

- To outline best practices for setting up, maintaining, and deploying WordPress projects both locally and to WP Engine (WPE). 
- By following these guidelines, developers can ensure consistent and efficient workflows, maintain high code quality, and minimize issues during deployment.

## When to Push / Pull from WPE to Local (Vice Versa)?

- When you need to edit plugins, themes, or custom code.
- If there's an error that cannot be resolved within WP Admin.
- To test plugins that could potentially disrupt production, development, or staging environments.

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
