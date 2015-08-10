# htmlunittest

Unzip `htmlunittest-webapp.zip` into a tomcat (webapp dir). Make sure the app name is `htmlunittest`. Start tomcat and
point the browser at [http://localhost:8080/htmlunittest/](http://localhost:8080/htmlunittest/) to make sure the page
loads ok in a browser.
  
Run the unit test in src/test/java/org/jenkins/js/AppTest.java. Change the HtmlUnit version in the pom.xml to see how
things work differently for different version of HtmlUnit.

#HtmlUnit v 2.6 (same as Jenkins core)
 
With `BrowserVersion.FIREFOX_2` (as used by `JenkinsRule`) or `BrowserVersion.FIREFOX_3` we get the following errors. This is the same as
I saw with Jenkins core and the Gus' new code.


```
com.gargoylesoftware.htmlunit.ScriptException: TypeError: Cannot find function isArray in object 
function (a, b) {
    return new n.fn.init(a, b);
}
. (http://localhost:8080/htmlunittest/jquery2.js#708)
======= EXCEPTION START ========
EcmaError: lineNumber=[708] column=[0] lineSource=[<no source>] name=[TypeError] sourceName=[http://localhost:8080/htmlunittest/jquery2.js] message=[TypeError: Cannot find function isArray in object 
function (a, b) {
    return new n.fn.init(a, b);
}
. (http://localhost:8080/htmlunittest/jquery2.js#708)]
com.gargoylesoftware.htmlunit.ScriptException: TypeError: Cannot find function isArray in object 
function (a, b) {
    return new n.fn.init(a, b);
}
. (http://localhost:8080/htmlunittest/jquery2.js#708)

```

#HtmlUnit v 2.18 (latest)

With `BrowserVersion.FIREFOX_38` or `BrowserVersion.CHROME`: Load fine !!!! There are a few CSS warnings, but it
doesn't totally bomb.