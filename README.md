# AWS Signature Version 4 Policy for Mule 4.x

This policy handles the AWS Signature V4 signing process to allow you to make a AWS request by HTTP. It is dependent on the AWS Signature Version 4 Extension for Mule 4 (https://github.com/djuang1/awsv4auth-extension)

> :warning: **MuleSoft Enterprise Repository Required**: This project requires that you are a MuleSoft customer with an [Enterprise License](https://docs.mulesoft.com/mule-runtime/4.3/maven-reference#configure-mulesoft-enterprise-repository). If you don't have credentials, contact Support and request Nexus enterprise credentials. 

You must publish your AWS Signature Version 4 Extension to the same Anypoint Platform organization that will use this custom policy. When you publish this policy to your Anypoint Platform organization, you need to reference the extension in your pom.xml file.

```
<dependency>
    <groupId>${org_id}</groupId>
    <artifactId>awsv4auth-extension</artifactId>
    <version>1.0.0</version>
    <classifier>mule-plugin</classifier>
</dependency>
```

### Instructions

1.  Clone the Repo
2.  Change the pom.xml `groupId` to match your organization id in your Anypoint Platform organization
2.  Change the pom.xml `awsv4auth-extension.version` to match the version of the connector in your Anypoint Platform organization
3.  Make sure your Maven `settings.xml` file has the correct servers and repositories (MuleSoft Enterprise Repository) setup. The credentials for the Enterprise Repository are different from your Anypoint Platform credentials.
```
  <servers>
    <server>
      <id>exchange-server</id>
      <username>ANYPOINT_USERNAME</username>
      <password>ANYPOINT_PASSWORD</password>
    </server>
    <server>
      <id>MuleRepository</id>
      <username>EE_LIC_USERNAME</username>
      <password>EE_LIC_PASSWORD</password>
    </server>
  </servers>
...
  <profiles>
    <profile>
      <id>Mule</id>
      <activation>
        <activeByDefault>true</activeByDefault>
      </activation>
      <repositories>
        <repository>
          <id>MuleRepository</id>
          <name>MuleRepository</name>
          <url>https://repository.mulesoft.org/nexus-ee/content/repositories/releases-ee/</url>
          <layout>default</layout>
          <releases>
            <enabled>true</enabled>
          </releases>
          <snapshots>
            <enabled>true</enabled>
          </snapshots>
        </repository>
      </repositories>
    </profile>
  </profiles>
...

```
4.  Deploy the policy to your [Exchange using Maven](https://docs.mulesoft.com/exchange/to-publish-assets-maven):  
```
mvn clean deploy
```
5.  Apply the policy to your API through API Manager

## Updates

Last Updated September 17, 2020

If you have questions or issues, e-mail Dejim Juang at dejimj@gmail.com.
