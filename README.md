# SpringBoot_Prometheus
SpringBoot Prometheus Graphana

## 1 Configure actuator,prometheus properties in project
Refer Pom.xml 

 <!-- Spring boot actuator to expose metrics endpoint -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>

        <!-- Micormeter core dependecy  -->
        <dependency>
            <groupId>io.micrometer</groupId>
            <artifactId>micrometer-core</artifactId>
        </dependency>


        <!-- Micrometer Prometheus registry  -->
        <dependency>
            <groupId>io.micrometer</groupId>
            <artifactId>micrometer-registry-prometheus</artifactId>
        </dependency>

## 2 Set appropriate application properties

management.endpoints.web.exposure.include=* <br />
management.endpoints.web.expose=*<br />
server.port=8080<br />

#disable security<br />
management.security.enabled=false<br />


#Metrics related configurations<br />
management.endpoint.metrics.enabled=true<br />

#Prometheus<br />
management.endpoint.prometheus.enabled=true<br />
management.metrics.export.prometheus.enabled=true<br />

## 3 start the App and access actuator

http://localhost:8080/actuator/<br />

Data for prometheus will be available at : http://localhost:8080/actuator/prometheus prometheus can then scrape data from here<br />

## 4 Install Prometheus

$ docker pull prom/prometheus<br />

Create yaml file, refer the prometheus.yml <br />

docker run --name prometheus -p 9090:9090 -v $PWD/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus <br />

Access prometheus : http://localhost:9090/graph <br />

## 5 installing Graphana

#run Grafana<br />
$docker run --name grafana -i -p 3000:3000 grafana/grafana<br />

#open Grafana WebUI and login <br />
$ open -a Safari http://localhost:3000<br />
