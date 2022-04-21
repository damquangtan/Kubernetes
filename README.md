# Kubernetes

## Bài 1: Kubernetes là gì?

### Kubernetes là gì?

Kubernetes (ks8) là một nền tảng mã nguồn mở (open-source) được dùng để quản lý container, được phát triển bởi google.
Có thể dùng Kubernetes để phát triển ứng dụng trên nhiều nền tảng khác nhau on-premise, cloud hoặc virtual machines.

### Tại sao nên sử dụng Kubernetes?

Nó liên quan tới bài toán chạy ứng dụng bằng container (giải thích cách deploy ứng dụng theo cách truyền thống, deploy
ứng dụng sử dụng virtual machine và deploy ứng dụng sử dụng container).
Chạy ứng dụng bằng container sẽ giúp chúng ta rất nhiều vấn đề. Nhưng sẽ như thế nào nếu số lượng container là rất lớn?
Làm thế nào chúng ta có thể biết container nào sẽ thuộc về ứng dụng nào? Và nếu ta muốn tăng performance của ứng dụng
bằng cách cho nó chạy 2 hoặc 3 container thì làm thế nào ta dẫn request của ngưởi dùng tới 2 hoặc 3 container đó, ta sẽ
trỏ tới container nào? Và nếu server vật lý của chúng ta bị sự cố và không thể chạy nữa thì sao? **Kubernetes sẽ giúp chúng
ta giải quyết những vấn đề này nhiều nhất có thể**.

Kubernetes giúp ta nhóm và quản lý các container theo ứng dụng và project. Nó cũng cung cấp tính năng Service Discovery và
Load Balancing để chúng ta có thể dẫn request của ứng dụng tới đúng container. Và k8s cũng có tính năng giúp ứng dụng của
chúng ta high available nhất có thể, khi một server vật lý gặp sự cố, nó có thể chuyển container vật lý của ta sang server
vật lý khác. Ngoài ra ks8 còn nhiều tính năng khác: auto scale resource, auto restart application when failure, zero downtime
deployment, automated rollouts and rollbacks application, ...

### Kiến trúc của Kubernetes

Kubernetes cluster (một cụm bao gồm một master và một hoặc nhiều worker) bao gồm 2 thành phần chính:

- Master nodes (control plane)
- Worker nodes

![k8s architecture] (https://github.com/damquangtan/Kubernetes/blob/main/k8s.png)

Master nodes bao gồm 4 thành phần chính là:

- API Server: thành phần chính để giao tiếp với các thành phần khác.
- Controller manager: gồm nhiều controller riêng và thực hiện các chức năng cụ thể cho từng resource trong kube như create pod, create deployment, v..v.
- Scheduler: schedules ứng dụng tới node nào
- Etcd: Là một database để lưu giữ trạng thái và resource của cluster.

Master node chỉ có nhiệm vụ control state của cluster, nó không chạy ứng dụng trên đó, ứng dụng được chạy trên các worker node. Worker node gồm 3 thành phần chính như sau:

- Container runtime (docker, rkt hoặc nền tảng khác): chạy container
- Kubelet: Giao tiếp với API Server và quản lý container trong một worker node.
- Kubernetes Service Proxy (kube-proxy): quản lý network và traffic của ứng dụng trong worker node.

### Tài liệu tham khảo:

- https://viblo.asia
- https://kubernetes.io/docs/
