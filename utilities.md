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
