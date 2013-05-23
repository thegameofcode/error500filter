Error500 Filter
===============

A system that sends an email to a concrete recipients when a error 500 occurs in a web application. 

It is a very easy way to anticipate critical errors in production environments.

## Java

### Installation

- Download com.thegameofcode.filter.error500filter.jar
- Create error500filter.properties and use the following variables:

```
ERROR500_FILTER_FROM=email@domain.com
ERROR500_FILTER_TO=email@domain.com
ERROR500_FILTER_SUBJECT=[ERROR500] Subject description
ERROR500_FILTER_BODY=This message has been created automatically, please not respond to this message<br /><br />Request: ##REQUEST_INFO##<br /><br />ERROR: ##ERROR_INFO##
```

- Create your own Error500Filter.java class extending from com.thegameofcode.filter.Error500Filter

```JAVA
public class Error500Filter extends com.thegameofcode.filter.Error500Filter {

  	override protected sendHtmlEmail(String p_toMail, String p_fromEmail, String p_subject, String p_body){
		// Your own code to send email
	}

}
```

- Add the following filter into your web.xml file (replacing your.package. with your class package)

```XML
<filter>
  <filter-name>Error500Filter</filter-name>
	<filter-class>your.package.Error500Filter</filter-class>
</filter>
<filter-mapping>
	<filter-name>Aplication</filter-name>
	<url-pattern>/*</url-pattern>
</filter-mapping>
```


## NodeJs


