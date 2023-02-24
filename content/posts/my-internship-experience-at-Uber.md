---
title: "My internship experience at Uber"
date: "2022-12-11"
aliases: ["/my-internship-experience-at-Uber/"]
---
<p align="center">
  <img alt="Dark" async src="https://d3m889aznlr23d.cloudfront.net/img/events/id/458/458390133/assets/ed3e8240dc5d801438b664066d7231cf.image-24-.png" > </p><p align = "center">
~ Uber Mission Statement
</p>


Eight weeks. Summers in Bangalore. Uber credits for rides. 

Prior to this internship, I had a vivid picture of developing software at a large company: engineers spending eight continous hours over tedious work. I was very nervous of how will I be able to work at such a big comapny. Fortunately, my experience at Uber was nothing like that. 

In the summers of 2022, I’ve had the pleasure of being an intern on the Reliability team at Uber which is responsible to increase reliability of core services at Uber. For my summer project, I've been working on static call graph analysis to generate callgraph of function caller-callee relation in Golang. Callgraphs are a way to visualize the flow of function calls graphically. Static callgraph analysis shows how the functions in a program interact with each other without executing the project. This allows developers to understand the flow of the program and identify the potential faulty functions. Building all this appeared very daunting to me at first. But a senior member of my team broke the project into small pieces to make it easier for me to understand. 

My first task was to learn [Golang](https://go.dev/). I had the freedom to explore the Go documentation, and my mentor let me figure out how to learn the language in the way and timeframe that worked best for me. After a couple of weeks, I was comfortable enough with Go. My mentor walked me through how the Go monorepo worked and helped me setting up my environment.

The next stage of my project was research about callgraphs, so I began by reading through [SSA](https://en.wikipedia.org/wiki/Static_single-assignment_form)(Static Single Assignment), [IR](https://en.wikipedia.org/wiki/Intermediate_representation)(Intermediate Representation) under the guidance of my mentor. I did a lot of reading about how to use the SSA dump of a project to build its callgraph. I found the Go monorepo especially helpful in understanding the code implementation and skeleton structure of projects and packages. Initially, Pointer Analysis was used to build callgraph. However, it took a lot of time to build the callgraph using this method because it is a whole program analysis and it made multiple runs on the program to build a precise callgraph. This led to the constraint of building the callgraph only once in a day. Another issue with this method was that the virtual functions calls made via interface were absent in the graph. Hence there were broken links in the graph. I researched and found about CHA(Class Hierachy Anaylsis). Using the CHA algorithm we could prepare a table for the entire implements relation between interfaces and build a raw graph with a single run on the project. This way the problem of broken links due to the absence of virtual function calls was solved and a correct raw graph containing all the function calls was obtained. Cha also made graph building pretty fast (less than 2 minutes for some services). However, another issue was that it listed out all the possible function calls from libraries which increased the time taken to obtain the adjacency list from the raw callgraph but we needed only those calls which were made between functions inside our project. So I modified the dfs to print only those edges which had functions present within our project. This further optimized the time taken for getting adjacency list from the raw callgraph. I also faced issues due to the glue architecture and code being written twice in temporary location. Finally, with the help of my mentor, attached tags to point out the critical changes possible due to changes in a particular function. A keypoint mentioned by my mentor which would have made me more close to an ideal intern: Share with the team a documentation of time taken by each method of callgraph analysis for various services and update it timely.

Working on this project taught me a lot about how project development at a company works, how to learn without fear of failure, and importantance of working in a team. From my first day in the office itself, I found friendly people and colourful, sunny spaces. I found constant support whenever I encountered an issue or had a question. There would be someone in the team always available to help and they really made me feel part of a group here at Uber. This internship overturned my assumptions about the industry, as I was free to pursue projects that interested me, supported by a strong and welcoming community. 

I am thankful to my team, my friends, and everyone else who made my experience so wonderful! 

