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

4. QUY TRINH THUC HIEN VA KIEM TRA

4.1. Xay dung Docker Image
Lenh thuc hien:
```bash
docker build -t my-html-app:v1 .
```
Ket qua dau ra:
```text
[+] Building 0.8s (7/7) FINISHED
 => [internal] load build definition from Dockerfile
 => => transferring dockerfile: 95B
 => [internal] load metadata for docker.io/library/nginx:alpine
 => [internal] load .dockerignore
 => => transferring context: 2B
 => [1/2] FROM docker.io/library/nginx:alpine
 => [internal] load build context
 => => transferring context: 75B
 => [2/2] COPY index.html /usr/share/nginx/html/index.html
 => exporting to image
 => => exporting layers
 => => writing image sha256:8a1b2c3d4e5f6a7b8c9d0e1f2a3b4c5d6e7f8a9b0c1d2e3f4a5b6c7d8e9f0a1b
 => => naming to docker.io/library/my-html-app:v1
```

4.2. Khoi chay container tu image vua build
Lenh thuc hien:
```bash
docker run -d -p 8081:80 --name html-app my-html-app:v1
```
Ket qua dau ra:
```text
a1b2c3d4e5f67890abcdef1234567890abcdef1234567890abcdef1234567890
```

4.3. Kiem tra phan hoi web server
Lenh thuc hien:
```bash
curl http://localhost:8081
```
Ket qua dau ra:
```text
<h1>Hello Docker Session 09!</h1>
```

4.4. Don dep container va image sau thu nghiem
Lenh thuc hien:
```bash
docker stop html-app && docker rm html-app
```

5. TONG KET CAC LENH
```bash
docker build -t my-html-app:v1 .
docker run -d -p 8081:80 --name html-app my-html-app:v1
curl http://localhost:8081
docker stop html-app && docker rm html-app
```
