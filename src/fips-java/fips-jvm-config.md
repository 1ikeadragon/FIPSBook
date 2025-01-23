# Configuring JVM for FIPS Mode

## Adding Bouncy Castle Provider

What not to do:
```java
Security.addProvider()
```
What to do:
```java
Security.InsertAt();
```
Or, 
Manually modify `java.security` file to add providers. Example:
```java
security.provider.1=org.bouncycastle.jcajce.provider.BouncyCastleFipsProvider C:HYBRID;ENABLE{All};
security.provider.2=org.bouncycastle.jsse.provider.BouncyCastleJsseProvider fips:BCFIPS
security.provider.3=SUN
security.provider.4=SunJGSS
securerandom.source=file:/dev/urandom
securerandom.strongAlgorithms=NativePRNGBlocking:SUN,DRBG:SUN
securerandom.drbg.config=
login.configuration.provider=sun.security.provider.ConfigFile
policy.provider=sun.security.provider.PolicyFile
policy.expandProperties=true
policy.allowSystemProperty=true
policy.ignoreIdentityScope=false
keystore.type=BCFKS
keystore.type.compat=true
```
