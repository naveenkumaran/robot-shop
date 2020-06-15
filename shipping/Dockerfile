#
# Build
#
FROM ibmjava:8-sdk AS build

WORKDIR /opt/shipping
COPY . /opt/shipping

RUN apt-get update && apt-get -y install maven
RUN mvn install

#
# Run
#
FROM ibmjava:8-sfj

EXPOSE 8080

WORKDIR /opt/shipping

ENV CART_ENDPOINT=cart:8080
ENV DB_HOST=mysql

COPY --from=build /opt/shipping/target/shipping-1.0-jar-with-dependencies.jar shipping.jar

CMD [ "java", "-Xmn256m", "-Xmx768m", "-jar", "shipping.jar" ]