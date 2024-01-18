# React + TypeScript + Vite + Dockers

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type aware lint rules:

- Configure the top-level `parserOptions` property like this:

```js
export default {
  // other rules...
  parserOptions: {
    ecmaVersion: 'latest',
    sourceType: 'module',
    project: ['./tsconfig.json', './tsconfig.node.json'],
    tsconfigRootDir: __dirname,
  },
}
```

- Replace `plugin:@typescript-eslint/recommended` to `plugin:@typescript-eslint/recommended-type-checked` or `plugin:@typescript-eslint/strict-type-checked`
- Optionally add `plugin:@typescript-eslint/stylistic-type-checked`
- Install [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react) and add `plugin:react/recommended` & `plugin:react/jsx-runtime` to the `extends` list


## Docker command to run containers with updated files:

I have used dockers to deploy my website.

`DockerFile` is a file that contains Docker Config for my docker image.
`.dockerfile` is a file for Dockers that works the same way `.gitignore` works for GitHub
To run this application in docker env run following commands,

- [docker build -t {ProjectName} .]

`{ProjectName}` is name of folder or repo your code is in, and "." denotes current directory. This command will make an image for your codebase. Now you need to create containers for this image in order to run it, you need to run the code given below.

- [docker run -p {Port}:{Port} -v "$(pwd):/app" -v /app/node_modules {Folder or dir name}]

`-p {Port}:{Port}` is used to map ports for host side {make sure no other container is running on same port}

`-v "$(pwd):/app" -v /app/node_modules` is used to assign volume

# How to publish docker-container?

Step 1 - Authenticate -> docker login

Step 2 - [docker tag {Project-Name} {User-Name}/{Name-of-Image}]