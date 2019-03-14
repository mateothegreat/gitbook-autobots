---
description: >-
  Create a file in the projects root directory called "tsconfig.json". This will
  instruct the TypeScript Compiler on how to compile our application.
---

# tsconfig.json

{% code-tabs %}
{% code-tabs-item title="/tsconfig.json" %}
```yaml
{
    "compilerOptions": {
        "target": "es6",
        "module": "commonjs",
        "lib": [
            "es5",
            "es6"
        ],
        "sourceMap": true,
        "outDir": "dist",
        "rootDir": "src",
        "noImplicitAny": true,
        "moduleResolution": "node",
        "experimentalDecorators": true,
        "emitDecoratorMetadata": true
    },
    "include": [
        "src/**/*"
    ]
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

