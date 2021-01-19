# Abstraction

<br />

**Tính trừu tượng trong lập trình hướng đối tượng** là chỉ nêu ra vấn đề mà không hiển thị cụ thể, chỉ hiện thị tính năng thiết yếu đối với đối tượng người dùng mà không nói quy trình hoạt động. Ví dụ: như tạo ra tính năng gửi tin nhắn, ta chỉ cần hiểu là người dùng viết tin rồi nhấn gửi đi. Còn quy trình xử lý tin nhắn gửi như thế nào thì ta chưa đề cập đến.

Như vậy, tính trừu tượng là che giấu thông tin thực hiện từ người dùng, họ chỉ biết tính năng được cung cấp: Chỉ biết thông tin đối tượng thay vì cách nó sử dụng như thế nào. Nó có những ưu điểm sau:

- Cho phép lập trình viên bỏ qua những phức tạp trong đối tượng mà chỉ đưa ra những khái niệm phương thức và thuộc tính cần thiết. Ta sẽ dựa những khái niệm đó để viết ra, nâng cấp và bảo trì.
- Nó giúp ta tập trung cái cốt lõi đối tượng. Giúp người dùng không quên bản chất đối tượng đó làm gì.

<br />

## I. Abstract class (Lớp trừu tượng)

Lớp trừu tượng là lớp được khai báo mà **không thể tạo ra đối tượng** từ lớp đó. Ta sẽ tạo những lớp con kế thừa lớp trừu tượng.

Mục đích lớp trừu tượng là tạo ra lớp chung cho những lớp có liên quan với nhau kế thừa.

Ví dụ khi xây dựng phần mềm quản lý nhà trường: Những lớp sinh viên, giảng viên, cán bộ... có những thuộc tính và phương thức chung như tên, năm sinh, quê quán... thì ta sẽ tạo một lớp con người là lớp trừu tượng và những đặc điểm chung được để trong lớp con người. Khi phát triển chương trình, ta chỉ có thể tạo các đối tượng từ lớp con kế thừa lớp con người, không thể cho tạo đối tượng từ lớp con người được.

Để tạo lớp trừu tượng ta dùng từ khóa `abstract` trước từ khóa `class`. Ta sẽ dùng lớp `Person` từ những bài trước đó, biến nó thành lớp `abstract`:

```java
package entity;

public abstract class Person {

    private String rollNumber;
    private String name;
    private boolean gender;
    private String dob;
    private String email;
    private String mobile;
    private String address;

    // getter & setter
    
    // display
    
    // input
}
```

<br />

##  

© Copyright
> ANEST LEARNING  
> Join us: &nbsp;&nbsp;&nbsp; [Facebook groups](https://www.facebook.com/groups/anest.learning/)  
> Website: &nbsp; [https://anest.dev](https://anest.dev) 
