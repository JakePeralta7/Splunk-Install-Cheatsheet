# Splunk Install Cheatsheet

## Installation 
```
rpm -i <rpm_path>
/opt/splunk/bin/splunk start --accept-license
/opt/splunk/bin/splunk enable boot-start 
```

## Configuration
### Configure Ports
Edit the file `/opt/splunk/etc/system/local/web.conf` and add the stanza:
```
[settings]
httpport = 8000
mgmtHostPort = 127.0.0.1:8089
```

### Configure SSL
The certificate must be in Privacy-Enhanced Mail format and comply with the x.509 public key certificate standard.
Add the following settings to the `[settings]` stanza in `/opt/splunk/etc/system/local/web.conf`:
```
enableSplunkWebSSL = true
privKeyPath = /opt/splunk/etc/auth/mycerts/<mySplunkWebPrivateKey>.key
serverCert = /opt/splunk/etc/auth/mycerts/<mySplunkWebCertificate>.pem
```

## Restart Splunk Service
A reboot is required for the changes to take effect.
```
/opt/splunk/bin/splunk restart splunkd
```

## Install Add-ons
```
tar -xvzf <archived_app>
mv <extracted_app_folder> /opt/splunk/etc/apps
```