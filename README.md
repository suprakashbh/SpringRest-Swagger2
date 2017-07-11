# SpringRest-Swagger2
This sample demo to implement Spring with Swagger

1. Add dependency in pom.xml 
    springfox-swagger2 and springfox-swagger-ui
2. For Spring MVC with Swagger 2 ( non Spring boot)
    Add this below configuration in spring context xml  
        <mvc:resources mapping="swagger-ui.html" location="classpath:/META-INF/resources/" />
        <mvc:resources mapping="/webjars/**" location="classpath:/META-INF/resources/webjars/" />
        
        include swagger confuguration:
        <bean name="/swaggerConfig" class="pckg name" />
        
 3. Add new SwaggerConfig Class
 
@Configuration
@EnableSwagger2
public class SwaggerConfig {

	@Bean
	public Docket api() {
		return new Docket(DocumentationType.SWAGGER_2).select()
				.apis(RequestHandlerSelectors.basePackage("rest pckg directory"))
				.paths(PathSelectors.ant("/*")).
				build().apiInfo(apiInfo()).
				useDefaultResponseMessages(false);
	}

	private ApiInfo apiInfo() {
		ApiInfo apiInfo = new ApiInfo("My REST API", "Some custom description of API.", "API TOS", "Terms of service",
				"myeaddress@company.com", "License of API", "API license URL");
		return apiInfo;
	}
}
