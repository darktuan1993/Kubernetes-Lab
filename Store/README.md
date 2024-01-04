### Storage POD

Mỗi pod khi khởi chạy sẽ có ít nhất 1 container bên trong và việc mount data vào trong container cũng giống như mount folder trong docker

### Cấu trúc file config
```bash
DECLARATIVE
      containers:
        - name: container-nginx
          image: nginx
          resources:
            limits:
              memory: "128Mi"
              cpu: "500m"

          volumeMounts:                          # Volume mount vào trong container 
            - name: demo-store-nginx             # Tên của volume
              mountPath: /usr/share/nginx/html   # Đường dẫn bên trong thư mục nằm container

      volumes:                                   # Chỉ định đường dẫn mount thư mục ra ngoài
        - name: demo-store-nginx                 # Tên của volume 
          hostPath:                              # Đường dẫn máy chủ
            path: /demo                          # Đường dẫn thư mục bên ngoài máy chủ            #
```

### Ưu và nhược điểm

Ưu: Không cần mount hay tạo PV , PVC, triển khai cho single node hoặc ứng dụng chạy trên 1 node
Nhược: Chỉ áp dụng cho ứng dụng chạy trên 1 node ko dùng đc cho deployment hoặc replicaset vì data không map nhau