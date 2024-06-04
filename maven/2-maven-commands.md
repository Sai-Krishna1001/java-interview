# Maven Commands

| **Section**         | **Command**                          | **Description**                                                                                         |
|---------------------|--------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Build Lifecycle** | `mvn validate`                       | Validates the project is correct and all necessary information is available.                            |
|                     | `mvn compile`                        | Compiles the source code of the project.                                                                |
|                     | `mvn test`                           | Runs tests using a suitable unit testing framework. These tests should not require the code to be packaged or deployed. |
|                     | `mvn package`                        | Takes the compiled code and packages it in its distributable format, such as a JAR.                     |
|                     | `mvn verify`                         | Runs any checks to verify the package is valid and meets quality criteria.                              |
|                     | `mvn install`                        | Installs the package into the local repository, for use as a dependency in other projects locally.      |
|                     | `mvn deploy`                         | Copies the final package to the remote repository for sharing with other developers and projects.       |
| **Clean Lifecycle** | `mvn clean`                          | Cleans up the output of the previous build by deleting the `target` directory.                           |
| **Site Lifecycle**  | `mvn site`                           | Generates a site based on the information in the POM.                                                    |
|                     | `mvn site:site`                      | Generates the project's site documentation.                                                              |
|                     | `mvn site:deploy`                    | Deploys the generated site to the specified location.                                                    |
|                     | `mvn site:stage`                     | Stages the site locally in a specific directory.                                                         |
|                     | `mvn site:stage-deploy`              | Deploys the staged site to the specified location.                                                       |
| **Project Info**    | `mvn help:effective-pom`             | Displays the effective POM as an XML for the current build, with values inherited from the parent POMs and profiles. |
|                     | `mvn help:effective-settings`        | Displays the effective settings for the current build, with values inherited from the user and global settings files. |
|                     | `mvn help:describe -Dplugin=<name>`  | Describes the attributes of a plugin, including its goals and parameters.                                |
|                     | `mvn help:evaluate -Dexpression=<expression>` | Evaluates the specified Maven expression and prints its value.                                       |
| **Dependency Mgmt** | `mvn dependency:resolve`             | Displays a list of dependencies for the project.                                                         |
|                     | `mvn dependency:tree`                | Displays the dependency tree for the project.                                                            |
|                     | `mvn dependency:list`                | Lists all dependencies used by the project.                                                              |
|                     | `mvn dependency:analyze`             | Analyzes the project's dependencies and lists any unused declared dependencies or used undeclared dependencies. |
|                     | `mvn dependency:analyze-dep-mgt`     | Analyzes your dependency management and lists mismatched versions.                                       |
|                     | `mvn dependency:analyze-only`        | Analyzes the project's dependencies but does not make any changes.                                       |
|                     | `mvn dependency:copy`                | Copies a specific artifact to a location defined by the user.                                            |
|                     | `mvn dependency:purge-local-repository` | Deletes specified dependencies and then re-resolves them.                                           |
| **Plugin Mgmt**     | `mvn plugin:help -Dgoal=<goal>`      | Displays help information on a specific plugin goal.                                                     |
|                     | `mvn plugin:describe -Dplugin=<name>`| Describes a specific plugin, including its goals and parameters.                                         |
|                     | `mvn plugin:download -DgroupId=<groupId> -DartifactId=<artifactId> -Dversion=<version>` | Downloads a specific plugin version to the local repository. |
|                     | `mvn plugin:report`                  | Generates a report for the specified plugin.                                                             |
| **Release**         | `mvn release:prepare`                | Prepares a release by updating POM versions, tagging in the SCM, and creating release POMs.              |
|                     | `mvn release:perform`                | Performs a release by deploying the release version, tagging the SCM, and creating the next development version. |
|                     | `mvn release:clean`                  | Cleans up after a release preparation that did not complete.                                             |
|                     | `mvn release:rollback`               | Rolls back a previous release preparation.                                                               |
| **Archetype**       | `mvn archetype:generate`             | Generates a new project from an archetype, or a template.                                                |
|                     | `mvn archetype:generate -DgroupId=<groupId> -DartifactId=<artifactId> -DarchetypeArtifactId=<archetypeArtifactId> -DinteractiveMode=false` | Generates a project from an archetype with specified groupId, artifactId, and archetypeArtifactId without interactive mode. |
|                     | `mvn archetype:generate -Dfilter=<filter>` | Generates a project from an archetype with a filter applied to the list of archetypes.            |
|                     | `mvn archetype:crawl`                | Crawls a remote repository for archetypes.                                                               |
| **Repository Mgmt** | `mvn deploy:deploy-file`             | Deploys a file to the remote repository.                                                                 |
| **Help**            | `mvn help:help`                      | Displays help information on using Maven.                                                                |
|                     | `mvn help:describe`                  | Describes the attributes of a plugin, including its goals and parameters.                                |
|                     | `mvn help:system`                    | Displays a list of the system properties for this build environment.                                     |
