
# Dockerfile mẫu.
# Chú ý: Tất cả các từ khóa trong tệp Dockerfile cần được viết hoa
# Dockerfile có hai mục đích sử dụng chính.
#   1. Tạo các image, tái sử dụng, tự động tạo image. 
#   2. Sử dụng các lệnh để cài đặt thực hiện chương trình khi container được thực thi.
# Bất kỳ docker file cũng cần phải kế thừa từ một image đã có sẵn: của các hãng hoặc của người sử dụng đã tạo ra image trước đó.
# Trong dockerfile này sẽ giới thiệu và giải thích các lệnh cơ bản thường hay được sử dụng.
# Dockerfile này để demo cách đóng gói image cho ứng dụng được phát triển trên nền tảng NETFRAMEWORK

# Step 1: Kế thừa từ image microsoft/iis, được phát hành bởi microsoft. Tìm hiểu thêm về image này tại địa chỉ : https://hub.docker.com/_/microsoft-windows-servercore-iis
# Trong image đã cài đặt sẵn IIS công cụ hỗ trỡ deploy các ứng dụng .NET, nếu không muốn sử dụng IIS có thể sử dụng image khác tại đây https://hub.docker.com/search?q=windows&type=image 
FROM microsoft/iis
# Step 2: Thêm metadata vào cho image. Sử dụng LABEL 
LABEL title="Project demo docker"
LABEL publishby="SSI"
LABEL version="1.0"
LABEL description="This is image demo, create by SSI/IT/Team2"
# Step 3: Thêm tác giả tạo image. Sử Dụng MAINTANCE hoặc LABEL
LABEL maintainer="SSI Securities Corporation"
# Step 4: Đối với Windows để thực hiện các command thì sử dụng công cụ powershell. 
SHELL ["powershell"] 
# Step 5: Sử dụng lệnh RUN để cài đặt thêm một ứng dụng khi build image hoặc thực hiện một lệnh bất kỳ
# Ở đây sẽ cài thêm NET-Framework-45-ASPNET và Web-Asp-Net45
# Để phân cách giữa các lệnh RUN ta thêm ký tự \ cuối lệnh

RUN Install-WindowsFeature NET-Framework-45-ASPNET ; \
    Install-WindowsFeature Web-Asp-Net45
    
# Step 6: Copy files đã được publish vào image. Đây là thư mục sẽ được IIS trỏ đến khi container được run
COPY DemoDockerfile /inetpub/wwwroot
# Step 7 EXPOSE một hoặc nhiều cổng để map port khi container run
EXPOSE 80

# Để build image sử dụng powershell và cd đến thư mục có chứ Dockerfile
# thực hiện lệnh: docker build -t dockerdemo1:1.0 .
# Chú ý cần có ký tự . ở cuối lệnh.