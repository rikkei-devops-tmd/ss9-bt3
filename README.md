BAI 3: VIET DOCKERFILE 3 DONG DONG GOI TRANG WEB HTML TINH

1. MUC TIEU
- Viet tep Dockerfile toi gian de tu dong goi trang HTML tinh vao Docker Image.
- Xay dung image my-html-app:v1 bang Docker Build.
- Khoi chay container tu image vua tao tren cong 8081 va kiem tra phan hoi.

2. CAU TRUC TEP TIN
- index.html: Tep ma nguon HTML tinh.
- Dockerfile: Huong dan dong goi image su dung base image nginx:alpine.
- README.md: Huong dan va nhat ky thuc hien.

3. MA NGUON

3.1. Tep index.html
```html
<h1>Hello Docker Session 09!</h1>
```

3.2. Tep Dockerfile
```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
```

4. QUY TRINH THUC HIEN VA KET QUA TERMINAL THUC TE

4.1. Xay dung Docker Image
Lenh thuc hien:
```bash
docker build -t my-html-app:v1 .
```
Ket qua dau ra:
```text
#0 building with "default" instance using docker driver

#1 [internal] load build definition from Dockerfile
#1 transferring dockerfile: 104B done
#1 DONE 0.0s

#2 [internal] load metadata for docker.io/library/nginx:alpine
#2 DONE 0.1s

#3 [internal] load .dockerignore
#3 transferring context: 2B done
#3 DONE 0.0s

#4 [internal] load build context
#4 transferring context: 71B done
#4 DONE 0.0s

#5 [1/2] FROM docker.io/library/nginx:alpine@sha256:df221db836e1754089190208cee7eeda94f233197056426eda74a43ab1abeac2
#5 resolve docker.io/library/nginx:alpine@sha256:df221db836e1754089190208cee7eeda94f233197056426eda74a43ab1abeac2 0.1s done
#5 DONE 0.1s

#6 [2/2] COPY index.html /usr/share/nginx/html/index.html
#6 CACHED

#7 exporting to image
#7 exporting layers done
#7 exporting manifest sha256:b70daa16489021b191d1e33d2cd71495c28560529e78cbf4af2069384d05cd1b done
#7 exporting config sha256:0d013cb77cafe3f3d69c79e2d29edc314194e7758d988efa649894e76e86f9fa done
#7 exporting attestation manifest sha256:daf1651297918544b50001013bdca34e407d121d124a405575164433b8965e0e 0.1s done
#7 exporting manifest list sha256:2e5047a1a05e68f8de63b454db0501940b128e07f7d5eb4a952339572282d98e 0.0s done
#7 naming to docker.io/library/my-html-app:v1 done
#7 unpacking to docker.io/library/my-html-app:v1 0.0s done
#7 DONE 0.2s
```

4.2. Khoi chay container tu image vua build
Lenh thuc hien:
```bash
docker run -d -p 8081:80 --name html-app my-html-app:v1
```
Ket qua dau ra:
```text
07a9b20e3b5727ff59a47f9bc7b459924f10015d0333f6a7bfbb0a21e054df30
```

4.3. Kiem tra danh sach container dang chay
Lenh thuc hien:
```bash
docker ps
```
Ket qua dau ra:
```text
CONTAINER ID   IMAGE            COMMAND                  CREATED        STATUS                  PORTS                                     NAMES
07a9b20e3b57   my-html-app:v1   "/docker-entrypoint.…"   1 second ago   Up Less than a second   0.0.0.0:8081->80/tcp, [::]:8081->80/tcp   html-app
```

4.4. Kiem tra phan hoi web server
Lenh thuc hien:
```bash
curl -s http://localhost:8081
```
Ket qua dau ra:
```text
<h1>Hello Docker Session 09!</h1>
```

4.5. Don dep container va image sau thu nghiem
Lenh thuc hien:
```bash
docker stop html-app && docker rm html-app
```
Ket qua dau ra:
```text
html-app
html-app
```

5. TONG KET CAC LENH
```bash
docker build -t my-html-app:v1 .
docker run -d -p 8081:80 --name html-app my-html-app:v1
docker ps
curl -s http://localhost:8081
docker stop html-app && docker rm html-app
```
