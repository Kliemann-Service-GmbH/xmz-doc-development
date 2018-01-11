# Buildsystem

- via Docker
- https://github.com/zzeroo/easy-build



```bash
docker build -t zzeroo/build-yocto ../build-yocto/
```


```bash
mkdir src/easy-build/shared
cd src/easy-build/shared/
```


```bash
docker run -ti --volume=(pwd):/home/build/ zzeroo/build-yocto:latest
```
