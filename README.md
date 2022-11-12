# The Complete Strapi Course

Practice about development Strapi 4 and plugins

## Required

### MacOS M1
```bash
Ventura 13.0.1
```
### NodeJS
```bash
# support version 14 and 16
node -v
# v16.18.1
```

## How to create project

```bash
yarn create strapi-app app --quickstart
# npx create-strapi-app@latest app --quickstart
cd app
yarn develop
```

then go to `http://localhost:1337/admin` and create original credential data

## Flow script create

```bash
1. Bootstraps a new Strapi project
2. Installs all dependencies
3. Builds the admin UI
4. Starts a dev server at localhost:1337
    4.1 /admin      Admin panel
    4.2 /api        Rest API    # must be install plugin
    4.3 /graphql    GraphQL API # must be install plugin
```

## Using with TS

### Bootstrap a Strapi project with TS
```bash
yarn create strapi-app app --quickstart --typescript
# npx create-strapi-app@latest app --quickstart --typescript
```
*** `--typescript or --ts`

### Convert an existing project to TS
```bash
# 1.add `tsconfig.json` to root directory
{
    "extends": "@strapi/typescript-utils/tsconfigs/server",
    "compilerOptions": {
      "outDir": "dist",
      "rootDir": ".",
      "allowJs": true //enables the build without .ts files
    },
    "include": [
      "./",
      "src/**/*.json"
    ],
    "exclude": [
      "node_modules/",
      "build/",
      "dist/",
      ".cache/",
      ".tmp/",
      "src/admin/",
      "**/*.test.ts",
      "src/plugins/**"
    ]
}
```

```bash
# 2.add `tsconfig.json` to ./src/admin/tsconfig.json
{
    "extends": "@strapi/typescript-utils/tsconfigs/admin",
    "include": [
        "../plugins/**/admin/src/**/*",
        "./"
    ],
    "exclude": [
        "node_modules/",
        "build/",
        "dist/",
        "**/*.test.ts"
    ]
}
```

```bash
# 3.remove .eslintignore and .eslintrc on root project
rm -rf .eslintignore .eslintrc
```

```bash
# 4. add an additional '..' to the `filename` in the `database.ts` configuration file `./config/database.ts`
```

```bash
# 5. rebuild
yarn develop
```