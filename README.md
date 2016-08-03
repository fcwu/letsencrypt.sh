# QNAP letsencrypt.sh 

The original repo is [letsencrypt.sh](https://github.com/lukas2511/letsencrypt.sh)

# Getting started

**NOTE: your domain must be reachable from port 80, such as http://your.domain/. Replace your.domain to your REAL domain**

```
[~] # curl -Lk https://github.com/fcwu/letsencrypt.sh/raw/master/letsencrypt.sh > letsencrypt.sh
[~] # export domain=your.domain
[~] # chmod +x letsencrypt.sh
[~] # cat <<EOF > domains.txt
> ${domain}
> EOF
[~] echo "WELLKNOWN=/share/Web/.well-known/acme-challenge" > config
[~] bash -c "source config && mkdir -p \${WELLKNOWN}"
[~] # ./letsencrypt.sh -c -o certs
# INFO: Using main config file /root/config
Processing your.domain
 + Signing domains...
 + Creating new directory certs/your.domain ...
 + Generating private key...
 + Generating signing request...
 + Requesting challenge for your.domain...
 + Responding to challenge for your.domain...
 + Challenge is valid!
 + Requesting certificate...
 + Checking certificate...
 + Done!
 + Creating fullchain.pem...
 + Done!
[~] # cat cert/${domain}/privkey.pem cert/${domain}/cert.pem > /etc/stunnel/stunnel.pem
[~] # /etc/init.d/stunnel.sh reload_apache
```
