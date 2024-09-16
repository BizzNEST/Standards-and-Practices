# Gaining Access To Site

- Allow users to gain access to the site's dashboard by themselves


## WPEngine Screen

1. Once you log into WPEngine make sure you are in the correct location where you will be working in: `Development` `Staging` or `Production`
<img width="649" alt="stagingLocations" src="https://github.com/user-attachments/assets/4760935d-808f-4c1f-9146-f63ff7f0745a">

2. After the correct location has been clicked you will want to click on `phpMyAdmin`
<img width="498" alt="myphp:wpAdminLocation" src="https://github.com/user-attachments/assets/856ec209-8c99-4551-9706-48c88a01de4b">

3. On left side there should be an image of a database that starts with -> `wp_name-of-site`(ex:wp_digitalnest)
<img width="236" alt="databaseLocation" src="https://github.com/user-attachments/assets/52c170d8-7b00-4fdc-b6a3-dde7392b0752">

4. Click on the `+` to expand and scroll down to `wp_users` and click on it
<img width="209" alt="wp_userLocation" src="https://github.com/user-attachments/assets/dab7c343-dca0-4830-b6bf-c0aec0deedcd">

5. The user we want to mess with will be at the very top of the database, click on `Edit`
<img width="1438" alt="phpMainAdmin" src="https://github.com/user-attachments/assets/1f195493-8608-464c-b24c-6200854400dc">

6. Once inside we will need to look for `user_pass`, this has a series of random ints and chars. You will create a password you will remember and input it in here.
<img width="621" alt="phpUserPass" src="https://github.com/user-attachments/assets/5ad693c7-09cf-4e03-b57c-b6d211c288ab">

7. Click  on `varchar(255)` to expand and look for `MD5`, click on it to encript (take note of the `user_email` since we will be using that to gain access)
<img width="635" alt="varChar" src="https://github.com/user-attachments/assets/548a8d04-a37a-427a-b338-9afdba97bc34">

8. Go back to `WPEngine` and click on `WP Admin`
<img width="498" alt="myphp:wpAdminLocation" src="https://github.com/user-attachments/assets/7c83c777-3909-485c-b3f7-6d0743f957f1">

## WP Admin

1. Input the email from `user_email` and the password you created
<img width="297" alt="adminEmail" src="https://github.com/user-attachments/assets/a437b1c5-3a80-46e2-a398-51eb7011afad">

2. Once inside on the left there will be a panel, go down until you reach `users`
<img width="309" alt="dashboardUsers" src="https://github.com/user-attachments/assets/33100005-c432-4335-b530-b71227094810">

3. Click on `Add New User` and input the information it asks for and give yourself the role of `Administrator`
<img width="396" alt="addUsers" src="https://github.com/user-attachments/assets/72383884-ec1d-436f-a3aa-817bd7d9dcab">

4. Once this is completed log out and you can log back in by using your own email/username and password you created
   <img width="609" alt="wpLogIn" src="https://github.com/user-attachments/assets/ff547a43-d003-4449-a3a0-bf85c43c4484">
