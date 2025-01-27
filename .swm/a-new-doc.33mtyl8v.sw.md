---
id: 33mtyl8v
title: A new doc
file_version: 1.1.2
app_version: 1.10.3
---

This code iterates over the dependencies listed in `packageData` and checks if `d3` exports all the properties from each module. It uses `import` to dynamically load each module and `assert` to check if each property is exported by `d3`.
<!-- NOTE-swimm-snippet: the lines below link your snippet to Swimm -->
### 📄 test/d3-test.js
```javascript
10     for (const moduleName in packageData.dependencies) {
11       it(`d3 exports everything from ${moduleName}`, async () => {
12         const module = await import(moduleName);
13         for (const propertyName in module) {
14           if (propertyName !== "version") {
15             assert(propertyName in d3, `${moduleName} exports ${propertyName}`);
16           }
17         }
18       });
19     }
```

<br/>

This code defines a `config` object that specifies the input and output files for a JavaScript bundle, along with other settings such as format and plugins. The output file name includes the value of `meta.name`, and a banner is added to the top of the output file that includes information about the package version and copyright.
<!-- NOTE-swimm-snippet: the lines below link your snippet to Swimm -->
### 📄 rollup.config.js
```javascript
14     const config = {
15       input: "bundle.js",
16       output: {
17         file: `dist/${meta.name}.js`,
18         name: "d3",
19         format: "umd",
20         indent: false,
21         extend: true,
22         banner: `// ${meta.homepage} v${meta.version} Copyright ${copyright}`
23       },
24       plugins: [
25         nodeResolve(),
26         json()
27       ],
```

<br/>

This file was generated by Swimm. [Click here to view it in the app](https://swimm-web-app.web.app/repos/Z2l0aHViJTNBJTNBZDMlM0ElM0FJZGl0WWVnZXJTd2ltbQ==/docs/33mtyl8v).
