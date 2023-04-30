# notes_only
== Json Format==
 1. By default, spring requires Json with double quotes, for example: {"name":"Peter Smith"}. 
 2. curl in windows can be used to POST Json, but there's two things to remember:
   2.1 curl consumes double quotes in the command line input, for example, -d '{"name":"Peter"}' is received as {name:Peter}  
   2.2 curl requires double quotes to mark a string containning spaces. for example, -d "Peter Smith" is valid but -d 'Peter Smith' is invalid. 
 In conclusion, use curl in this manner: -d "{\"name\":\"Peter Smith\"}"
==Conflict between ReactJS and Devtools==
1. Typically, ReactJS constantly update static/built/bundle.js
2. With Devtools, the bundle.js file will stack in the old version, for unkown reason.
3. I've tried to fix this problem, but I couldn't. 
4. So, the solution so far is to remove Devtools to avoid the conflict.
5. I hope to investigate this conflict in the future. 
