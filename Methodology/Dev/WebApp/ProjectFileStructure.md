# Project File Structure

## General Structure

Use default's React/Angular initializers structure

- package.json, package-lock.json, tsconfig, gitignore
- README
- src directory
  - app
  - assets
  - public
  - LazyParty
    - Put here all the components/services/libraries that you wrote by yourself but are absolutely generic and can be use in all other projects. In this case, the best choice is to put it in an organized repo(NPM,bower..), but if you are too LAZY, at least isolate it from all other app code so you will treat it as an external library.
- dist directory
  - will be used for compiled bundled files.
- GUI tests / e2e
- Server
  - the server files hosting the client's site.
  - Server should as thin as possible. Only need to server the App bundle
  - In cases needed, add Authentication/Authorization solution so server as well.
- ThirdParty
  - Used for external libraries and packages. Try to avoid use other libraries which are not taken from an organized repo, but in case you must do, put it there, so everyone will know to treat it as an external library.

## App Code

- Organize your code by logical modules and not by types of files. (?? Say more about it)
- Test files will be located next to the tested code.

### File postfix

- .component.controller
- .component.controller.test
- .component.module
- .service / .provider
- .route
- .configuration

(?? research more)
(?? Consider splitting it to file structure per framework (Angular/React/Vue))
