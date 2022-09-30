
## Getting Started

### <u>Test a Non-Secure Application</u>
1. Build a fresh springboot Application using [Spring Initializer](https://start.spring.io). Add spring web dependency.
2. Create a Rest API by adding a controller layer 
```bash
@RestController
public class Controller
{
    @GetMapping("/hello")
    public String hello()
    {
        return "<h1>Hello User, have a nice day.<h1>";
    }
}
````
3. You can customize username and password by adding it in your application.properties file. 
```bash
  spring.security.user.name=<YourUsername>
  spring.security.user.password=<YourPassword>
```
Now, instead of using default spring security credentials, use these customized configured authentication credentials.

4. Now, run the application, then hit ROOT url : `http://localhost:8080/hello` in your browser.
### <u> Adding Spring Security to Springboot</u>

5. Add `spring-boot-starter-security` dependency in POM. 
```bash
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-security</artifactId>
</dependency>
```

| WARNING : For parent version (spring-boot-starter-parent) Version 2.7.1 is not able to work with spring security depenency on 26th June, 2022. Hence, using 2.7.0 |
|----------------------------------------------------------------------------|
<details>
    <summary><I>About the Spring Security Dependency</I></summary>

>This is a starter pack and a maven dependency, which pulls in all the necessary spring security dependecnies and makes them available for you, so that you do not need to download individual dependencies.<br><br>
> **Note :** Now, most of the springboot starter dependency don't have typically effect just after adding it to the class path, you also have 
to add some kind of configuration that goes with it in order to tell springboot that a dependency added, configure it. <br>
However, in spring security, it quite diferent. <br>
Just by adding the dependency in the class path, spring security immediately starts working.
</details>

### <u> Test a Secure Application</u>

6. Now, do `mvn clean install`, and hit the root URL : `http://localhost:8080/hello` in your browser after running application. You will see there is a sign-in form now. This sign in form also do login validations.

<details>
 <summary><I>How Spring Security Dependency internally works ? </I></summary>

> Hi, how just by adding spring security dependency to the class path, it is verifying you and stopping you to access the spring application. How this dependency is able to do so much ? <br>
It is because of the _Filters_.<br><br>
> **Filters** one of those core concepts associated with servlet.Spring boot and spring security all of these build on top of the servlet technologies, so that we do not has to deal with a servlet layer.<br><br>
Think of a web app and you have a bunch of servlets in it which does the work when a user makes a request.
So, when a user makes a request to a URL, there will a particular servlet that will do the functionality and will provide the response for that particular request. So, this is the servlet work.<br><br> 
> **How Filters works ?** <br>
Now, Filters will stand in front of servlet and intercept every request and gives you an opportunity to do something with each requests. You can think it like a cross cutting, pieces of functionality that you can use in may ways like,<br>
> a) to log every request<br>
> b) check if a particular header is there in every request or not<br><br>
> So, while the servlets are mapped to the URLs, filters can be applied to all URLs that intercept all the URLs that may allow or deny any requests.<br>
> Similarly, _spring security_ is just doing a filter and examining all the requests to allow or deny the request as per what it should be doing.

> **Spring Security Default Behaviour**
* Add Mandatory authenications for URLs
* Add login forms
* Handles login error
* Creates a user and sets a default password 

</details>

7. Enter is the configured customized user ID and password.

**Congratulations! You have secured you springboot application with customized credentials.**

## References

[This Project is Well explained by Java Brains](https://www.youtube.com/watch?v=PhG5p_yv0zs&list=PLqq-6Pq4lTTYTEooakHchTGglSvkZAjnE&index=3)
