# license-maven-plugin-issue

`This is a short demo of an issue I detected in one of my projects. It is stripped down to portray the issue at hand.`

I have a multi-project setup with a parent child hierarchy. The parent project contains the configuration for the license-maven-plugin (basically the executions for the aggregate-add-third-party goal). There are two subprojects:

- submodule1 (this is a java application based e.g. on spring boot)
- submodule2 (this is a non java application not containing any dependencies)

subodule1 has a compile time dependency on submodule2.

When im running `mvn package` on the parent pom then the build succeeds but jar file of submodule1 does not contain the jar file of the submodule2 in the  BOOT-INF/lib folder.

When im running `mvn package -Dlicense.skipAggregateAddThirdParty=true` on the parent pom to skip the license plugin then the build succeeds and the submodule1 will contain the sumodule2 library in the  BOOT-INF/lib folder which is the behavior expected by me.
 
 I took a look at the maven debug output but I cannot pinpoint the issue. Can anyone chime in on this how to solve the issue or does anyone have an idea why the execution of the license-maven-plugin leads to the submodule2 dependency not being included? 