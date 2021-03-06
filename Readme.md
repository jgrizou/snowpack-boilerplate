Functional Repl.it version of the SnowPack ["Getting Started" tutorial](https://www.snowpack.dev/tutorials/getting-started) as of 22/02/2021.

Deployement as github page directly via version control panel. This allow to live edit your website on repl.it and deploy it live only when you are ready via a simple commit.

Repl.it Spotlight page: https://repl.it/@jgrizou/Snowpack-Boilerplate

Github repo: https://github.com/jgrizou/snowpack-boilerplate

Github page of the build version: https://jgrizou.github.io/snowpack-boilerplate/

# How to fork and use this repl

See video: TODO

To develop:
- Clicking the Run button will run ```snowpack dev``` command and host on the repl embedded webpage as expected.

To deploy:
- in ./snowpack.config.js change the ```baseUrl: '/snowpack-boilerplate'``` to the name of your repo, this is to adapt to the baseUrl of the ghpage. This demo is hosted on a github repository called snowpack-boilerplate, hence why ```baseUrl: '/snowpack-boilerplate'```.
- go into the shell panel and execute ```npm run build```. This will compile the code to static files in the ./docs folder.
- then go into the version control tab, commit and push changes to your repo.
- make sure your repository is set as serving a github page from the ./docs folder.


# Technical considerations

Website code is under ./src and builds into ./docs

I started from a Node.js template and reconfigure the Run button to start snowpack via ```snowpack dev``` instead (see .replit file).

./docs/.nojekyll file tells github to not try to use jekyll on the files. We copy it on the build command, see ```snowpack build && touch ./docs/.nojekyll``` in package.json build script.

In ./snowpack.config.js you find:

```
module.exports = {
  
  mount: {
    src: '/',
  },
 
  buildOptions: {
    baseUrl: '/snowpack-boilerplate',
    out: './docs',
  },
  
};
```

- mount is to tell that the ./src folder contain the site files
- baseUrl is to prepend the name of your repo for base links (/) to work and redirect to (/snowpack-boilerplate)
- out is the place where the file will be generated by snowpack, we want this to be docs as per ghpages convention

See https://github.com/snowpackjs/snowpack/discussions/1423 for ghpage discussion


Finally, in src/index.html, notice the use of %PUBLIC_URL% to refer the the baseUrl.


Have fun!
