# Vecosy GIT configuration repository
## Add an application (myNewApp) version 1.0.0
```
$> git checkout master
$> git checkout -b myNewApp/1.0.0
```
### Add security
*optional if vecosy is started with `--insecure` option

#### generate keys

generate the private key

**IMPORTANT** : should be saved in an external safe place like *vault*

```
$ openssl genrsa -out priv.key 2048
# the filename has to be pub.key
$ openssl rsa -in priv.key -outform PEM -pubout -out pub.key
```
#### generate a jws token
##### install jose-util
```
$ go get -u github.com/square/go-jose/jose-util
$ go install github.com/square/go-jose/jose-util
```
##### generate jws token
```
# the jws payload is not important
$ echo "myAppName" | jose-util sign --key priv.key --alg RS256
```
the generated token can be used as *Bearer* or in the GRPC `token` metadata header

### Add some configuration
#### config.yml
```
db:
  user: mydbUser
  password: myDbPasword
```
### Commit the configuration
```
$> git add config.yml
$> git commit -m "created configu for myNewApp 1.0.0"
$> git push
```
## Configure vecosy server
### edit vecosy.yml adding the repo coordinate
```
repo:
  remote:
    url: https://github.com/vecosy/config-sample.git
    pullEvery: 2m
  local:
    path: /tmp/vecosyData

```

## Example
### Smart Config 
https://github.com/vecosy/config-sample/tree/app1/1.0.0
### Spring
https://github.com/vecosy/config-sample/tree/spring-app1/1.0.0