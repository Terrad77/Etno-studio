# Vanilla App Template

This project was created using Vite. To learn more and configure additional features,
[refer to the documentation](https://vitejs.dev/).

## Creating a Repository from the Template

Use this GoIT organization repository as a template to create your own project repository.
Click the `«Use this template»` button and select `«Create a new repository»`, as shown in the image.

![Creating repo from a template step 1](./assets/template-step-1.png)

On the next step, a new repository creation page will open. Fill in the repository name,
make sure the repository is set to public, then click `«Create repository from template»`.

![Creating repo from a template step 2](./assets/template-step-2.png)

Once the repository has been created, navigate to the repository settings under
`Settings` > `Actions` > `General`, as shown in the image.

![Settings GitHub Actions permissions step 1](./assets/gh-actions-perm-1.png)

Scroll to the bottom of the page. In the `«Workflow permissions»` section, select
`«Read and write permissions»` and check the checkbox. This is required to automate
the project deployment process.

![Settings GitHub Actions permissions step 2](./assets/gh-actions-perm-2.png)

You now have a personal project repository with the file and folder structure from
the template repository. Treat it like any other personal repository — clone it to
your machine, write code, make commits, and push them to GitHub.

## Getting Started

1. Make sure you have the LTS version of Node.js installed on your machine.
   [Download and install](https://nodejs.org/en/) it if necessary.
2. Install the project's base dependencies by running `npm install` in the terminal.
3. Start the development server by running `npm run dev` in the terminal.
4. Open your browser and navigate to
   [http://localhost:5173](http://localhost:5173). The page will automatically
   reload whenever you save changes to project files.

## Files and Folders

- Page component markup files should be placed in the `src/partials` folder and
  imported into `index.html`. For example, the header markup file `header.html`
  is created in the `partials` folder and imported into `index.html`.
- Style files should be placed in the `src/css` folder and imported into the
  corresponding HTML page files. For example, the stylesheet for `index.html`
  is named `index.css`.
- Add images to the `src/img` folder. The bundler will optimize them, but only
  during a production build. This process runs in the cloud to avoid loading
  your local machine, as it can take a significant amount of time on slower computers.

## Deployment

The production build of the project is automatically compiled and deployed to GitHub
Pages in the `gh-pages` branch every time the `main` branch is updated — for example,
after a direct push or a merged pull request. To enable this, update the `--base=/<REPO>/`
flag value for the `build` command in `package.json`, replacing `<REPO>` with your
repository name, then push the changes to GitHub.

```json
"build": "vite build --base=/<REPO>/",
```

Next, go to your GitHub repository settings (`Settings` > `Pages`) and configure
the production files to be served from the `/root` folder of the `gh-pages` branch,
if this was not done automatically.

![GitHub Pages settings](./assets/repo-settings.png)

### Deployment Status

The deployment status of the latest commit is indicated by an icon next to its identifier.

- **Yellow** — the project is being built and deployed.
- **Green** — deployment completed successfully.
- **Red** — an error occurred during linting, building, or deployment.

For more detailed status information, click the icon and follow the `Details` link
in the dropdown window.

![Deployment status](./assets/deploy-status.png)

### Live Page

After a few minutes, the live version of the page will be available at the URL
shown under `Settings` > `Pages` in your repository settings. For example, here
is the link to the live version of this repository:

[https://goitacademy.github.io/vanilla-app-template/](https://goitacademy.github.io/vanilla-app-template/).

If the page opens blank, check the `Console` tab in your browser's developer tools
for any errors related to incorrect paths to CSS or JS files (**404**). Most likely,
the `--base` flag value for the `build` command in `package.json` is incorrect.

## How It Works

![How it works](./assets/how-it-works.png)

1. After every push to the `main` branch of the GitHub repository, a dedicated script
   (GitHub Action) defined in `.github/workflows/deploy.yml` is triggered.
2. All repository files are copied to the server, where the project is initialized,
   linted, and built before deployment.
3. If all steps complete successfully, the compiled production files are pushed to the
   `gh-pages` branch. Otherwise, the script execution log will indicate what went wrong.
