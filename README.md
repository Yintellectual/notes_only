# notes_only
== Json Format==
 1. By default, spring requires Json with double quotes, for example: {"name":"Peter Smith"}. 
 2. curl in windows can be used to POST Json, but there's two things to remember:
   2.1 curl consumes double quotes in the command line input, for example, -d '{"name":"Peter"}' is received as {name:Peter}  
   2.2 curl requires double quotes to mark a string containning spaces. for example, -d "Peter Smith" is valid but -d 'Peter Smith' is invalid. 
 In conclusion, use curl in this manner: -d "{\"name\":\"Peter Smith\"}"
 
 
== bundle.js created by ReactJS is not up-to-date ==
1. Typically, ReactJS constantly update static/built/bundle.js
2. Using Eclipse, you have to manually open bundle.js and save it, to trigger deployment on the embedded saver
3. this is stupid, hope to fix it somehow
4. bundle.js is a huge file, so open it with text editer to reduce the lag.


== Enable CORS for Spring Rest Data ==
[reference](https://github.com/spring-projects/spring-data-rest/blob/main/src/main/asciidoc/configuring-cors.adoc)
```
@Component
public class SpringDataRestCustomization implements RepositoryRestConfigurer {

  @Override
  public void configureRepositoryRestConfiguration(RepositoryRestConfiguration config, CorsRegistry cors) {

    cors.addMapping("/person/**")
      .allowedOrigins("http://domain2.example")
      .allowedMethods("PUT", "DELETE")
      .allowedHeaders("header1", "header2", "header3")
      .exposedHeaders("header1", "header2")
      .allowCredentials(false).maxAge(3600);
  }
}
```


== Promise, then, await in js ==

In modern javascript, remote calls like fetch() usually return a Promise instead of data directly. To use the data inside a Promise, there are 2 ways:
[reference: Javascript: How to access the return value of a Promise object](https://dev.to/ramonak/javascript-how-to-access-the-return-value-of-a-promise-object-1bck)
1. using Promise.then()
```
const address = fetch("https://jsonplaceholder.typicode.com/users/1")
  .then((response) => response.json())
  .then((user) => {
    return user.address;
  });

const printAddress = () => {
  address.then((a) => {
    console.log(a);
  });
};

printAddress();
```
2. using async / await syntax
```
const address = fetch("https://jsonplaceholder.typicode.com/users/1")
  .then((response) => response.json())
  .then((user) => {
    return user.address;
  });

const printAddress = async () => {
  const a = await address;
  console.log(a);
};

printAddress();
```


== Tailwind Buildin Free SVG Icons ==

Search icons in [https://heroicons.com/](https://heroicons.com/). 
Use icons like:
```
<ChevronRightIcon className="h-6 w-6">
```


== NextJS Toggle Display ==
Best practice:
```
<div style={showMyComponent? {}:{display:"none"}}>
```
