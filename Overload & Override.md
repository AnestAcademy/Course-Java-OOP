# Overload & Override

## I. Overload

## II. Override (ghi đè)

### 1. Khái niệm

- **Override** là một tính năng cho phép một lớp con cung cấp một triển khai cụ thể của phương thức đã được cung cấp bởi một trong các lớp cha của nó. Nói dễ hiểu hơn, nếu lớp con có một hoặc nhiều phương thức giống với một trong các lớp cha của nó, thì đó là ghi đè phương thức.
- **Override** được sử dụng để thu được tính đa hình tại runtime.

### 2. Các quy tắc cho việc Override

- Override method phải cùng tên với method với class cha.
- Override method phải có cùng tham số giống với method class cha (số lượng, kiểu dữ liệu, thứ tự).
- Phải là quan hệ IS-A (kế thừa).
- Access modifier của phương thức ghi đè phải giống hoặc lớn hơn phạm vi của access modifier phương thức được ghi đè của class cha.
  - Ví dụ chúng ta không thể ghi đè một phương thức **public** bằng một phương thức **private**. Nếu không, tình huống xảy ra là một lời gọi phương thức đã được trình biên dịch chấp nhận vì tưởng là phương thức **public** nhưng đến khi nó chạy lại bị máy ảo từ chối vì phiên bản được gọi lại là **private**.
- Các phương thức **final**, **static**, **private** không thể cài đè.
