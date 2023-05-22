Reproduction for https://github.com/vuetifyjs/vuetify/issues/17419.

Steps followed to create this reproduction;

1. `yarn create vuetify`

- Basic w/ Typescript using pnpm

2. Update dependencies

- `"vue": "^3.3.4"`
- `"vuetify": "^3.3.0"`

3. Update `vite.config.js`

```ts
styles: { configFile: "src/styles/settings.scss" },
```

4. Create `src/styles/settings.scss`

```scss
@use "vuetify/settings" with (
  $input-font-size: 14px,
  $input-details-letter-spacing: normal
);
```

5. `pnpm dev`

Console output contains several errors complaining about VInput variables;

````
  Error: This variable was not declared with !default in the @used module.
    ╷
  2 │   $input-font-size: 14px,
    │   ^^^^^^^^^^^^^^^^^^^^^^
    ╵
    src/styles/settings.scss 2:3                                 @use
    plugin-vuetify:components/VResponsive/VResponsive.sass 1:1  root stylesheet
    ```
````
