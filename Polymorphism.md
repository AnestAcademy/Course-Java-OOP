# Tính đa hình (Polymorphism)

<br />

**Tính đa hình (polymorphism)** là một trong bốn tính chất cơ bản của lập trình hướng đối tượng trong Java.  
**Tính đa hình** là khả năng một đối tượng có thể thực hiện một tác vụ theo nhiều cách khác nhau.

Đối với tính chất này, nó được thể hiện rõ nhất qua việc gọi phương thức của đối tượng. Các phương thức hoàn toàn có thể giống nhau, nhưng việc xử lý luồng có thể khác nhau.

Trong Java, chúng ta sử dụng nạp chồng phương thức (method overloading) và ghi đè phương thức (method overriding) để có tính đa hình.

<br />

## I. Overload (nạp chồng)

### 1. Khái niệm

Đây là khả năng cho phép một lớp có nhiều thuộc tính, phương thức cùng tên nhưng với các tham số khác nhau về loại cũng như về số lượng. Khi được gọi, dựa vào tham số truyền vào, phương thức tương ứng sẽ được thực hiện.

### 2. Các quy tắc cho việc Override

- Các method nằm trong cùng một class.
- Các method trùng tên.
- Các method khác số lượng tham số, nếu có cùng số lượng tham số thì các tham số phải khác kiểu dữ liệu.

#### Lưu ý:

- Trong Java, chúng ta không thể thực hiện nạp chồng phương thức chỉ bằng cách thay đổi kiểu trả về của phương thức đó.
- Hàm tạo cũng có thể được nạp chồng.

<br />

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
- Các phương thức **final**, **static**, **private** không thể ghi đè.

<br />

##  

© Copyright
> ANEST LEARNING  
> Join us: &nbsp;&nbsp;&nbsp; [Facebook groups](https://www.facebook.com/groups/anest.learning/)  
> Website: &nbsp; [https://anest.dev](https://anest.dev)  
