# Maven Commands

## Table of Contents
1. [Build Commands](#build-commands)
2. [Lifecycle Commands](#lifecycle-commands)
3. [Dependency Commands](#dependency-commands)
4. [Project Commands](#project-commands)
5. [Repository Commands](#repository-commands)
6. [Plugin Commands](#plugin-commands)
7. [Archetype Commands](#archetype-commands)
8. [Site Commands](#site-commands)
9. [Other Useful Commands](#other-useful-commands)

## Build Commands

### Clean
- **mvn clean:** Removes the target directory and everything in it.
  ```sh
  mvn clean
  ```
### Compile
- mvn compile: Compiles the source code of the project.
```sh
mvn compile
```
### Test
- mvn test: Runs the tests using a testing framework.
```sh
mvn test
```
### Package
mvn package: Packages the compiled code into a JAR or WAR file.
```sh
mvn package
```
### Install
mvn install: Installs the package into the local repository.
```sh
mvn install
```
### Deploy
mvn deploy: Deploys the package to a remote repository.
```sh
mvn deploy
```
## Lifecycle Commands
### Default Lifecycle
```sh
mvn validate   # Validate the project is correct and all necessary information is available.
mvn compile    # Compile the source code.
mvn test       # Test the compiled source code.
mvn package    # Package the compiled code into a JAR/WAR.
mvn verify     # Verify the package is valid and meets quality criteria.
mvn install    # Install the package into the local repository.
mvn deploy     # Deploy the package to a remote repository.
```
### Clean Lifecycle
```sh
mvn pre-clean  # Perform tasks before cleaning.
mvn clean      # Remove files generated during the build.
mvn post-clean # Perform tasks after cleaning.
```
### Site Lifecycle
```sh
mvn pre-site   # Perform tasks before generating site documentation.
mvn site       # Generate site documentation.
mvn post-site  # Perform tasks after site generation.
mvn site-deploy # Deploy generated site documentation to the specified server.
```
## Dependency Commands
### Dependency Tree
- mvn dependency:tree: Displays the dependency tree for the project.
```sh
mvn dependency:tree
```
### Dependency List
- mvn dependency:list: Lists all dependencies used by the project.
```sh
mvn dependency:list
```
### Dependency Analysis
- mvn dependency:analyze: Analyzes the project's dependencies and identifies used and unused ones.
```sh
mvn dependency:analyze
```
## Project Commands
### Archetype Creation
- mvn archetype:generate: Generates a new project based on an archetype.
```sh
mvn archetype:generate
```
### Validate
- mvn validate: Validates the project is correct and all necessary information is available.
```sh
mvn validate
```
### Project Info
- mvn help:describe: Describes the attributes of a specified goal or plugin.
```sh
mvn help:describe -Dplugin=org.apache.maven.plugins:maven-compiler-plugin
```
### Project Help
- mvn help:effective-pom: Displays the effective POM for the current build.
```sh
mvn help:effective-pom
```
## Repository Commands
### Repository Index
- mvn repository:index: Creates an index of the repository.
```sh
mvn repository:index
```
### Dependency Resolution
- mvn dependency:resolve: Resolves and displays the dependencies for the project.
```sh
mvn dependency:resolve
```
## Plugin Commands
### Plugin List
- mvn plugin:list: Lists all plugins used in the project.
```sh
mvn plugin:list
```
### Plugin Help
- mvn help:describe: Provides detailed information about a plugin goal.
```sh
mvn help:describe -Dplugin=org.apache.maven.plugins:maven-compiler-plugin
```
### Plugin Configuration
- mvn plugin:configuration: Displays the effective configuration for a plugin.
```sh
mvn help:effective-settings
```
## Archetype Commands
### Generate Project
- mvn archetype:generate: Generates a project from an archetype.
```sh
mvn archetype:generate -DgroupId=com.example -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
```
## Site Commands
### Site Generation
- mvn site: Generates the project’s site documentation.
```sh
mvn site
```
### Site Deployment
- mvn site:deploy: Deploys the generated site to the specified server.
```sh
mvn site:deploy
```
## Other Useful Commands
### Effective POM
- mvn help:effective-pom: Displays the effective POM configuration after inheritance and active profiles are applied.
```sh
mvn help:effective-pom
```
### Effective Settings
- mvn help:effective-settings: Displays the effective settings after merging global and user-level settings.
```sh
mvn help:effective-settings
```
### Clean Cache
- mvn dependency:purge-local-repository: Cleans the local repository of project artifacts.
```sh
mvn dependency:purge-local-repository
```
### Debug Mode
- mvn -X: Runs Maven in debug mode, providing detailed logs.
```sh
mvn -X clean install
```
### Skip Tests
- mvn -DskipTests: Skips running tests during the build.
```sh
mvn clean install -DskipTests
```
### Run Tests
- mvn test: Runs tests using the configured testing framework.
```sh
mvn test
```
### Clean and Install
- mvn clean install: Cleans the project and then installs the package into the local repository.
```sh
mvn clean install
```
### Profiles
- mvn -P<profile-name>: Activates a specific build profile.
```sh
mvn clean install -Pproduction
```
