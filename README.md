# fish

This is a project to put my skills to the test.

## Create a vue project

```sh
docker run --rm -it -v $(pwd):/app -w /app node sh
```

Inside the container

```sh
npm init vue@latest
```

Maybe you need to change the folder owner.

## Running project

```sh
docker run --rm -it -v $(pwd):/app -w /app node npm i

docker run --rm -v $(pwd):/app -w /app -dp 3000:3000 node yarn dev
```

The project can be run using npm but I have a [bug](https://github.com/vitejs/vite/issues/6767) with it.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```
