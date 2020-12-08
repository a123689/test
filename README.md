# Kiểm thử đơn vị

Kiểm thử dòng điều khiển

• Dựa trên khái niệm đồ thị dòng điều khiển (control flow graph)

• Đồ thị dòng điều khiển là một đồ thị có hướng gồm:

– Các đỉnh tương ứng với các câu lệnh /nhóm câu lệnh

– Các cạnh là các dòng điều khiển giữa các câu lệnh /nhóm câu lệnh

<img width="854" alt="Screen Shot 2020-12-07 at 2 05 12 PM" src="https://user-images.githubusercontent.com/54991791/101319869-42630400-3895-11eb-892f-65f8da39c6a9.png">

### Các độ đo kiểm thử

• Độ đo kiểm thử là mức độ bao phủ của một bộ kiểm thử (tập
các ca kiểm thử) được đo bằng tỷ lệ các thành phần thực sự
được kiểm thử so với tổng số ca cần kiểm thử.

• Các thành phần kiểm thử có thể là các câu lệnh, các điểm quyết
định, các điều kiện con, các đường thi hành hay sự kết hợp giữa
chúng.

• Độ bao phủ càng lớn thì độ tin cậy của bộ kiểm thử càng cao.

• Mục tiêu: kiểm thử với số ca tối thiểu nhưng độ bao phủ tối đa.

### Độ đo kiểm thử cấp 1 - độ đo C1

• Mỗi câu lệnh được thực hiện ít nhất một lần sau khi chạy các ca kiểm thử.

• Như ví dụ trên, cần 2 ca kiểm thử để đạt 100% độ bao phủ cho độ đo C1

<img width="569" alt="Screen Shot 2020-12-07 at 2 10 41 PM" src="https://user-images.githubusercontent.com/54991791/101320318-201db600-3896-11eb-8c64-ba75133a42e5.png">

### Độ đo kiểm thử cấp 2 - độ đo C2
• Các điểm quyết định trong đồ thị dòng điều khiển của đơn vị kiểm thử đều được thực hiện ít nhất một lần cả hai nhánh đúng và sai.

<img width="872" alt="Screen Shot 2020-12-07 at 2 22 45 PM" src="https://user-images.githubusercontent.com/54991791/101321302-ba322e00-3897-11eb-8d90-a2eab09c7308.png">

Các ca kiểm thử tương ứng của độ đo C2 ứng với hàm foo ở trên là:

<img width="870" alt="Screen Shot 2020-12-07 at 2 25 14 PM" src="https://user-images.githubusercontent.com/54991791/101321516-0e3d1280-3898-11eb-8768-893a75e9c04c.png">

### Độ đo kiểm thử cấp 3 - độ đo C3
• Các điều kiện con thuộc các điều kiện phức tạp tương ứng với các điểm quyết định trong đồ thị dòng điều khiển đều được thực hiện ít nhất một lần cả hai nhánh đúng và sai.

<img width="871" alt="Screen Shot 2020-12-07 at 2 27 48 PM" src="https://user-images.githubusercontent.com/54991791/101321800-899ec400-3898-11eb-8031-2be9cab4a95a.png">

Các ca kiểm thử tương ứng của độ đo C3 ứng với hàm foo ở trên là:
<img width="633" alt="Screen Shot 2020-12-07 at 2 30 36 PM" src="https://user-images.githubusercontent.com/54991791/101321986-d71b3100-3898-11eb-92fb-31fb9dd5af38.png">

### Các phương thức Assert()

assertEquals(): So sánh 2 giá trị để kiểm tra bằng nhau. Test sẽ được chấp nhận nếu các giá trị bằng nhau.

assertFalse(): Đánh giá biểu thức luận lý. Test sẽ được chấp nhận nếu biểu thức sai.

assertNotNull(): So sánh tham chiếu của một đối tượng với null. Test sẽ được chấp nhận nếu tham chiếu đối tượng khác null.

