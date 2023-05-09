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
