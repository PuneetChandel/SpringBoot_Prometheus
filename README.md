# SpringBoot_Prometheus
SpringBoot Prometheus Graphana

## 1 Configure actuator in spring boot project
Refer Pom.xml 

## 2 Set appropriate application properties

management.endpoints.web.exposure.include=*
management.endpoints.web.expose=*
server.port=8080

#disable security
management.security.enabled=false

#Metrics related configurations
management.endpoint.metrics.enabled=true

#Prometheus
management.endpoint.prometheus.enabled=true
management.metrics.export.prometheus.enabled=true

## 3 start the App and access actuator

http://localhost:8080/actuator/

Data for prometheus will be available at : http://localhost:8080/actuator/prometheus prometheus can then scrape data from here

## 4 Install Prometheus

$ docker pull prom/prometheus

- Create yaml file

docker run --name prometheus -p 9090:9090 -v $PWD/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus

Access prometheus : http://localhost:9090/graph 

## 5 installing Graphana

#run Grafana
$ docker run --name grafana -i -p 3000:3000 grafana/grafana

#open Grafana WebUI and login 
$ open -a Safari http://localhost:3000
