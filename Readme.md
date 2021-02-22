Functional version of the SnowPack "Getting Started" tutorial as of 22/02/2021.

See: https://www.snowpack.dev/tutorials/getting-started#install-snowpack

I started from a Node.js template and reconfigure the Run button to start snowpack instead (see .replit).


== 

I tried to make it deploy automatically to github pages by:

- building into the ./docs folder: "npm run build" + see snowpack.config
- commit and push
- make a github page for the repo


Should work well but still need ot understand how to:
- build from a src folder because otherwise snowpack seems to copy everything over, including the .git folder. This makes the commit impossible as repl consider it as a submodule
- also building from src, I cannot remove the index.js file from / (due to repl.it limitation from the node.js template I suppose)
- need to ammend the baseUrl when building to the correct one for the github pages
