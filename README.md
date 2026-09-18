# PHẦN 2 — COMPONENT VÀ ĐIỀU HƯỚNG CƠ BẢN

## Trang 13 – XÂY DỰNG CÁC COMPONENT

“Đầu tiên, chúng ta cần hiểu **Component là gì**.

Trong React, Component có thể hiểu là một khối giao diện độc lập. Mỗi component có thể được tái sử dụng và kết hợp với các component khác để tạo thành một ứng dụng hoàn chỉnh.

Trong ví dụ của nhóm em, mỗi màn hình được xây dựng thành một component riêng.

Ví dụ:

- `Home` đại diện cho trang chủ
- `About` đại diện cho trang giới thiệu
- `NoMatch` đại diện cho trang 404

Sau khi có các component này, React Router sẽ liên kết từng URL với component tương ứng.

Nhìn vào sơ đồ bên phải, khi URL là `/` thì React Router đưa người dùng tới `Home`; `/about` thì hiển thị `About`; còn nếu URL không khớp với route đã định nghĩa thì sẽ hiển thị `NoMatch`.

Như vậy, có thể hiểu đơn giản là: **Component tạo ra giao diện, còn React Router quyết định giao diện nào sẽ được hiển thị dựa trên URL.**”

---

## Trang 14 – Functional Component và URL – Route – Component

“Tiếp theo chúng ta đi sâu hơn một chút vào **Functional Component**.

Functional Component là một component được viết dưới dạng một hàm JavaScript và trả về giao diện JSX.

Ví dụ ở bên trái, chúng ta có hàm `Home()`. Hàm này trả về một thẻ `h2` với nội dung `Home View`, vì vậy khi component `Home` được render thì giao diện tương ứng sẽ xuất hiện.

Tóm lại, **Functional Component chịu trách nhiệm tạo giao diện, còn React Router chịu trách nhiệm kết nối URL với đúng Component.**”

---

## Trang 15 – Xây dựng Home và About

“Sau khi hiểu phần lý thuyết, chúng ta bắt đầu xây dựng các component cụ thể.

Đầu tiên, chúng ta import `BrowserRouter`, `Routes` và `Route` từ thư viện `react-router-dom`.

Tiếp theo là hai component `Home` và `About`.

Component `Home` trả về một vùng giao diện có tiêu đề `Home View`.

Tương tự, component `About` trả về giao diện có tiêu đề `About View`.

Điểm cần chú ý ở đây là mỗi trang được tách thành một component riêng. Nhờ vậy, sau này khi cấu hình routing, chúng ta chỉ cần chỉ định URL nào tương ứng với component nào.”

---

## Trang 16 – NoMatch và cấu hình Route

“Tiếp theo là component `NoMatch`.

Component này dùng để hiển thị trang **404 – Page Not Found** khi người dùng truy cập vào một URL không tồn tại.

Ở phía dưới là component `App`.

Trong `App`, toàn bộ hệ thống route được đặt bên trong `Router`.

Bên trong `Router` có `Routes`, và bên trong `Routes` là từng `Route`.

Ví dụ:

- `path="/"` sẽ render component `Home`.
- `path="/about"` sẽ render component `About`.

Như vậy, `Route` có thể hiểu là nơi khai báo mối quan hệ giữa **đường dẫn URL và component cần hiển thị**.”

---

## Trang 17 – Kết quả khi truy cập `/about`

“Sau khi cấu hình như trên, đây là kết quả khi truy cập đường dẫn `/about`.

Chúng ta có thể thấy trên thanh địa chỉ hiện tại là `localhost:3000/about`.

React Router đọc URL này, tìm thấy route `/about`, sau đó render component `About`.

Vì vậy trên giao diện chúng ta thấy `About View`.

Đây chính là kết quả thực tế của luồng mà chúng ta vừa nói:

**URL → Route → Component.**”

---

## Trang 18 – Cách hoạt động của Link

“Sau khi đã hiển thị được các trang dựa trên URL, vấn đề tiếp theo là: **người dùng sẽ chuyển giữa các trang bằng cách nào?**

Trong React Router, chúng ta sử dụng component `Link`.

`Link` là component của `react-router-dom`, dùng để điều hướng giữa các route trong ứng dụng React.

Khi người dùng click vào `Link`, quá trình diễn ra theo bốn bước.

Đầu tiên, người dùng click vào `Link`, ví dụ click `About`.

Tiếp theo, URL thay đổi thành `/about`.

Sau đó, React Router tìm route phù hợp với URL đó.

Cuối cùng, component tương ứng được render, trong ví dụ này là `About View`.

Như vậy có thể nhớ luồng:

**Click Link → URL thay đổi → React Router tìm Route → Render Component.**”

---

## Trang 19 – Câu hỏi tương tác

Đến slide này bạn có thể **dừng lại và hỏi khán giả**:

> “Theo mọi người, tại sao trong React Router chúng ta lại dùng `Link` thay vì dùng thẻ `<a>` thông thường?”

Đợi một vài giây cho mọi người trả lời, rồi bạn nói:

“Đúng rồi. Điểm khác biệt chính nằm ở việc tải lại trang.

