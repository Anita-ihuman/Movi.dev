## Set up Your Next Js App with Typescript, Eslint and Prettier

When creating a new project, automating lint tools can help developers save a lot of time and effort of having to manually formatting codes.
In order to have set up your project, I have put together details steps on how to install all the needed dependencies without reading through tons of documentation before setting up. 

 In this article, I will be sharing with you the steps on how to set up a Next, js project that uses Typescript, ESLint and Prettier. Having Eslint with Prettier as automated syntax scans on your code and reformatting. This will ensure that consistent rules are being followed for indentation, spacing, semicolons, etc and delivers clean code. 


## NEXT
[Next.js](https://nextjs.org/) is a React framework for developing single-page Javascript applications. It lets you build server-side rendering and static web applications using React. It has great features and benefits making it very convenient in building websites.


## Set-Up 
Next.js is like every other node.js application so, to build a project with Next.js you need to have [node.js](https://nodejs.org/) installed in your system. This is because you will be needing *npm* or *Yarn *to install dependencies for the project.

### 1.Initiate the project by running this command in your terminal.

```
// for yarn 
yarn create next-app
``` 
```
// for Npm 
Npm create next-app
``` 


### 2.Git and gitignore.
Now that we have created a project, we have to make sure we initiate git and add a .gitignore file created. *cd *into the directory, run these commands in the terminal.

```
git init
``` 

```
touch .gitignore
``` 

## 3. Install the necessary dependencies


- ### Typescript:
[TypeScript](https://www.typescriptlang.org/) is an object-oriented programming language that simplifies JavaScript code, making it easier to read and debug. With the help of TSC (TypeScript Compiler), your Typescript code (.ts file)  is converted to JavaScript (.js file).

To install typescript run this command in the terminal

```
yarn add --dev typescript @types/react @types/node
``` 

```
npm install -D typescript @types/react @types/node
``` 
Once you have run the command create a file named * tsconfig.json* in the root directory and paste the configuration below in the file.

```{
  "compilerOptions": {
    "target": "es5",
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": true,
    "skipLibCheck": true,
    "strict": false,
    "forceConsistentCasingInFileNames": true,
    "noEmit": true,
    "esModuleInterop": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve",
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"]
    }
  },
  "exclude": ["node_modules", ".next", "out"],
  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx", "**/*.js"]
}
``` 
You can now change your files from javascript to typescript.

```
./pages/index.js # a ./pages/index.tsx
./pages/api/hello.js # a ./pages/api/hello.ts
``` 

- ### Eslint:
[Eslint](https://eslint.org/) is a popular javascript linter. This tool reads your source code and finds errors before running your code saving you time and To install Eslint run this command in the terminal.

```
yarn add -D eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint-plugin-react
``` 
Then create a file in the root directory using this command. 

```
touch .eslintrc.json
``` 
Paste the details below in the config file. 

```
{
  "env": {
    "browser": true,
    "es6": true,
    "jest": true
  },
  "rules": {
    "no-console": "error",
    "import/first": "error",
    "react/prop-types": "off"
  },
  "extends": [
    "react-app",
    "react-app/jest",
    "eslint:recommended",
    "plugin:react/recommended",
    "plugin:@typescript-eslint/recommended",
    "plugin:react-hooks/recommended",
    "prettier"
  ],
  "parser": "@typescript-eslint/parser",
  "root": true,
  "plugins": ["react", "@typescript-eslint"],
  "parserOptions": {
    "ecmaVersion": 11,
    "ecmaFeatures": {
      "jsx": true
    },
    "project": "./tsconfig.json"
  },
  "settings": {
    "react": {
      "pragma": "React",
      "version": "detect"
    }
  }
}
``` 

- ### Prettier: 
[Prettier](https://movi.hashnode.dev/how-to-write-100x-cleaner-code-for-experienced-and-newbies-cked6cvho00yhtds1017s58qj) is a popular javascript formatter that makes sure that developer on a team has the same code formatters regardless of their editors.
To install Prettier, run this command in the terminal.

```
yarn add -D prettier eslint-config-prettier eslint-plugin-prettier
``` 
Then create another file that will be used to write our configuration by using this command. 

```
touch .prettierrc
``` 
Update the config file with the code below.

```
  module.exports ={
   // Change your rules accordingly to your coding style preferences.
  // https://prettier.io/docs/en/options.html
  semi: false,
  trailingComma: 'es5',
  singleQuote: true,
  printWidth: 100,
  tabWidth: 2,
  useTabs: false,
}
``` 
That is just it, your project is ready for you to start working on. You can install every other dependency subsequently into the project.



## Conclusion 
I am currently still learning how to use Next js and Typescript in a project. I can say that taking out time to set up a project and install all the dependencies needed for the project, goes a long way to deliver an improved development process.
