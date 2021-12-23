Poms:
reservation-system

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.udacity.jpnd</groupId>
    <artifactId>reservation-system</artifactId>
    <version>1.0-SNAPSHOT</version>

    <packaging>pom</packaging>
    <name>Reservation system</name>

    <properties>
        <maven.compiler.source>11</maven.compiler.source>
        <maven.compiler.target>11</maven.compiler.target>
    </properties>

    <modules>
        <module>flightmodule</module>
        <module>hotelmodule</module>
        <module>packagemodule</module>
    </modules>

    <build>
        <pluginManagement>
            <plugins>
                <plugin>
                    <artifactId>maven-compiler-plugin</artifactId>
                    <version>3.8.1</version>
                </plugin>
            </plugins>
        </pluginManagement>
    </build>
</project>
flightmodule

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <parent>
        <groupId>com.udacity.jpnd</groupId>
        <artifactId>reservation-system</artifactId>
        <version>1.0-SNAPSHOT</version>
    </parent>

    <artifactId>flightmodule</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>jar</packaging>
    <name>flightmodule</name>
</project>
hotelmodule

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <parent>
        <groupId>com.udacity.jpnd</groupId>
        <artifactId>reservation-system</artifactId>
        <version>1.0-SNAPSHOT</version>
    </parent>

    <artifactId>hotelmodule</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>jar</packaging>
    <name>hotelmodule</name>
</project>
packagemodule

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <dependencies>
        <dependency>
            <groupId>com.udacity.jpnd</groupId>
            <artifactId>hotelmodule</artifactId>
            <version>1.0-SNAPSHOT</version>
            <scope>compile</scope>
        </dependency>
        <dependency>
            <groupId>com.udacity.jpnd</groupId>
            <artifactId>flightmodule</artifactId>
            <version>1.0-SNAPSHOT</version>
            <scope>compile</scope>
        </dependency>
    </dependencies>

    <parent>
        <groupId>com.udacity.jpnd</groupId>
        <artifactId>reservation-system</artifactId>
        <version>1.0-SNAPSHOT</version>
    </parent>

    <artifactId>packagemodule</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>jar</packaging>
    <name>packagemodule</name>

    <build>
        <pluginManagement>
            <plugins>
                <plugin>
                    <groupId>org.apache.maven.plugins</groupId>
                    <artifactId>maven-jar-plugin</artifactId>
                    <version>3.2.0</version>
                    <configuration>
                        <archive>
                            <manifest>
                                <addClasspath>true</addClasspath>
                                <classpathPrefix>lib/</classpathPrefix>
                                <mainClass>com.udacity.packagesearch.search.Main</mainClass>
                            </manifest>
                        </archive>
                    </configuration>
                </plugin>
            </plugins>
        </pluginManagement>
    </build>

</project>
Module Descriptors
flightmodule

module com.udacity.flight {
    exports com.udacity.flight.search;
    exports com.udacity.flight.model;
}
hotelmodule

module com.udacity.hotel {
    exports com.udacity.hotel.search;
    exports com.udacity.hotel.model;
    opens com.udacity.hotel.model;
}
packagemodule

module com.udacity.packagesearch {
    requires com.udacity.flight;
    requires com.udacity.hotel;
}
