# 01-npm-link

This is an example of how copy-pasting code into a repo would work. Consider this scenario: a package `dependency` we would like `dependent` to depend on exists at `~/dependency`. We use `npm link` or `npm install file:` to install `dependency`.

```
~
├── dependency
│   ├── index.js
│   ├── package-lock.json
│   └── package.json
└── dependent
    ├── index.js
    ├── package-lock.json
    └── package.json
```

```sh
$ cd ~/dependent
$ npm install --save file:../dependency
```

Once the link is made, `~/dependency` will by symlinked as `~/dependent/node_modules/dependency`, so `dependent` will always have access to the currently checked out code inside `~/dependency`. The maintainers of dependents on `dependency` will need to check out the correct code whenever working on that dependent &mdash; this is likely to be a maintenance nightmare.
