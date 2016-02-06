# Creating free Let's Encrypt certificates
1. Clone the Let's Encrypt repo

        git clone https://github.com/letsencrypt/letsencrypt && cd letsencrypt
2. Request a certificate for your domain

        ./letsencrypt-auto certonly --standalone-supported-challenges http-01 -d yourdomain.com
3. Let's Encrypt will bootstrap itself and request a certificate.
4. Profit!!! (Securely)
