# Typescript

Always prefer than Javascript

Pros:

- Strictly typed lang. Helps us reduce bugs and magic of our code.
- Evolves much faster than Javascript

Cons:

- Typescript transpile to Javascript, thus all underground is still old ugly javascript.
- Not all external libraries are written in Typescript or have d.ts, thus making us fit Typescript to some javascript APIs

## Best Practices

### General BP

- Use Typescript imports, not require(), unless has not other option.
- Folders of Typescript files will be consider as a module. ReExport only 'external' api for each module.
- Use native EcmaScript functions instead of 'lodash' or other Third-part libraries
- Use moment.js instead of EcmaScript Date type - All over the code.
- Use Async-Await operators and not .then.catch.finally functions when working with Promise
- Try your best sticking to Typescript. For example, don't use 'function' which is of JavaScript, but allowed in a .ts file.
- Const > let > var = Never use it.

### Strict configuration

Set Typescript to be strict as possible. Otherwise, you just doesn't use it's full potential.

- strict: true
- noImplicitReturns: true
- noUnusedLocals: true
- strictNullChecks: true
- noImplicitThis: true
- noImplicitAny: true
- alwaysStrict: true

### Eslint

Tslint linter is dead, long live eslint linter with Typescript rules.

parser: '@typescript-eslint/parser', // Specifies the ESLint parser
extends: [
'plugin:@typescript-eslint/recommended', // Uses the recommended rules from the @typescript-eslint/eslint-plugin
],
