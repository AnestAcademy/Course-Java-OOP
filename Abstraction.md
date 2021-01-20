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

### 1. Một số đặc điểm của abstract class:

- Lớp trừu tượng có thể có các method abstract hoặc non-abtract.
- Lớp trừu tượng có thể khai báo 0, 1 hoặc nhiều abstract method bên trong.
- Không thể khởi tạo 1 đối tượng trực tiếp từ một abstract class.
- Một lớp kế thừa từ một abstract class (subclass – lớp con) không cần phải implement non-abstract methods, nhưng bắt buộc phải override những abstract methods. Trừ khi subclass cũng là abstract class.

<br />

Ví dụ nếu chúng ta khởi tạo instance từ class **Person** thì sẽ báo lỗi:

```java
public class Main {

    public static void main(String[] args) {

        Person person = new Person();  // error
    }
}
```

<br />

### 2. Abstract method (Phương thức trừu tượng)

Một phương thức được khai báo là abstract được gọi là phương thức trừu tượng (abstract method).

Các phương thức trừu tượng chỉ được định nghĩa mà không có chương trình bên trong (không có code bên trong hàm), lớp con kế thừa bắt buộc phải **override** nó lại để sử dụng. Phương thức trừu tượng có ý nghĩa định nghĩa phương thức bắt buộc phải có trong lớp con kế thừa vì khi kế thừa lớp con bắt buộc phải **override** lại phương thức đó.

Ví dụ: 
```java
public abstract void display();
```

<br />

### 3. Ví dụ về Abstract class và Abstract method

Ví dụ: Viết chương trình vẽ một hình bất kỳ sao cho cách sử dụng - vẽ là giống nhau, bất kể đó là hình gì với màu đỏ. Hình đó có thể là hình chữ nhật (rectangle), hình tròn (circle), tam giác (triangle)...

Với yêu cầu trên, chúng ta sẽ tạo một lớp trừu tượng **Shape**. Lớp này cung cấp một phương thức trừu tượng `draw()`, phương thức này để đảm bảo rằng:
- Vì mỗi hình sẽ có cách vẽ cụ thể riêng nên chúng ta sẽ chỉ cần định nghĩa phương thức `draw()` mà chưa cần triển khai vẽ như thế nào => `draw()` sẽ là abstract method
- Tất cả các hình đều có cùng cách sử dụng (draw) vì các class con sẽ kế thừa class **Shape**, nên cũng sẽ kế thừa method `draw()`

**Shape.java**
```java
public abstract class Shape {

    public Shape() {         
    }
     
    public abstract void draw();
}
```

<br />

Ngoài ra, chúng ta cũng cần có phương thức không trừu tượng `getColor()` để cung cấp màu sử dụng chung cho tất cả các hình (vì yêu cầu tất cả cách hình có màu đỏ nên method này có thể triển khai luôn được code). 

**Shape.java**
```java
public abstract class Shape {

    private String color = "red";
     
    public Shape() {         
    }
    
    public abstract void draw();
     
    public String getColor() {
        return color;
    }
}
```

<br />

Tiếp theo, chúng ta tạo 2 lớp **Rectangle** và **Circle** kế thừa từ lớp **Shape**, 2 lớp này sẽ có những cách xử lý `draw()` khác nhau cụ thể để có thể vẽ ra cho đúng hình. 

**Rectangle.java**
```java
public class Rectangle extends Shape {
 
    @Override
    public void draw() {
        System.out.println("Draw " + super.getColor() + " rectangle");
    }
}
```

**Circle.java**
```java
public class Circle extends Shape {
 
    @Override
    public void draw() {
        System.out.println("Draw " + super.getColor() + " circle");
    } 
}
```

<br />

Cuối cùng, chúng ta tạo class **ShapeApp**, gọi phương thức `draw()` để vẽ hình theo yêu cầu.

**ShapeApp.java**
```java
public class ShapeApp {

    public static void main(String[] args) {
        Shape rect = new Rectangle();
        rect.draw();
        System.out.println("---");
        Shape circle = new Circle();
        circle.draw();      
    }
}
```

Kết quả nhận được:
```java
Draw red rectangle
---
Draw red circle
```

<br />

## II. Interface

Trong Java, Interface (giao diện) là một kiểu dữ liệu tham chiếu tương tự như Class (lớp) nhưng chỉ có thể chứa hằng số và tên các abstract methods (phương thức trừu tượng).

Một lớp mô tả các thuộc tính và hành vi của một đối tượng. Một interface chứa các hành vi mà một class triển khai.

### 1. Đặc điểm của Interface

- Interface là một kỹ thuật để thu được tính trừu tượng hoàn toàn và **đa kế thừa** trong Java.
- Interface luôn luôn có modifier là: **_public interface_**, cho dù bạn có khai báo rõ hay không.
- Nếu có các trường (field) thì chúng đều là: **_public static final_**, cho dù bạn có khai báo rõ hay không.
- Các phương thức trong interface đều là abstract methods (phương thức trừu tượng), nghĩa là không có thân hàm, và đều có modifier là: **_public abstract_**, cho dù bạn có khai báo rõ hay không.
- Interface không có hàm khởi tạo (constructor).
- Trừ khi một lớp triển khai interface là lớp trừu tượng abstract, còn lại tất cả các phương thức của interface bắt buộc phải **override** trong class triển khai (implements) nó.

<br />

> Java Compiler thêm từ khóa public abstract trước phương thức của interface và các từ khóa public static final trước các thành viên dữ liệu.

