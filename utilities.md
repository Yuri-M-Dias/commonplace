# General utilities that can be useful

##SSL
### Generating SSL cert using Java Keytool
	sudo keytool \
		-import \
		-alias certificate \
		-file ./ssl-config/certificate.crt \
		-keystore $JAVA_HOME/jre/lib/security/cacerts \
		-storepass changeit \
		-noprompt 
	sudo keytool \
		-genkey \
		-alias cas \
		-keyalg RSA \
		-keystore /vagrant/ssl-config/cas-server.jks \
		-dname "CN=localhost,OU=localhost, O=localhost, L=localhost, ST=localhost, C=BR" \
		-storepass changeit \
		-ext san=ip:192.168.33.89 \
		-noprompt
	sudo keytool \
		-exportcert \
		-alias cas \
		-file /vagrant/ssl-config/cas-server.crt \
		-keystore /vagrant/ssl-config/cas-server.jks \
		-storepass changeit \
		-noprompt
	sudo keytool \
		-delete -v \
		-keystore /usr/lib/jvm/java-8-oracle/jre/lib/security/cacerts \
		-storepass changeit \
		-alias cas
	sudo keytool \
		-import \
		-alias cas \
		-file /vagrant/ssl-config/cas-server.crt \
		-keystore /usr/lib/jvm/java-8-oracle/jre/lib/security/cacerts \
		-storepass changeit \
		-noprompt 
	sudo keytool \
		-import \
		-alias cas \
		-file /vagrant/ssl-config/cas-server.crt \
		-keystore $JAVA_HOME/jre/lib/security/cacerts \
		-storepass changeit \
		-noprompt 
	sudo keytool \
		-list -v \
		-keystore /usr/lib/jvm/java-8-oracle/jre/lib/security/cacerts \
		-storepass changeit \
		-alias cas
