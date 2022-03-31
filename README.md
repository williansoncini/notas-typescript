Belezera, aqui vou colocar algumas notas de typescript que estou aprendendo :3

- [Instalação](#instalação)
- [Tipos de arquivos](#tipos-de-arquivos)
- [Compilando arquivos](#compilando-arquivos)
- [Script e module mode](#script-e-module-mode)
- [Executando os arquivos .ts de maneira mais rápida](#executando-os-arquivos-ts-de-maneira-mais-rápida)
  - [instalação ts-node](#instalação-ts-node)
- [Configuração code runner](#configuração-code-runner)
- [Configurando o Eslint](#configurando-o-eslint)
  - [instalação](#instalação-1)
  - [Arquivo de configuração](#arquivo-de-configuração)
  - [Exemplo de `.eslintrc.js`](#exemplo-de-eslintrcjs)
  - [Instanado o Prettier](#instanado-o-prettier)
  - [Arquivo de configuração](#arquivo-de-configuração-1)
  - [Configurando o Prettier](#configurando-o-prettier)
- [Arquivo de configuração do TypeScript](#arquivo-de-configuração-do-typescript)
  - [Conteudo do arquivo](#conteudo-do-arquivo)
- [Buildando](#buildando)

# Instalação
```js
npm i typescript -D
```

# Tipos de arquivos
As extensões dos arquivos de typescript são definidos como `*.ts`

# Compilando arquivos
Para compilar os arquivos typescript para javascript

```js
npx tsc index.ts
```

# Script e module mode
O typescript trabalha com esses modos. O script mode será implementado por padrão no seu script. Ao utilizar `export` ele irá assumir que você está no modo de modulos.

No modo script ele assume boa parte do seu código como apenas um unico script, então você pode receber erros de declarações duplicadas por exemplo.

Já no modo módulo ele assume que seu script está separados por módulos, então com isso você não recebera erros de declarações repetidas por conta de outros arquivos por exemplo.

**Mas 99% você ira trabalhar com o module mode :3**

# Executando os arquivos .ts de maneira mais rápida
## instalação ts-node
```js
npm i ts-node -D
```
# Configuração code runner
Dentro do vscode, com a extensão de code-runner instalada, faça as seguintes personalizanações:
```json
{
	"code-runner.executorMap": {
		"typescript": "npx ts-node --files"
	}
}
```

# Configurando o Eslint
## instalação
```js
npm i eslint -D
npm i @typescript-eslint-plugin @typescript-eslint/parser -D
```

Se não tiver ainda, você precisa da extenção do es lint no vs code :3

## Arquivo de configuração
O Eslint precisa do arquivo `eslintrx.js` na raiz do seu projeto, para conseguir fazer as correções :3

## Exemplo de `.eslintrc.js`
Sem regras :3

```js
module.exports = {
  env: {
    browser: true,
    es6: true,
    node: true,
  },
  extends: [
    'eslint:recommended',
    'plugin:@typescript-eslint/eslint-recommended',
    'plugin:@typescript-eslint/recommended',
  ],
  globals: {
    Atomics: 'readonly',
    SharedArrayBuffer: 'readonly',
  },
  parser: '@typescript-eslint/parser',
  parserOptions: {
    ecmaVersion: 11,
    sourceType: 'module',
  },
  plugins: ['@typescript-eslint'],
  rules: {},
};
```

## Instanado o Prettier
```js
npm i prettier eslint-config-prettier eslint-plugin-prettier -D
```
## Arquivo de configuração 
Crie um arquivo chamado  `prettierrc.js` :3
Exemplo do conteudo desse arquivo: 
```js
module.exports = {
	semi: true,
	trailingComma: 'all',
	singleQuote: true,
	printWidth: 80,
	tabWidth: 2,
}
```
## Configurando o Prettier
Adicione a linha abaixo na chave `extends` do arquivlo `.eslintrc.js`
```js
'plugin:prettier/recommended',
```

# Arquivo de configuração do TypeScript
Existe um arquivo chamado `tsconfig.js` que aceita váaaaaaaarias configurações do typescript, você pode iniciar esse arquivo com o seguinte comando:

```js
npx tsc --init
```

## Conteudo do arquivo
Por padrão ele vem com muiiiiitas coisas comentadas, e somente algumas habilitadas

Um exemplo de arquivo já configurado é esse:

> Esse arquivo foi pego de um curso de 2019, então pode estar desatualizado ok 👍🏻

`tsconfig.json`
```json
{
  "compilerOptions": {
    /* Visit https://aka.ms/tsconfig.json to read more about this file */

    /* Basic Options */
    // "incremental": true,                   /* Enable incremental compilation */
    "target": "ES2019",                       /* Specify ECMAScript target version: 'ES3' (default), 'ES5', 'ES2015', 'ES2016', 'ES2017', 'ES2018', 'ES2019', 'ES2020', or 'ESNEXT'. */
    "module": "CommonJS",                     /* Specify module code generation: 'none', 'commonjs', 'amd', 'system', 'umd', 'es2015', 'es2020', or 'ESNext'. */
    "lib": ["ESNext", "DOM"],                 /* Specify library files to be included in the compilation. */
    "allowJs": true,                       /* Allow javascript files to be compiled. */
    // "checkJs": true,                       /* Report errors in .js files. */
    // "jsx": "preserve",                     /* Specify JSX code generation: 'preserve', 'react-native', or 'react'. */
    // "declaration": true,                   /* Generates corresponding '.d.ts' file. */
    // "declarationMap": true,                /* Generates a sourcemap for each corresponding '.d.ts' file. */
    "sourceMap": true,                        /* Generates corresponding '.map' file. */
    // "outFile": "./",                       /* Concatenate and emit output to single file. */
    "outDir": "./dist",                       /* Redirect output structure to the directory. */
    "rootDir": "./src",                       /* Specify the root directory of input files. Use to control the output directory structure with --outDir. */
    // "composite": true,                     /* Enable project compilation */
    // "tsBuildInfoFile": "./",               /* Specify file to store incremental compilation information */
    "removeComments": true,                   /* Do not emit comments to output. */
    // "noEmit": true,                        /* Do not emit outputs. */
    "noEmitOnError": true,
    // "importHelpers": true,                 /* Import emit helpers from 'tslib'. */
    // "downlevelIteration": true,            /* Provide full support for iterables in 'for-of', spread, and destructuring when targeting 'ES5' or 'ES3'. */
    // "isolatedModules": true,               /* Transpile each file as a separate module (similar to 'ts.transpileModule'). */

    /* Strict Type-Checking Options */
    "strict": true,                           /* Enable all strict type-checking options. */
    // "noImplicitAny": true,                 /* Raise error on expressions and declarations with an implied 'any' type. */
    // "strictNullChecks": true,              /* Enable strict null checks. */
    // "strictFunctionTypes": true,           /* Enable strict checking of function types. */
    // "strictBindCallApply": true,           /* Enable strict 'bind', 'call', and 'apply' methods on functions. */
    // "strictPropertyInitialization": true,  /* Enable strict checking of property initialization in classes. */
    // "noImplicitThis": true,                /* Raise error on 'this' expressions with an implied 'any' type. */
    // "alwaysStrict": true,                  /* Parse in strict mode and emit "use strict" for each source file. */

    /* Additional Checks */
    // "noUnusedLocals": true,                /* Report errors on unused locals. */
    // "noUnusedParameters": true,            /* Report errors on unused parameters. */
    // "noImplicitReturns": true,             /* Report error when not all code paths in function return a value. */
    // "noFallthroughCasesInSwitch": true,    /* Report errors for fallthrough cases in switch statement. */

    /* Module Resolution Options */
    // "moduleResolution": "node",            /* Specify module resolution strategy: 'node' (Node.js) or 'classic' (TypeScript pre-1.6). */
    // "baseUrl": "./",                       /* Base directory to resolve non-absolute module names. */
    // "paths": {},                           /* A series of entries which re-map imports to lookup locations relative to the 'baseUrl'. */
    // "rootDirs": [],                        /* List of root folders whose combined content represents the structure of the project at runtime. */
    // "typeRoots": [],                       /* List of folders to include type definitions from. */
    // "types": [],                           /* Type declaration files to be included in compilation. */
    // "allowSyntheticDefaultImports": true,  /* Allow default imports from modules with no default export. This does not affect code emit, just typechecking. */
    "esModuleInterop": true,                  /* Enables emit interoperability between CommonJS and ES Modules via creation of namespace objects for all imports. Implies 'allowSyntheticDefaultImports'. */
    // "preserveSymlinks": true,              /* Do not resolve the real path of symlinks. */
    // "allowUmdGlobalAccess": true,          /* Allow accessing UMD globals from modules. */

    /* Source Map Options */
    // "sourceRoot": "",                      /* Specify the location where debugger should locate TypeScript files instead of source locations. */
    // "mapRoot": "",                         /* Specify the location where debugger should locate map files instead of generated locations. */
    // "inlineSourceMap": true,               /* Emit a single file with source maps instead of having a separate file. */
    // "inlineSources": true,                 /* Emit the source alongside the sourcemaps within a single file; requires '--inlineSourceMap' or '--sourceMap' to be set. */

    /* Experimental Options */
    "experimentalDecorators": true,           /* Enables experimental support for ES7 decorators. */
    "emitDecoratorMetadata": true,            /* Enables experimental support for emitting type metadata for decorators. */

    /* Advanced Options */
    "skipLibCheck": true,                     /* Skip type checking of declaration files. */
    "forceConsistentCasingInFileNames": true  /* Disallow inconsistently-cased references to the same file. */
  },
  "include": [
    "./src"
  ]
}
```

# Buildando
Bora buildar?

Para buildar o código é muito simples se você já tiver o `tsconfig.json` já configurado, e eu vou contar que você tenha ahusdhfua

Então basta executar o comando abaixo:
```js
npm tsc
```

Com isso ele deve criar a pasta do build com todos os arquivos dentro

# Tipos privimitos

## Tipos básicos
```typescript
let nome: string = 'texto'; // qualquer tipo de string
let idade: number = 10; // 10, 10.43, -5.55, 0xf00d, 0b1010, 0o7744
let adulto: boolean = true; // true ou false
let simbolo: symbol = Symbol('Qualquer symbol'); // symbol
let big: bigint = 10n;
```

# Arrays
`:Array<Tipo do dado>`

```typescript
let arrayNumeros: Array<number> = [1,2,3];
//let arrayNumeros: number[];
let arrayTexto: Array<string> = ['a', 'b', 'c'];
//let arrayTexto = string[];
```

# Objetos
`Chave: TipoDado`

Quando você já seta valores dentro do objeto, ele já sofre inferencia de tipos, então não é necessário setar os tipos dos valores, porem quando você não faz isso é necessário setar os tipos.

Você pode colocar o simbolo ? para indicar que um atributo não é obrigatório

```ts
// Exemplo setando os tipos dos valores
let pessoa: {nome: string, idade: number, adulto?: boolean}

// Exemplo já sofrendo inferencia
const pessoa = {
	readonly nome: 'Willian',
	idade: 999,
	adulto: true,
};
```

## Funções

```ts
// => indica o tipo do retorna da função
const soma: (x: number, y:number) => number => x + y;


// Aqui ele já sabe que o retorno será um number
function soma2(x: number, y:number){
	return x + y;
}
```


## Tipo any
Você deve setar o valor any, quando realmente quise utilizar any, mas não é incado. Porém vai saber quando serpa necessário não é mesmo? :3

```ts
function tipoAny(msg: any){
	return msg;
}
```

## Void
```ts
function printName(name: string):void {
	console.log(`You are amazing ${name}!`);
};
```

## Tuple
Array com valores fixos, mas só se você quiser :3

```ts
// Definindo um valor para cada posição do array
const dadosCliente: readonly [number, string] = [1, 'Willian'];

//Mais exemplos
const dadosClienteV2: readonly [number, ...string[]] = [1,'Willian', 'Bora', 'Estudar'];

const dadosClienteQuePodemSerMudados: [number, string] = [1, 'Willian'];
```

## Undefined
Quando não definimos se pode ou não existir o retorno. Geralmente utilizado em objetos ou arrays em campos com o simbolo de ?, declarando a não obrigatoriedade.

```ts
// Exemplo
export function createPerson(
	firstName: string,
	lastName?: string, 
) : {
	firstName: string;
	lastName?: string; // Aqui vai retornar undefined
} {
	return {
		firstName,
		lastName,
	}
}

//Ficou beeeeem verboso mas a sequenci acima significa: FUNÇÃO => TIPO DE DADOS => TIPO DE RETORNO (OBJETO) => CORPO DA FUNÇÃO

```

## null
Quando retornamos nulo em uma função, fica como responsabilidade para a próxima etapa a validar

```ts
//Exemplo de retorno number | null
const function calculaQuadrado(x: any){
	if(typeof x === 'number') return x * x;
	return null;
}
```

## Never
Quando algo nunca vai retornar nada

```ts
// Nunca vai retornar nada
export function criaErro(): never {
	thow new Error('Erro qualquer')
}
```

## enum
Utilizado para enumerar as coisas

```ts
enum Cores {
	VERMELHO,
	AZUL,
	AMARELO
};
console.log(Cores.VERMELHO) //0
//Ou

enum Cores {
	ROXO = 10,
	VERDE = 20,
	ROSA = 30
};
console.log(Cores.ROXO) //10
console.log(Cores[0]) //ROXO

// CAAAARA e ele uni as coisas viu, atualmente o Cores está assim
// Unindo os dois Cores acima
Cores {
	VERMELHO,
	AZUL,
	AMARELO,
	ROXO = 10,
	VERDE = 20,
	ROSA = 30,
}
```

### Exemplo de tipagem

```ts

```













