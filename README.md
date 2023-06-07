# package.json Notes

## GUI Deploy Link:

lab-16-server-d53-dev.us-east-2.elasticbeanstalk.com

## CLI Deploy Link:

I am so confused with what exactly this is looking for, wasted an hour trying to find what it is or means, but at this point I'm assuming there's something I've done wrong or am not understanding. 

## UML 

Just to be clear, this came from: 
> https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts-webserver.html

[UML for Lab 16](/lab-16-uml.png)




## For React Applications

To deploy your application at GitHub pages, you'll need to add a home page property to your package.json which points to the deployed base URL of your GitHub Pages site.

*NOTE: This will break deployments to other hosting services such as Netlify, Vercel, or AWS Amplify, so if you later wish to deploy there, remove this property completely.*

```json
{
  "homepage": "https://yourname.github.io/repository-name"
}
```

## Node / Express Applications

### For Tests

Your scripts section should have the following, so that you can easily run tests locally and in your CI.

```json
  "scripts": {
    "start": "node index.js",
    "test": "jest --verbose --coverage",
    "test-watch": "jest --watchAll --verbose --coverage",
    "init:config": "sequelize init:config",
    "db:create": "sequelize db:create"
},
```

### For NPM Modules

If you are creating a module to deploy at NPM, you'll want a "bin" section that identifies the name of the global command to run and your .js file that runs when called.

```json
"bin": {
    "fetch": "index.js"
}
```

Additionally, that file should have as it's first line, so that it'll run without having to type "node filename.js" every time

`#!/usr/bin/env node`
