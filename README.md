# The Complete Strapi Course

Practice about development Strapi 4 and plugins

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

## Admin panel

### Super Admin (app designer)
- Defines data models on `Content-Type Builder`
- Configure app settings on `Settings`

### Editor
- Creates/edits content on `Content Manager`
- Supervises all authors on `Content Manager`

### Author
- Creates/edits content on `Content Manager`
- No access to others' content on `Content Manager`

### App User
- Signs up/in to your app on `Frontend app`

## How to upgrade
1. Use the latest version(the one Strapi CLI installed by default)(v.4.5.0)
2. Use the version same the course (v4.3.9)