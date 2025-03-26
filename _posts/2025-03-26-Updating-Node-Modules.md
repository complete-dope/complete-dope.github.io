---
layout: post
date: 2025-03-26
title : Editing the node modules
---

A noob method of playing with Node modules  

Steps to follow to update code from a node_module like `d3-force` directly !!

So what we get in a node_modules are the build folder that dont support HRM (hot reload module) so we have to make changes and then build that folder using the rollup module ( maybe we can use other libs also !!) 


Steps: 
1. Make that change in the file that you want !!(be it debugging statements or logic change  )
2. Install the required files, using `npm install` and if required change the package manager from yarn to npm    
3. Then lookup to package.json and you might find a function named "prepublishOnly"
4. Run the command `npm run prepublishOnly`, If the command requires the some folder , build those or remove those folders from the npm command  !!  
5. Then once you fix the errors , got the errors solved , then we build this file using `npm run prepublishOnly`
6. Then run the development server using the `npm run dev -- --cache`

This is how to rebuild a node-module  !!  

