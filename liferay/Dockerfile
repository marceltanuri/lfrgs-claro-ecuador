FROM liferay/dxp:7.3.10-ga1

EXPOSE 8080 8000 11311

ENV LIFERAY_HOME /opt/liferay
ENV TOMCAT_HOME $LIFERAY_HOME/tomcat

USER root

# Add Liferay license (with permissions to liferay user)
COPY deploy/activation-key-digitalenterprisedevelopment-7.3-liferaycom.xml $LIFERAY_HOME/deploy
RUN chown -R liferay:liferay $LIFERAY_HOME/deploy

# Add OSGi configs (with permissions to liferay user)
#COPY osgi/configs/* $LIFERAY_HOME/osgi/configs
#RUN chown -R liferay:liferay $LIFERAY_HOME/osgi/configs/*

# Configure database conection (with permissions to liferay user)
COPY tomcat/conf/Catalina/localhost/* $TOMCAT_HOME/conf/Catalina/localhost/
RUN chown -R liferay:liferay $TOMCAT_HOME/conf/Catalina/localhost/*

# Add database libs (mysql and oracle) (with permissions to liferay user)
COPY tomcat/lib/ext/* $TOMCAT_HOME/lib/ext/
RUN chown -R liferay:liferay $TOMCAT_HOME/lib/ext/*

# Configure Liferay (with permissions to liferay user)
COPY properties/* $LIFERAY_HOME/
RUN chown -R liferay:liferay $LIFERAY_HOME/*

USER liferay

WORKDIR $LIFERAY_HOME