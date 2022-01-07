COPY your data to ```./files/``` folder

```
docker build -t quay.io/roccqqck/smuggle .

docker push quay.io/roccqqck/smuggle
```

```
docker run -itd --name smuggle quay.io/roccqqck/smuggle 
 
docker cp <containerId>:/file/path/within/container /host/path/target

tar -xvzf files.tar.gz
```