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

<img width="274" alt="Screen Shot 2020-12-08 at 7 29 58 PM" src="https://user-images.githubusercontent.com/54991791/101484458-402fa100-398c-11eb-9166-bb27a29aa5cf.png">

class JUnitLifeCycleTest {

    companion object{
        @BeforeClass @JvmStatic
        fun runOnceBeforeClass() {
            println("@BeforeClass - runOnceBeforeClass")
        }

        @AfterClass @JvmStatic
        fun runOnceAfterClass() {
            println("@AfterClass - runOnceAfterClass")
        }
    }


    @Before
    fun runBeforeTestMethod() {
        println("@Before - runBeforeTestMethod")
    }

    @After
    fun runAfterTestMethod() {
        println("@After - runAfterTestMethod")
    }

    @Test
    fun test_method_1() {
        println("@Test - test_method_1")
    }

    @Test
    fun test_method_2() {
        println("@Test - test_method_2")
    }
}

### Ví dụ @Ignore a Test

Vì một lý do nào đó, chúng ta muốn tạm thời vô hiệu hóa test case (bỏ qua/ không chạy test case đó).

Thông thường ta sẽ xóa hoặc comment annotation @Test, như thế trình test runner sẽ bỏ qua method đó nhưng đồng thời test case đó cũng sẽ không được report, chúng ta có thể quên mất là có test case đó.

 
Biện pháp thay thế là sử dụng annotation @Ignore ở trước hoặc sau annotation @Test, sau khi chạy JUnit test, nó vẫn thông báo là có test case đó nhưng đang bị disable.

    @Test
    @Ignore("This test case will be ignored")
    fun testEquals() {
        val expected = "DAT"
        Assert.assertEquals(expected, "DAT")
    }

    @Test
    fun testTrue() {
        Assert.assertTrue(true)
    }

    @Test
    fun testFalse() {
        Assert.assertFalse(false)
    }

### Ví dụ Timeout Test

Chúng ta có thể expect thời gian timeout của một test case bằng cách sử dụng thuộc tính timeout trong annoation @Test.

  object TaskUtils {
 
    fun doNormalTask() : Int{
        try {
            TimeUnit.SECONDS.sleep(3)
        } catch (e: InterruptedException) {
            e.printStackTrace()
        }
        return 1
    }

    fun doHeavyTask() : Int{
        try {
            TimeUnit.SECONDS.sleep(5)
        } catch (e: InterruptedException) {
            e.printStackTrace()
        }
        return 1
    }
 }
 
  Mong muốn thời gian thực thi mỗi phương thức tối đa là 3 giây. Nếu sau thời gian đó, thì xem như phương thức test bị failed. 
  
    @Test(timeout = 3100)
    fun testTimeout1() {
        val expected = 1
        val actual = doNormalTask()
        Assert.assertEquals(expected.toLong(), actual.toLong())
    }

    @Test(timeout = 3000)
    fun testTimeout2() {
        val expected = 1
        val actual = doHeavyTask()
        Assert.assertEquals(expected.toLong(), actual.toLong())
    }
 
### Ví dụ Expected Exceptions Test

object MathUtil {

    fun sum(a:Int):Int{
        if(a == 0){
            throw IllegalArgumentException("Fail")
        }
        return 1
    }
}

Trong một số trường hợp chúng ta cần viết unit test ứng với trường hợp xảy ra exception thì chúng ta expect kết quả là test case đó sẽ xảy ra một Exception chứ không phải một giá trị cụ thể

    @Test(expected = IllegalArgumentException::class)
    @Throws(Exception::class)
    fun testDivideByZero() {
        MathUtil.sum(0)
    }
    

### Ví dụ @FixMethodOrder Test

Các phương thức test trong một class nên được viết một cách độc lập, không phụ thuộc lẫn nhau nên thứ tự thực thi một lớp không quan trọng. Tuy nhiên, chúng ta có thể xác định thứ tự thực thi của các method trong class test bằng cách dùng annotation @FixMethodOrder ở mức class. Có 3 kiểu sắp xếp là:

@FixMethodOrder(MethodSorters.DEFAULT): Đây là kiểu sắp xếp mặc định nếu không khai báo @FixMethodOrder

@FixMethodOrder(MethodSorters.JVM): Thứ tự các method test dựa theo JVM. Tuy nhiên thứ tự này có thể bị thay đổi khi thực thi.

@FixMethodOrder(MethodSorters.NAME_ASCENDING): Thứ tự các method được thực thi dựa theo tên method. Thông thường, nếu cần sắp xếp thì kiểu này được chọn bởi nó giữ đúng thứ tự theo tên phương thức, không bị thay đổi như 2 kiểu trên.

@FixMethodOrder(MethodSorters.NAME_ASCENDING)
class FixMethodOrderTest {

    @Test
    fun test_11() {
        Assert.assertTrue(true)
    }

    @Test
    fun test_1() {
        Assert.assertTrue(true)
    }

    @Test
    fun test_10() {
        Assert.assertTrue(true)
    }

    @Test
    fun test_2() {
        Assert.assertTrue(true)
    }
}

### Test database

@Entity(tableName = "shopping_items")
data class ShoppingItem(
    var name: String,
    var amount: Int,
    var price: Float,
    var imageUrl: String,
    @PrimaryKey(autoGenerate = true)
    val id: Int? = null
)


@Dao
interface ShoppingDao {
    @Insert(onConflict = OnConflictStrategy.REPLACE)
    suspend fun insertShoppingItem(shoppingItem: ShoppingItem)
    
     @Query("SELECT * FROM shopping_items")
    fun getAllShoppingItems(): List<ShoppingItem>
}


@Database(
    entities = [ShoppingItem::class],
    version = 1
)
abstract class ShoppingItemDatabase : RoomDatabase() {

    abstract fun shoppingDao(): ShoppingDao
}

@ExperimentalCoroutinesApi
@RunWith(AndroidJUnit4::class)
@SmallTest
class ShoppingDaoTest {


    @Rule
    @JvmField
    var instan  = InstantTaskExecutorRule()
    private lateinit var database: ShoppingItemDatabase
    private lateinit var dao: ShoppingDao

    @Before
    fun setup(){
        database = Room.inMemoryDatabaseBuilder(
            ApplicationProvider.getApplicationContext(),
            ShoppingItemDatabase::class.java
        ).allowMainThreadQueries().build()
        dao = database.shoppingDao()
    }

    @After
    fun teardown(){
        database.close()
    }

    @Test
    fun insertShoppingItem() = runBlockingTest {
        val shoppingItem = ShoppingItem("name",1,1f,"url",1)
        dao.insertShoppingItem(shoppingItem)

        val allShoppingItems = dao.getAllShoppingItems()
        assertEquals(shoppingItem,allShoppingItems.get(0))

    }

}
