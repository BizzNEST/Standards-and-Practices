# Gaining Access To Site

- Allow users to gain access to the site's dashboard by themselves


## WPEngine Screen

1. Once you log into WPEngine make sure you are in the correct location where you will be working in: `Development` `Staging` or `Production`

2. After the correct location has been clicked you will want to click on `phpMyAdmin`

3. On left side there should be an image of a database that starts with -> `wp_name-of-site`(ex:wp_digitalnest)

4. Click on the `+` to expand and scroll down to `wp_users` and click on it

5. The user we want to mess with will be at the very top of the database, click on `edit`

6. Once inside we will need to look for `User_pass`, this has a series of random ints and chars

7. Find `MD5` and click on it to encript it (take note of the `user_email` since we will be using that to gain access)

8. Go back to `WPEngine` and click on `WP Admin`

## WP Admin

1. Input the email from `user_email` and the password you created

2. Once inside on the left there will be a panel, go down until you reach `users`

3. Click on `Add New User` and input the information it asks for and give yourself the role of `Administrator`

4. Once this is completed log out and you can log back in by using your own email/username and password you created