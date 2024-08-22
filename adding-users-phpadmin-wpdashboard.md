# Gaining Access To Site

- Allow users to gain access to the site's dashboard by themselves


## WPEngine Screen

1. Once you log into WPEngine make sure you are in the correct location where you will be working in: `Development` `Staging` or `Production`
[Development Location Example](/Images/stagingLocations.png)

2. After the correct location has been clicked you will want to click on `phpMyAdmin`
[Development Location Example](/Images/myphp:wpAdminLocation.png)

3. On left side there should be an image of a database that starts with -> `wp_name-of-site`(ex:wp_digitalnest)
[Development Location Example](/Images/databaseLocation.png)

4. Click on the `+` to expand and scroll down to `wp_users` and click on it
[Development Location Example](/Images/wp_userLocation.png)

5. The user we want to mess with will be at the very top of the database, click on `edit`
[Development Location Example](/Images/phpMainAdmin.png)

6. Once inside we will need to look for `User_pass`, this has a series of random ints and chars
[Development Location Example](/Images/phpUserPass.png)

7. Click  on `varchar(255)` to expand and look for `MD5`, click on it to encript (take note of the `user_email` since we will be using that to gain access)
[Development Location Example](/Images/varChar.png)

8. Go back to `WPEngine` and click on `WP Admin`
[Development Location Example](/Images/myphp:wpAdminLocation.png)

## WP Admin

1. Input the email from `user_email` and the password you created
[Development Location Example](/Images/adminEmail.png)

2. Once inside on the left there will be a panel, go down until you reach `users`
[Development Location Example](/Images/dashboardUsers.png)

3. Click on `Add New User` and input the information it asks for and give yourself the role of `Administrator`
[Development Location Example](/Images/addUsers.png)

4. Once this is completed log out and you can log back in by using your own email/username and password you created