# dockerfiles
https://hub.docker.com/u/roccqqck


```
git clone https://github.com/roccqqck/dockerfiles
cd dockerfiles/miniconda3-ssh
ls -a
```
會有一個```Dockerfile```
```
docker build -t 帳號/名字:版本
docker build -t roccqqck/miniconda3-ssh:20191218 .
```

上傳到自己的docker帳號
```
docker push roccqqck/miniconda3-ssh:20191218
```
輸入docker帳號密碼