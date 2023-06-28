### API 
    1. API là gì?
        - Application Programming Interface
        - Cho phép các ứng dụng khác kết nối và tương tác với dịch vụ web, hệ thống cơ sở dữ liệu (database), máy chủ (server) và các nền tảng khác
    2. API thể hiện dưới 2 dạng: XML và JSON ( JSON được sử dụng nhiều hơn)
    3. Ưu và nhược điểm:
        - Ưu điểm: Kết nối mọi lúc nhờ vào internet
        - API luồng dữ liệu 2 chiều nên đáng tin cậy
        - Cung cấp trải nghiệm thân thiện
        - Mã nguôn mở
        - Nhược điểm: 
          - Tốn nhiều chi phí phát triẻn, vận hành, chỉnh sửa
          - Đòi hỏi kiến thức chuyên sâu
          - Khi hệ thống bị tấn công, có thể gặp vấn đề bảo mật
    4. HTTP ( Hypertext Transfer Protocol): giao thức truyền tải siêu văn bản != HTML (Hypertext Markup Language) Ngôn ngữ đánh dấu siêu văn bản
            - HTTP cho phép lấy về các tài nguyên như HTML, text, video, hình ảnh...
            - HTTP là nền tảng để trao đổi dữ liệu cho các ứng dụng web vs mô hình Client/ Server
    5. HTTP có 2 phần request và response ( Client gửi request, server gửi lại response)
            - Request: 
                - URL: địa chỉ duy nhất có thể là webpage, image, video ("https://jsonplaceholder.typicode.com/posts")
                - Method: GET, POST, PUT, DELETE (hành động client muốn tác động lên resource)
                - Headers: nơi chứa thông tin cần thiết của 1 request
                - Body: nơi chứa thông tin mà client sẽ điền
              - Response:
                - Status code: 200 (success), 201 (created), 300-399 (redirection message), 400-499 (client error response), 500-599 (server error response)
                - Headers
                - Body
    6. Fetch API
            - Fetch API giúp việc nhận và gửi request đơn giản hơn
            - Tham số đầu vào của phương thức fetch() là API URL, trả về 1 Promise

### Đồng bộ: 
// function synchronous() {
//     console.log(1);
//     console.log(2);
//     console.log(3);
// }
// synchronous()

//ưu điểm: khi chạy lần lượt, dễ kiểm soát hơn, còn khi có lỗi,
// chương trình dừng lại không chạy tiếp nữa
//hạn chế: đôi khi lấy dữ liệu từ bên ngoài (đọc file, lấy data từ DB), cần thời gian
//nếu thực hiện đồng bộ, tổng thời gian của chương trình sẽ = tổng thời gian thực hiện từng câu lệnh 

### Asynchronous:
//quá trình mà các câu lệnh có thể chạy cùng 1 lúc chứ ko cần chờ câu lệnh trước
//nếu câu lệnh sau thưc hiện nhanh hơn, sẽ trả về kết quả sớm hơn câu lệnh trước

// function async() {
//     setTimeout(() => {
//         console.log(1)
//     }, 2000)
//     console.log(2)
//     console.log(3)
// }
// async()

### callback:
//1.function 2.truyền vào function khác dưới dạng đối số 3.được gọi lại
// function userName() {
//     console.log("Nguyen van A")
// }
// function demoCallback(callback) {
//     setTimeout(() => {
//         callback()
//     }, 1000)
//     console.log("Nguyen van B")
// }
// demoCallback(userName)

### Callbackhell : callback lồng nhau quá nhiều, code khó đọc, dễ bug, khó phát triển
// function getData(link, callback) {
//     setTimeout(() => {
//         callback()
//     }, 1000)
// }
// getData("Data1", () => {
//     getData("Data2", () => {
//         getData("Data3", () => {
//             getData("Data4", () => {
//                 console.log("DONE")
//             })
//         })
//     })
// })

### TRong Javascript, bất đồng bộ có 2 loại chính:
// Browser API/ Web API
// setTimeout(), setInterval()
// click, scroll..., events

//để giải quyết bất đồng bộ có những cách sau:
//Promise
//Callback
//Async/Await

### Promise: là 1 hàm callback gồm 2 tham số như sau:
//resolve: function sẽ được gọi nếu Promise chạy thành công
//reject: function sẽ được gọi nếu Promise xảy ra lỗi
// Promise cung cấp 2 phương thức xử lý sau khi thực hiện:
//then() dùng để xử lý khi Promise thực hiện thành công (khi resolve được gọi)
//catch() dùng để xử lý khi Promise thực hiện thất bại (khi reject được gọi)

// let promise = new Promise((resolve, reject) => {
//     resolve('Success')
//     reject('Error')
// })
// promise.then((value) => {
//     console.log(value)
// })
// .then(() => {
//     console.log('Finished')
// })
// .catch(err => {
//     console.log(err)
// })

//Async/Await: 1 tính năng của Javascript giúp ta làm việc với hàm bất đồng bộ
//Async/Await: được xây dưng trên Promise
//Async: khai báo 1 hàm bất đồng bộ (async function funcName(){...})
//Async tự đông biến 1 hàm thông thường thành 1 Promise
//Khi gọi tới hàm async nó sẽ xử lý moi thứ và trả về kết quả trong hàm của nó
//Async cho phép sử dụng Await

//Await : tạm dừng việc thực hiện các hàm async
//Khi đặt trước 1 promise, nó sẽ đợi cho đến khi Promise kết thúc và trả về kết quả
//Await chỉ làm việc với promise, nó ko hoạt động với callback
//Await chỉ được sử dụng bên trong function async