Khi sử dụng thẻ `<a>`, trình duyệt thường thực hiện điều hướng theo cách truyền thống và tải lại trang.

Còn `Link` của React Router cho phép thay đổi URL và chuyển route **ngay trong SPA mà không cần reload toàn bộ trang**.

Nhờ vậy trải nghiệm chuyển trang sẽ mượt hơn và vẫn giữ đúng cơ chế của Single Page Application.”

---

## Trang 20 – Điều hướng bằng Link

“Bây giờ chúng ta đưa `Link` vào code.

Ở đây trong component `App`, chúng ta tạo một thanh `nav`.

Bên trong có hai `Link`.

`Link to="/"` dùng để chuyển về trang Home.

Còn `Link to="/about"` dùng để chuyển sang trang About.

Phía dưới vẫn là phần khai báo route.

Ngoài hai route `/` và `/about`, chúng ta có thêm route `*` để hiển thị `NoMatch` nếu URL không hợp lệ.

Điểm quan trọng là khi dùng `Link`, việc chuyển trang được thực hiện ngay trong ứng dụng React, thay vì tải lại toàn bộ trang như cách điều hướng thông thường bằng thẻ `<a>`.

Đây là một đặc điểm rất quan trọng trong Single Page Application.”

---

## Trang 21 – Kết quả điều hướng bằng Link

“Và đây là kết quả sau khi chúng ta triển khai điều hướng bằng `Link`.

Ở phía trên giao diện chúng ta có hai liên kết là `Home` và `About`.

Hiện tại URL đang là `/about`, vì vậy component `About` đang được render.

Nếu người dùng click vào `Home`, URL sẽ chuyển về `/` và component `Home` sẽ được hiển thị.

Nếu click lại `About`, URL chuyển sang `/about` và React Router render `About`.

Toàn bộ quá trình điều hướng này diễn ra **mà không cần tải lại toàn bộ trang**.

Như vậy, ở phần 2 chúng ta đã nắm được ba ý chính:

- **Component** dùng để xây dựng từng phần giao diện.
- **Route** dùng để liên kết URL với Component.
- **Link** được dùng để điều hướng giữa các route trong ứng dụng.”

---

# PHẦN 3 — NESTED ROUTES VÀ DYNAMIC ROUTES

## Chuyển sang phần 3

“Sau khi đã biết cách tạo route và điều hướng cơ bản, em xin chuyển sang **phần 3: Nested Routes và Dynamic Routes**.

Ở phần này chúng ta sẽ giải quyết một bài toán thực tế hơn: khi một trang có nhiều trang con và các trang này dùng chung một phần giao diện, chúng ta nên tổ chức route như thế nào?”

---

## Nested Router là gì?

“Đầu tiên là **Nested Router**, hay chính xác hơn là **Nested Routes**.

Nested Routes là kỹ thuật đặt các route con bên trong một route cha.

Ví dụ trong hình bên trái, chúng ta có route cha là `/posts`. Bên trong `/posts` sẽ có các route con đại diện cho từng nội dung.

Điểm quan trọng nằm ở hình bên phải.

Một trang web thường có những thành phần cố định như `Header`, `Navbar`, `Sidebar` hay layout chung. Khi chuyển giữa các route con, chúng ta không cần render lại toàn bộ giao diện đó mà chỉ cần thay đổi vùng nội dung bên trong.

Do đó Nested Routes giúp chúng ta tổ chức route theo cấu trúc cha – con, tái sử dụng layout chung và làm ứng dụng dễ quản lý hơn.”

---

## Tại sao cần Nested Routes?

“Để thấy rõ hơn lý do cần Nested Routes, chúng ta xem ví dụ một trang Blog.

Ở đây có hai đường dẫn:

- `/blog/first-blog-post`
- `/blog/second-blog-post`

Hai trang này đều sử dụng chung tiêu đề Blog, menu điều hướng, header và layout.

Nếu không sử dụng Nested Routes thì ở Blog 1 và Blog 2, chúng ta có thể phải viết lại những thành phần giống nhau.

Trong khi thực tế chỉ có nội dung của bài viết là thay đổi.

Do đó Nested Routes giúp chúng ta giữ phần layout chung ở route cha và chỉ thay đổi nội dung của route con.

Kết quả là giảm lặp code, URL rõ ràng hơn và cấu trúc chương trình cũng dễ mở rộng hơn.”

---

## Outlet trong Nested Routes

“Vậy câu hỏi là: nếu giữ layout của route cha, thì nội dung của route con sẽ được hiển thị ở đâu?

React Router giải quyết vấn đề này bằng component `Outlet`.

Trong ví dụ này, phần `My Blog` và các liên kết `Blog 1`, `Blog 2` thuộc về giao diện chung của route cha.

Bên dưới chúng ta đặt `<Outlet />`.

Có thể hiểu `Outlet` giống như một vị trí trống dành cho route con.

Khi URL thay đổi, React Router tìm route con phù hợp và đưa component của route đó vào đúng vị trí `Outlet`.

Nhờ vậy phần cha vẫn giữ nguyên, còn phần bên trong `Outlet` được thay đổi theo route.”
