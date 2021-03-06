# resty-gate

A Web Server or API Gateway based on OpenResty.

## Features

- [x] HTTPS to HTTP proxy, let's encrypt as certs.
- [x] limit traffic.
- [x] JWT auth.
- [x] upstream load balance.

## Install Deps

* `opm --cwd get openresty/lua-resty-limit-traffic`
* `opm --cwd get SkyLothar/lua-resty-jwt`

## Run

* `openresty -p . -c conf/nginx.conf`

## lets encrypt
* `lego --email="akagi201@gmail.com" --domains="akjong.com" --http run`

## TEST

### JWT Test

```bash
# apt-get install httpie || brew install httpie
$ http --print HBhb localhost/verify/ "Authorization:Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJmb28iOiJiYXIifQ.dtxWM6MIcgoeMgH87tGvsNDY6cHWL6MGW4LeYvnm1JA"
# token as url argument
$ http --print HBhb localhost/verify/?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJmb28iOiJiYXIifQ.dtxWM6MIcgoeMgH87tGvsNDY6cHWL6MGW4LeYvnm1JA
# token as cookie
$ http --print HBhb localhost/verify/ "Cookie:token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJmb28iOiJiYXIifQ.dtxWM6MIcgoeMgH87tGvsNDY6cHWL6MGW4LeYvnm1JA"
```