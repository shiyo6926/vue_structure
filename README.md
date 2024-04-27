# lab8-group-a2

## how to use

👉  Get started with frontend with the following commands:
 http://localhost:8080
 $ cd my-vue-project
 $ npm run serve

👉  Get started with backend with the following commands:
 http://localhost:3000
 $ cd backend
 $ npm node app.js

 make sure run these two together to render the data from database
 -Karmen

## Update record

 04/28/2024 By Yaqi

Since I couldn't log on to github today, I recorded the changes to the framework in readme.:)

create some folders

src
| api //The api is created in this folder, such as base.js, and imported in index.js. For example, communication apis with the back end (like axios)
| assets
| components //The components that make up the page
| router
    └─index.js //router code, the case has been given in the file, according to fill in the content of the route
| utils //Method function, if needed
| views //Pages, such as login pages, user information pages, etc., all pages must be in this folder, cannot be written in app.vue or in components
    | user.vue //Not created yet,just as an example,created based on actual conditions
    └─home.vue //I moved the code from the previous app.vue to here and just changed the name
| App.vue //changed,there is no need to write any pages or code in app.vue
| main.js //changed,added import routing, apis, and external libraries like axios that I thought might use
