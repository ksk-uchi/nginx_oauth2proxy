FROM alpine:3.5

RUN apk update
RUN apk add ca-certificates

COPY oauth2_proxy /bin/

ADD ./extra_whitelist.txt /root/extra_whitelist.txt

# To generate a strong cookie secret use python -c 'import os,base64; print base64.b64encode(os.urandom(16))'

CMD oauth2_proxy \
        --client-id='{your client id}' \
        --client-secret='{your client secret string}' \
        --cookie-domain='localhost' \
        --cookie-secret='{your cookie chars whatever you want}' \
        --cookie-secure=false \
        --http-address='0.0.0.0:4180' \
        --provider='google' \
        --proxy-prefix='/my_oauth' \
        --redirect-url='http://localhost/team' \
        --set-xauthrequest=true \
        --upstream='http://localhost/team' \
        --authenticated-emails-file='/root/extra_whitelist.txt'
