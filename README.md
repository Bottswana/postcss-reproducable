# postcss-import Reproduction 
Repository created using the following commands:

    ng new postcss-test
    npm install @clr/ui --save
    
    ? Do you want to enforce stricter type checking and stricter bundle budgets in the workspace?
      This setting helps improve maintainability and catch bugs ahead of time.
      For more information, see https://angular.io/strict No
    ? Would you like to add Angular routing? No
    ? Which stylesheet format would you like to use? CSS

styles.css populated with:

    /* This line causes the error */
    @import "../node_modules/@clr/ui/clr-ui-dark.min.css" screen and (prefers-color-scheme: dark);
    
    /* This import succeeds without problem */
    /*@import "../node_modules/@clr/ui/clr-ui-dark.min.css";*/

## Reproduce

    npm install
    npm run ng build
    √ Browser application bundle generation complete.
    
    Error: ./src/styles.css
    Module build failed (from ./node_modules/mini-css-extract-plugin/dist/loader.js):
    ModuleBuildError: Module build failed (from ./node_modules/postcss-loader/dist/cjs.js):
    TypeError: Cannot read property '0' of undefined
        at C:\Users\James\Projects\postcss-test\node_modules\postcss-import\index.js:78:37
        at Array.forEach (<anonymous>)
        at applyMedia (C:\Users\James\Projects\postcss-test\node_modules\postcss-import\index.js:70:16)
        at C:\Users\James\Projects\postcss-test\node_modules\postcss-import\index.js:51:9
        at async LazyResult.runAsync (C:\Users\James\Projects\postcss-test\node_modules\postcss\lib\lazy-result.js:358:11)
        at async Object.loader (C:\Users\James\Projects\postcss-test\node_modules\postcss-loader\dist\index.js:95:14)
        at C:\Users\James\Projects\postcss-test\node_modules\webpack\lib\NormalModule.js:316:20
        at C:\Users\James\Projects\postcss-test\node_modules\loader-runner\lib\LoaderRunner.js:367:11
        at C:\Users\James\Projects\postcss-test\node_modules\loader-runner\lib\LoaderRunner.js:233:18
        at context.callback (C:\Users\James\Projects\postcss-test\node_modules\loader-runner\lib\LoaderRunner.js:111:13)
        at Object.loader (C:\Users\James\Projects\postcss-test\node_modules\postcss-loader\dist\index.js:104:7)
     @ multi ./src/styles.css styles[0]
    
    Error: ./src/styles.css (./node_modules/css-loader/dist/cjs.js??ref--13-1!./node_modules/postcss-loader/dist/cjs.js??ref--13-2!./src/styles.css)
    Module build failed (from ./node_modules/postcss-loader/dist/cjs.js):
    TypeError: Cannot read property '0' of undefined
        at C:\Users\James\Projects\postcss-test\node_modules\postcss-import\index.js:78:37
        at Array.forEach (<anonymous>)
        at applyMedia (C:\Users\James\Projects\postcss-test\node_modules\postcss-import\index.js:70:16)
        at C:\Users\James\Projects\postcss-test\node_modules\postcss-import\index.js:51:9
        at async LazyResult.runAsync (C:\Users\James\Projects\postcss-test\node_modules\postcss\lib\lazy-result.js:358:11)
        at async Object.loader (C:\Users\James\Projects\postcss-test\node_modules\postcss-loader\dist\index.js:95:14)
