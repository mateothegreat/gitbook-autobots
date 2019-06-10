# Creating your own Module

## tsconfig.json

We need to tell the typescript command `tsc` how to compile our project. Create the following file in your project root and name it `tsconfig.json`:

```typescript
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
        "emitDecoratorMetadata": true,
        "declaration": true
    },
    "include": [
        "src/**/*"
    ]
}
```

