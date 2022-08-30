# To deploy build artifacts through Artifactory you need to 
# add a deployment element with the URL of a target local repository to which you want to deploy your artifacts. For example:

<distributionManagement>
    <repository>
        <id>central</id>
        <name>a0tb5xt3n9ogu-artifactory-primary-0-releases</name>
        <url>https://cloudjfrogserver.jfrog.io/artifactory/manen-libs-release</url>
    </repository>
</distributionManagement>



# configure - generate settings

<?xml version="1.0" encoding="UTF-8"?>
<settings xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.2.0 http://maven.apache.org/xsd/settings-1.2.0.xsd" xmlns="http://maven.apache.org/SETTINGS/1.2.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <servers>
    <server>
      <username>${security.getCurrentUsername()}</username>
      <password>${security.getEscapedEncryptedPassword()!"*** Insert encrypted password here ***"}</password>
      <id>central</id>
    </server>
    <server>
      <username>${security.getCurrentUsername()}</username>
      <password>${security.getEscapedEncryptedPassword()!"*** Insert encrypted password here ***"}</password>
      <id>snapshots</id>
    </server>
  </servers>
  <profiles>
    <profile>
      <repositories>
        <repository>
          <snapshots>
            <enabled>false</enabled>
          </snapshots>
          <id>central</id>
          <name>manen-libs-release</name>
          <url>https://cloudjfrogserver.jfrog.io/artifactory/manen-libs-release</url>
        </repository>
        <repository>
          <snapshots />
          <id>snapshots</id>
          <name>manen-libs-snapshot</name>
          <url>https://cloudjfrogserver.jfrog.io/artifactory/manen-libs-snapshot</url>
        </repository>
      </repositories>
      <pluginRepositories>
        <pluginRepository>
          <snapshots>
            <enabled>false</enabled>
          </snapshots>
          <id>central</id>
          <name>manen-libs-release</name>
          <url>https://cloudjfrogserver.jfrog.io/artifactory/manen-libs-release</url>
        </pluginRepository>
        <pluginRepository>
          <snapshots />
          <id>snapshots</id>
          <name>manen-libs-snapshot</name>
          <url>https://cloudjfrogserver.jfrog.io/artifactory/manen-libs-snapshot</url>
        </pluginRepository>
      </pluginRepositories>
      <id>artifactory</id>
    </profile>
  </profiles>
  <activeProfiles>
    <activeProfile>artifactory</activeProfile>
  </activeProfiles>
</settings>
