# TypeSpec

## [Installation](https://typespec.io/docs)

```
npm install -g @typespec/compiler
```

## JSON SCHEMA

### tsp init

```sh
bash-5.2$ tsp init
TypeSpec compiler v0.54.0

✔ Please select a template › Empty project      min compiler ver: 0.54.0
Create an empty project.
✔ Project name … jsonschema

TypeSpec init completed. You can run `tsp install` now to install dependencies.
Project created successfully.
```

### main.tsp

```sh
bash-5.2$ cat > main.tsp 
import "@typespec/json-schema";

using TypeSpec.JsonSchema;

@jsonSchema
namespace Schemas;

model Person {
  name: string;
  address: Address;
  @uniqueItems nickNames?: string[];
  cars?: Car[];
}

model Address {
  street: string;
  city: string;
  country: string;
}

model Car {
  kind: "ev" | "ice";
  brand: string;
  @minValue(1900) year: int32;
}
Ctrl+D
```

### tsp install

```sh
bash-5.2$ tsp install
TypeSpec compiler v0.54.0


added 74 packages, and audited 75 packages in 1s

12 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```

### tsp compile

```sh
bash-5.2$ tsp compile . --emit=@typespec/json-schema
TypeSpec compiler v0.54.0

Diagnostics were reported during compilation:

/Volumes/japi/typespec/jsonschema/main.tsp:1:1 - error import-not-found: Couldn't resolve import "@typespec/json-schema"
> 1 | import "@typespec/json-schema";
    | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
error import-not-found: Couldn't resolve import "@typespec/json-schema"
/Volumes/japi/typespec/jsonschema/main.tsp:3:16 - error invalid-ref: Namespace TypeSpec doesn't have member JsonSchema
> 3 | using TypeSpec.JsonSchema;
    |                ^^^^^^^^^^
/Volumes/japi/typespec/jsonschema/main.tsp:5:2 - error unknown-identifier: Unknown identifier jsonSchema
> 5 | @jsonSchema
    |  ^^^^^^^^^^
/Volumes/japi/typespec/jsonschema/main.tsp:5:1 - error unknown-decorator: Unknown decorator
> 5 | @jsonSchema
    | ^^^^^^^^^^^
/Volumes/japi/typespec/jsonschema/main.tsp:11:4 - error unknown-identifier: Unknown identifier uniqueItems
> 11 |   @uniqueItems nickNames?: string[];
     |    ^^^^^^^^^^^
/Volumes/japi/typespec/jsonschema/main.tsp:11:3 - error unknown-decorator: Unknown decorator
> 11 |   @uniqueItems nickNames?: string[];
     |   ^^^^^^^^^^^^

Found 7 errors.

No emitter was configured, no output was generated. Use `--emit <emitterName>` to pick emitter or specify it in the TypeSpec config.
(failed reverse-i-search)`npm install ': /Users/japi/.^Cm/_npx/79e0e2c6955b7129/node_modules/.bin/weft wallet ls --walletpath
 ./_cfg/_wallets/
```

### npm install

```sh
bash-5.2$ npm install --save @typespec/json-schema

added 1 package, and audited 76 packages in 2s

12 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```

### tsp compile

```sh
bash-5.2$ tsp compile . --emit=@typespec/json-schema
TypeSpec compiler v0.54.0

Compilation completed successfully.

bash-5.2$ find tsp-output -ls
2627898        0 drwxr-xr-x    3 japi             staff                  96 31 mar 23:54 tsp-output
2627899        0 drwxr-xr-x    3 japi             staff                  96 31 mar 23:54 tsp-output/@typespec
2627900        0 drwxr-xr-x    5 japi             staff                 160 31 mar 23:54 tsp-output/@typespec/json-schema
2627903        8 -rw-r--r--    1 japi             staff                 323 31 mar 23:54 tsp-output/@typespec/json-schema/Car.yaml
2627901        8 -rw-r--r--    1 japi             staff                 323 31 mar 23:54 tsp-output/@typespec/json-schema/Person.yaml
2627902        8 -rw-r--r--    1 japi             staff                 219 31 mar 23:54 tsp-output/@typespec/json-schema/Address.yaml
```

### Person.yaml

```yaml
bash-5.2$ cat tsp-output/\@typespec/json-schema/Person.yaml 
$schema: https://json-schema.org/draft/2020-12/schema
$id: Person.yaml
type: object
properties:
  name:
    type: string
  address:
    $ref: Address.yaml
  nickNames:
    type: array
    items:
      type: string
    uniqueItems: true
  cars:
    type: array
    items:
      $ref: Car.yaml
required:
  - name
  - address
```

### Address.yaml

```yaml
bash-5.2$ cat tsp-output/\@typespec/json-schema/Address.yaml 
$schema: https://json-schema.org/draft/2020-12/schema
$id: Address.yaml
type: object
properties:
  street:
    type: string
  city:
    type: string
  country:
    type: string
required:
  - street
  - city
  - country
```

```yaml
bash-5.2$ cat tsp-output/\@typespec/json-schema/Car.yaml 
$schema: https://json-schema.org/draft/2020-12/schema
$id: Car.yaml
type: object
properties:
  kind:
    anyOf:
      - type: string
        const: ev
      - type: string
        const: ice
  brand:
    type: string
  year:
    type: integer
    minimum: 1900
    maximum: 2147483647
required:
  - kind
  - brand
  - year
```

