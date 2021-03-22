# Java I/O: OutputStream với InputStream

<br />

**Java I/O hay Input/Output** trong java được sử dụng để xử lý đầu vào và đầu ra trong java.

Java sử dụng khái niệm stream để làm cho hoạt động I/O nhanh hơn. Gói **java.io** chứa tất cả các lớp cần thiết cho hoạt động input và output.

### Khái niệm về stream

Một stream là một dãy dữ liệu. Trong java, một stream bao gồm các byte. Nó được gọi là stream (dòng chảy) vì nó giống như một dòng nước chảy liên tục.

Trong java, 3 stream được tạo cho chúng ta một cách tự động. Tất cả các stream này được gắn với console.

- `System.out`: output stream tiêu chuẩn
- `System.in`: input stream tiêu chuẩn
- `System.err`: error stream tiêu chuẩn

<br />

## I. OutputStream

Ứng dụng Java sử dụng một output stream để ghi dữ liệu đến đích, nó có thể là một tệp tin, một mảng, thiết bị ngoại vi hoặc socket.

Lớp OutputStream là một lớp trừu tượng. Nó là super class của tất cả các lớp đại diện cho một output stream của các byte. Một output stream chấp nhận ouput các byte và gửi chúng đến một nơi có thể chứa.

### Các phương thức của lớp OutputStream

| No | Method | Description |
| -- | ------ | ----------- |
|  1 | public void write(int) throws IOException | Được sử dụng để ghi một byte đến output stream hiện tại. |
|  2 | public void write(byte[]) throws IOException | Được sử dụng để ghi một mảng các byte đến output stream hiện tại. |
|  3 | public void flush() throws IOException | Flush output stream hiện tại. |
|  4 | public void close() throws IOException | Được sử dụng để đóng output stream hiện tại. |

<br />

Ví dụ ghi một Object data vào một file:

```java
public static boolean writeObject(Object data, String path) {

    File file = new File(path);
    if (!file.exists()) {
        try {
            file.createNewFile();
        } catch (IOException ex) {
            ex.printStackTrace(System.out);
        }
    }

    try (FileOutputStream fos = new FileOutputStream(path);
            ObjectOutputStream oos = new ObjectOutputStream(fos)) {
        oos.writeObject(data);
        return true;
    } catch (IOException ex) {
        ex.printStackTrace(System.err);
    }
    return false;
}
```

<br />

## II. InputStream

Ứng dụng Java sử dụng một input stream để đọc dữ liệu từ một nguồn, nó có thể là một tệp tin, một mảng, thiết bị ngoại vi hoặc socket.

Lớp InputStream là một lớp trừu tượng. Nó là super class của tất cả các lớp đại diện cho một input stream của các byte.

### Các phương thức của lớp InputStream

| No | Method | Description |
| -- | ------ | ----------- |
|  1 | public abstract int read() throws IOException | Đọc byte kế tiếp của dữ liệu từ input stream. Nó trả về -1 khi đọc đến vị trí cuối tập tin. |
|  2 | public int available() throws IOException | Trả về một ước tính về số byte có thể đọc được từ input stream hiện tại. |
|  3 | public void close() throws IOException | Được sử dụng để đóng input stream hiện tại. |

<br />

Ví dụ đọc data từ một file:

```java
public static Object readObject(String path) {

    try (FileInputStream fis = new FileInputStream(path);
            ObjectInputStream ois = new ObjectInputStream(fis)) {
        Object data = ois.readObject();
        return data;
    } catch (IOException | ClassNotFoundException ex) {
        ex.printStackTrace(System.err);
    }
    return null;
}
```

<br />

##  

© Copyright
> ANEST LEARNING  
> Join us: &nbsp;&nbsp;&nbsp; [Facebook groups](https://www.facebook.com/groups/anest.learning/)  
> Website: &nbsp; [https://anest.dev](https://anest.dev) 
