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
