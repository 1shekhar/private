# Embolder - Embold Test Automation
### _Automated validation for UI, API and DB_
------

## Features

- Pre-configured Maven based Java project
- Can be run via Terminal or IDE (Eclipse / IntelliJ) as standalone maven project
- Continuous Integration using Jenkins
- Effective Test Report generation using Allure

> Please note, this project is currently configured for Google Chrome, Mozilla Firefox and Microsoft Edge. Rest browsers are not supported yet.

## Pre-requisites

Following configuration is needed in order to run this project locally.

- [Apache Maven] 3.5+ (https://maven.apache.org/)
- [JRE] 8u171+(https://8u171.oracle.com/java/technologies/javase/javase8-archive-downloads.html)
- [Allure](https://docs.qameta.io/allure/#_installing_a_commandline)

> After installing above, make sure you have three environment variables set in your local machine - `${JAVA_HOME}`, `${M2_HOME}`, `${ALLURE_HOME}`

## Execution Steps

Clone this repository

```sh
mkdir uitests && cd uitests
git clone https://github.com/1shekhar/redstar
```

Run maven goal. You can configure above goal by providing some custom `${env}` variables. Currently you can provide browser and platform on which tests needs to be run. 
You can give your localhost URL too. For example,
```sh
mvn clean install -Dbrowser=firefox
```
or
```sh
mvn clean install -Dbrowser=edge -DappURL=https://v2.emboldct.dev
```
### Supported Environment Variables

| Environment Variable | Supported Value | Default Value |
| ------ | ------ | ------ |
| browser |chrome, edge, firefox | chrome |
| appURL | Any valid URL | https://app.gamma-staging.com |
| ghUser | Provide GitHub Username | NA |
| ghPass | Provide GitHub Password | NA |
| bbUser | Provide Bitbucket Username | NA |
| bbPass | Provide Bitbucket Password | NA |

When you run mvn command without providing any custom `${env}` by simply executing 
```sh
mvn clean install
```
Execution will be carried out with **Google Chrome** in non-headless mode on **[V2 Staging](https://app.gamma-staging.com)** 
Tests will use **Test_Credentials** of GitHub and Bitbucket account logins.
> Please note, execution will fail if Google Chrome or the browser you selected for execution is not installed on your local machine.

## Test Report Generation

Test report generation is carried out by using Allure framework. 
After successful / unsuccessful execution, **allure-results** directory gets created at root location (where pom.xml is located).
Simple run below command
```sh
allure serve allure-results
```

## Development

Want to contribute? Great!

Clone this repository and ask for collabortion access to owner.
#### Building for source

_Currently there are some issues with some dependencies. Will share build steps later._

## Configuration with Jenkins

Dillinger is very easy to install and deploy in a Docker container.

By default, the Docker will expose port 8080, so change this within the
Dockerfile if necessary. When ready, simply use the Dockerfile to
build the image.

```sh
cd dillinger
docker build -t <youruser>/dillinger:${package.json.version} .
```

This will create the dillinger image and pull in the necessary dependencies.
Be sure to swap out `${package.json.version}` with the actual
version of Dillinger.

Once done, run the Docker image and map the port to whatever you wish on
your host. In this example, we simply map port 8000 of the host to
port 8080 of the Docker (or whatever port was exposed in the Dockerfile):

```sh
docker run -d -p 8000:8080 --restart=always --cap-add=SYS_ADMIN --name=dillinger <youruser>/dillinger:${package.json.version}
```

> Note: `--capt-add=SYS-ADMIN` is required for PDF rendering.

Verify the deployment by navigating to your server address in
your preferred browser.

```sh
127.0.0.1:8000
```

## License

MIT

**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