assertNotSame(): So sánh địa chỉ vùng nhớ của 2 tham chiếu đối tượng bằng cách sử dụng toán tử ==. Test sẽ được chấp nhận nếu cả 2 đều tham chiếu đến các đối tượng khác nhau

assertNull(): So sánh tham chiếu của một đối tượng với giá trị null. Test sẽ được chấp nhận nếu tham chiếu là null.

assertSame(): So sánh địa chỉ vùng nhớ của 2 tham chiếu đối tượng bằng cách sử dụng toán tử ==. Test sẽ được chấp nhận nếu cả 2 đều tham chiếu đến cùng một đối tượng.

assertTrue(): Đánh giá một biểu thức luận lý. Test sẽ được chấp nhận nếu biểu thức đúng fail(): Phương thức này làm cho test hiện hành thất bại, phương thức này thường được sử dụng khi xử lý các biệt lệ.

### Viết Unit Test



  object SampleTest {
  
    fun foo(a:Int,b:Int,c:Int,d:Int): Int{
        var e: Int = 0
        if(a == 0) return 0
        var x = 0
        if((a==b) ||(a==d)){
            x = 1
        }
        try {
            e = 1/x
        }catch (e:Exception){

        }

        return  e

    }
 }
 
 class SampleTestTest{
 
    @Test
    fun testCase1Result0(){
        val result = SampleTest.foo(0,1,2,3)
        assertEquals(0,result)
    }

    @Test
    fun testCase2Result1(){
        val result = SampleTest.foo(1,1,2,3)
        assertEquals(1,result)
    }

    @Test
    fun testCase3Result(){
        val result = SampleTest.foo(1,2,1,2)

    }

    @Test
    fun testCase4Result(){
        val result = SampleTest.foo(1,2,1,1)
        assertEquals(1,result)
    }

}

## Một số Annotation cơ bản của JUnit

JUnit cung cấp một số Annotation để viết Test như sau:

### @Before
Phương thực được đánh dấu với Annotation này sẽ được gọi trước mỗi khi phương thức @Test được gọi.

Nó thường được sử dụng để khởi tạo dữ liệu trước khi thực thi một phương thức @Test.

### @After
Phương thực được đánh dấu với Annotation này sẽ được gọi sau mỗi khi phương thức @Test được gọi.

Nó thường được sử dụng để dọn dẹp bộ nhớ sau khi thực thi một phương thức @Test.

### @BeforeClass
Phương thực được đánh dấu với Annotation này sẽ được gọi trước khi thực thi tất cả các phương thức @Test được gọi trong một Test class. Phương thức này chỉ được gọi một lần duy nhất.

Phương thức đánh dấu Annotation này phải là static.


 
Nó thường được sử dụng để khởi tạo dữ liệu cho việc thực thi một Test class.

### @AfterClass
Tương tự như @BeforeClass, nhưng nó được gọi sau khi kết thúc thực thi các phương thức @Test. Phương thức này chỉ được gọi một lần duy nhất.

Phương thức đánh dấu Annotation này phải là static.

Nó thường được sử dụng để dọn dẹp bộ nhớ sau khi thực thi tất cả các phương thức @Test trong một Test class.

### @Test
Được sử dụng để đánh dấu đây là một phương thức test.@Test(timeout=500)Được sử dụng khi cần giới hạn thời gian thực thi của một phương thức. Nếu vượt quá thời này thì phương thức sẽ fail.

### @Test(expected=XxxException.class)
Được sử dụng khi cần test một ngoại lệ được throw ra từ phương thức được test. Nếu ngoại lệ không được throw thì phương thức sẽ fail.

### @Ignore
Được sử dụng để đánh dấu phương thức này để được bỏ qua (ignore/ disable), không cần thực thi test.

Nó có thể sử dụng cho một phương thức test hay một class từ một test suite.

### @FixMethodOrder
Annotation này cho phép user có thể chọn thứ tự thực thi các phương thức @Test trong một test class.


## Lifecycle của một Test Class trong JUnit

Trong ví dụ bên dưới, chúng ta sẽ thấy được cách mà một Unit test được thi thi với JUnit
