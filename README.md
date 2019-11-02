# Vecosy GIT configuration repository
## Add an application (myNewApp) version 1.0.0
```
$> git checkout master
$> git checkout -b myNewApp/1.0.0
```
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