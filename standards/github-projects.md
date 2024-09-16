# Creating New GitHub Repositories

This documentaion will detail basic procedure and best practices for creating repositories on Digital Nest's GitHub organization.

## Initial Creation

1. Ensure you are on the [BizzNEST organization page](https://github.com/BizzNEST)

2. In the **Repositories** section, click **New**

3. You should now be on a *'Create a new repository'* page with various fields. Below will detail procedure for each section:

    > ### Repository Template
    >
    > 1. Select the **BizzNEST/.github** template
    > 2. Leave *'Include all branches'* unselected
    >
    > ### Owner/Repository Name
    >
    > 1. The owner should be **BizzNEST**
    > 2. Your repository name should reflect the topic and scope of the product (examples below).
    >    - a custom map component for Tesla -> tesla-map
    >    - documentation for an internal bizzNest database -> bizzNest-internal-database
    >    - the backend api for a web app -> cool-app-api
    >
    > *Repository names usually follow a lowercase format(hyphens allowed) and must be unique
    >
    > #### Description
    >
    > 1. Define the scope of the repository (Ex. if it's for a project or documenation, etc.)
    >
    > ### Access
    >
    > 1. The default access is **Private** and should be selected on repo creation.

## Setting up the development environment

1. Under the **Code** tab, click **Code** and copy either the **HTTPS** or **SSH** (if you have an SSH key) git URL

2. Open your code editor (The next steps will be detailed for Visual Studio Code, but will apply for other editors)

3. Open a new terminal with ``Ctrl + Shift + ` ``.

4. Navigate to the folder where you want the repo

5. Execute these steps/commands:

    > 1. Clone the repo:
    > ```sh
    > git clone https://github.com/your-username/your-repo.git
    > ```
    > (paste the git URL from [1])
    >
    > 2. Install dependencies:
    > ```sh
    > npm i
    > ```
    >
    > 3. Create a .env file in `root` to store any secret variables (API keys, config keys, etc.)
    >
    > 4. Run the development server:
    > ```sh
    > npm start
    > ```

### Essential extensions for VS Code:

- Prettier (by [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)) -> code formatting
- Live Server (by [Ritwick Dey](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)) -> website preview

#### Quality of Life (QOL)

- Bongo Cat (by [pixl garden](https://marketplace.visualstudio.com/items?itemName=pixl-garden.BongoCat)) -> cuz we like some fun around here :)


## Important Best Practices

- **NEVER** push `.env` or `credentials.json` files to GitHub

- Run `npm i` each time you pull from origin (this ensures that you are developing with the correct dependencies)

- Always keep repo visibility **Private**