<br />

### 2. Một interface tương tự với một class bởi những điểm sau đây:

- Một interface được viết trong một file với định dạng `.java`, với tên của interface giống tên của file.
- Bytecode của interface được lưu trong file có định dạng `.class`.
- Khai báo interface trong một **package**, những file bytecode tương ứng cũng có cấu trúc thư mục có cùng tên package.

<br />

### 3. Một interface khác với một class ở một số điểm sau đây:

- Bạn không thể khởi tạo một interface.
- Một interface không chứa bất cứ hàm Contructor nào.
- Tất cả các phương thức của interface đều là abstract.
- Một interface không thể chứa một trường (field) nào trừ các trường **_static final_**.
- Một interface không thể kế thừa từ lớp, nó được triển khai (implements) bởi một lớp.
- Một interface có thể kế thừa từ nhiều interface khác.

<br />

### 4. Ví dụ sử dụng Interface

Tương tự như yêu cầu ở ví dụ về sử dụng abstract class ở trên, nhưng chúng ta sẽ dụng Interface để áp dụng vào chương trình.

Vì các đặc điểm của Interface nên giờ đây chúng ta chỉ cần viết lại ngắn gọn như sau:

**Shape.java**
```java
public interface Shape {
     
    String color = "red";
     
    void draw();     
}
```

<br />

Vì dùng Interface nên chúng ta sẽ kế thừa bằng từ khóa **implements** (triển khai), không dùng từ khóa **extends**.

**Rectangle.java**
```java
public class Rectangle implements Shape {
 
    @Override
    public void draw() {
        System.out.println("Draw " + color + " rectangle");
    }   
}
```

**Circle.java**
```java
public class Circle implements Shape {
 
    @Override
    public void draw() {
        System.out.println("Draw " + color + " circle");
    }    
}
```

<br />

Class **ShapeApp** chúng ta không thay đổi gì:

**ShapeApp.java**
```java
public class ShapeApp {

    public static void main(String[] args) {
        Shape rect = new Rectangle();
        rect.draw();
        System.out.println("---");
        Shape circle = new Circle();
        circle.draw();      
    }
}
```

Kết quả nhận được:
```java
Draw red rectangle
---
Draw red circle
```

<br />

### 5. Khi triển khai interface, có vài quy tắc sau:

- Một lớp có thể triển khai một hoặc nhiều interface tại một thời điểm.
- Một lớp chỉ có thể kế thừa một lớp khác, nhưng được triển khai nhiều interface.
- Một interface có thể kế thừa từ một interface khác, tương tự cách một lớp có thể kế thừa lớp khác.

<br />

## III. So sánh abstract class và interface trong Java

<br />

| No | Lớp trừu tượng (abstract class) | Interface |
| :-: | --- | --- |
| 1 | Thể hiện tính trừu tượng < 100%. |	Thể hiện tính trừu tượng 100% (Java < 8). |
| 2 | Lớp trừu tượng có thể có các phương thức **_abstract_** và **_non-abstract_** | Phiên bản Java < 8, Interface chỉ có thể có phương thức **_abstract_**. <br />Phiên bản Java 8, có thể thêm **_default_** và **_static methods_**. <br />Phiên bản Java 9, có thể thêm **_private methods_**. |
| 3 | Lớp trừu tượng **_không_** hỗ trợ đa kế thừa. | Interface **_hỗ trợ_** đa kế thừa. |
| 4 | Lớp trừu tượng có thể có các biến **_final_**, **_non-final_**, **_static_** và **_non-static_**. | Interface chỉ có các biến **_static final_**. |
| 5 | Lớp trừu tượng có thể có phương thức **_static_**, phương thức **_main_** và **_constructor_**. | Interface không thể có phương thức **_static_**, **_main_** hoặc **_constructor_**. |
| 6 | Từ khóa abstract được sử dụng để khai báo lớp trừu tượng. | Từ khóa interface được sử dụng để khai báo Interface. |
| 7 | Lớp trừu tượng có thể cung cấp trình triển khai của Interface | Interface không cung cấp trình triển khai cụ thể của lớp abstract. |
| 8 | Sử dụng Abstract class khi chúng ta chỉ có thể hoàn thành một vài chức năng (method/function) chuẩn của hệ thống, một vài chức năng còn lại các lớp con **extends** sẽ phải hoàn thành. Những tính năng đã hoàn thành này vẫn sử dụng như bình thường, đây là những tính năng chung. | Sử dụng Interface khi bạn muốn tạo dựng một bộ khung chuẩn gồm các chức năng (method/function) mà tất cả module/project cần phải có. Các module phải **implements** tất cả chức năng đã được định nghĩa. |

<br />

Nói về Abtract Class và Interface, đôi khi bạn sẽ gặp một số cách gọi:
- Khi một class extend một class/abtract class thì có nghĩa là ta đang thể hiện mối quan hệ **is-a** (là)
- Khi implement một interface, thì ta đang thể hiện mối quan hệ **has-a** (có, hay thực hiện).

```java
// Programmer là Person, thực hiện việc Programming, Debugging
 
class Programmer extends Person implements Programming, Debugging {}
```

<br />

##  

© Copyright
> ANEST LEARNING  
> Join us: &nbsp;&nbsp;&nbsp; [Facebook groups](https://www.facebook.com/groups/anest.learning/)  
> Website: &nbsp; [https://anest.dev](https://anest.dev) 
