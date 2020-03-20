# boomicicd-sonarqube
SonarQube rules for Boomi Component XML

- The SonarQube Rules are published as an XML. In order to import the rules.
- Goto to the sonarqube-url/profiles. And click on the Restore button from the top right corner and choose the xml file.
- To install a docker image with the Boomi SonarQube rules go [here] (https://hub.docker.com/repository/docker/boomicicd/sonar)

Here are sample rules found in the XML.

|**Rule Name**|**Details**|**Definition**|
|-----|-----|-----|
|Components name|Component names shall not start with "New ".|/Component/Name/text()[starts-with(., 'New ')]|
|Process description|Process description must not be empty|/Component/Type[text()="process"]/../Description[not(text())]|
|Exceptions message |Business exception message shall have at least one parameter defined {1} |/Component/Object/process[@enableUserLog]/shapes/shape[@image="exception_icon"]/configuration/exception/exMessage/text()[not(contains(.,'{1}'))]|
|Business rules error message |Business rules error message shall have at least one parameter defined {1} |/Component/Object/process[@enableUserLog]/shapes/shape[@shapetype="businessrules"]/configuration/businessrules/rule/errorMessage/@content[not(contains(.,'{1}'))]|
|Connection URL |The connection property URL shall not be hard coded|/Component/Overrides/Connections/ConnectionOverride/field[@id="URL"][@overrideable='false']|
|Connection username|The connection property username shall not be hard coded|/Component/Overrides/Connections/ConnectionOverride/field[@id="user"][@overrideable='false']|
|Connection password|The connection property password shall not be hard coded|/Component/Overrides/Connections/ConnectionOverride/field[@id="password"][@overrideable='false']|
  
