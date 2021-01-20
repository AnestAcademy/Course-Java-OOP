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

Ví dụ trong dự án đang thực hiện của chúng ta, những lớp **Student**, **Staff**... có những thuộc tính và phương thức chung như tên, năm sinh, quê quán... thì ta sẽ tạo một lớp **Person** là lớp chứa những đặc điểm chung đó và cho lớp **Student**, **Staff** kế thừa lớp **Person**. Nhưng trong thực tế chúng ta sẽ không bao giờ cần tạo đối tượng từ lớp **Person** (`new Person()`) vì các đối tượng làm việc chính trong dự án là **Student** và **Staff**. Vì vậy khi phát triển chương trình, ta chỉ cần tạo các đối tượng từ lớp con kế thừa và không cho tạo đối tượng từ lớp **Person** bằng cách biến nó thành lớp trừu tượng.

Để tạo lớp trừu tượng ta dùng từ khóa `abstract` trước từ khóa **class**. Ta sẽ dùng lớp **Person** từ những bài trước đó, biến nó thành lớp `abstract`:

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

### Một số đặc điểm của abstract class:

- Lớp trừu tượng có thể có các method abstract hoặc non-abtract.
- Lớp trừu tượng có thể khai báo 0, 1 hoặc nhiều abstract method bên trong.
- Không thể khởi tạo 1 đối tượng trực tiếp từ một abstract class.
- Một lớp kế thừa từ một abstract class (subclass – lớp con) không cần phải implement non-abstract methods, nhưng bắt buộc phải override những abstract methods. Trừ khi subclass cũng là abstract class.

Ví dụ nếu chúng ta khởi tạo instance từ class **Person** thì sẽ báo lỗi:

```java
public class Main {

    public static void main(String[] args) {

        Person person = new Person();  // error
    }
}
```

<br />

## II. Abstract method (Phương thức trừu tượng)

**Các phương thức trừu tượng** là chỉ định nghĩa mà không có chương trình bên trong, lớp con kế thừa phải bắt buộc override nó lại để sử dụng. Phương thức trừu tượng có ý nghĩa định nghĩa phương thức bắt buộc phải có trong lớp con kế thừa.

<br />

##  

© Copyright
> ANEST LEARNING  
> Join us: &nbsp;&nbsp;&nbsp; [Facebook groups](https://www.facebook.com/groups/anest.learning/)  
> Website: &nbsp; [https://anest.dev](https://anest.dev) 
