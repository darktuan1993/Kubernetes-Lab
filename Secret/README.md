### Secret

Secret là một tài nguyên giúp bạn quản lý cấu hình của ứng dụng mà không cần thay đổi mã nguồn. Secret tương tự như configMap, ngoại trừ nó được mã hóa. Có 2 bước tạo

```bash
DECLARATIVE
        apiVersion: v1              # Api
        kind: Secret                # Loại
        metadata:                   # metadata
            name:  secretName       # tên
        data:                       # Dữ liệu
            secretKey:  BASE64_ENCODED_VALUE    # Giá trị giải mã Base64
        type: Opaque                #
```

### Chạy lệnh tạo configmap bằng imperative

Đọc secret từ 1 file bên ngoài

```bash
  kubectl create secret generic secret-1 --from-env-file=secret.properties
```
=> secret đã được tạo secret/secret-1 created

### Kiểm tra lại trên hệ thống

```bash
  kubectl get secret
```

```bash
  kubectl get secret <tên secret> -oyaml
```