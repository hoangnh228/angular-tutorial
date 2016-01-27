# angular-tutorial
Hướng dẫn về framework AngularJS <br /><br />
## Tổng quan về AngularJS
### Giới thiệu
AngularJS là một bộ Javascript Framework rất mạnh và thường được sử dụng để xây dựng project Single Page Application (SPA). Nó mở rộng HTML DOM với các thuộc tính bổ sung cho nên đáp ứng được nhiều yêu cầu từ phía người dùng. AngularJS là một Framework mã nguồn mở hoàn toàn miễn phí và được hàng ngàn các lập trình viên trên thế giới ưa chuộng và sử dụng. Angular JS hỗ trợ mô hình MVC.

Dưới đây là một số tính năng cốt lõi quan trọng của AngularJS:
- Data-binding (Ràng buộc dữ liệu): tự động đồng bộ dữ liệu giữa model và view
- Scope: những đối tượng kết nối Controller và View
- Controller: lớp business logic phía sau views
- Service: mục đích của xây dựng service là để tái sử dụng các phương thức chung ở nhiều view hoặc controller khác nhau
- Filters (Bộ lọc): format lại dữ liệu hiển thị ra ngoài view người dùn
- Directives: cho phép mở rộng HTML và bạn có thể custom lại các thuộc tính (attribute), phần tử (elements)
- Templates: hiển thị thông tin từ controller, đây là một thành phần của views
- Routing: chuyển đổi giữa các action trong controller
- MVW: Model-View-Whatever, từ MVW chúng ta có thể phát triển thành MVC Model-View-Controller hoặc là MVVM Model-View-ViewModel
- Deep Linking (Liên kết sâu): cho phép bạn mã hóa trạng thái của ứng dụng trong các URL để nó có thể đánh dấu được với công cụ tìm kiếm.
- Dependency Injection: liên kết, thống nhất các đối tượng và chắc năng.

Mối liên hệ giữa các thành phần trong AngularJS <br />
<img src="https://s3.amazonaws.com/classconnection/362/flashcards/6692362/png/screen_shot_2014-12-23_at_70514_pm-14A7A42335A47DBBC08.png" width="400">

### Cài đặt
Để sử dụng AngularJS trong project, bạn cần phải khai báo 1 cặp thẻ `<script></script>` chứa đường link tới file <kbd>angular.min.js</kbd>. Trong tutorial này, tôi sẽ sử dụng AngularJS phiên bản 1.4.9 (phiên bản ổn định). Bạn có thể tải AngularJS trên [trang chủ](https://angularjs.org/) rồi giải nén, hoặc sử dụng CDN như sau `https://ajax.googleapis.com/ajax/libs/angularjs/1.4.9/angular.min.js`.

## Expression - Controller - Scope
### Expression
AngularJS đồng bộ dữ liệu giữa ứng dụng với HTML bằng cách sử dụng _expression_. Hiểu 1 cách đơn giản, expression là dữ liệu chúng ta muốn hiển thị ra màn hình. Dữ liệu ở đây có thể là số, chuỗi, phần tử của mảng hoặc thuộc tính của đối tượng... 
Expression được viết bên trong cặp dấu {{ }} 

[Demo Expression](https://github.com/ntaback26/angular-tutorial/blob/master/expression.html)

**Giải thích:** thuộc tính <kbd>ng-app</kbd> ở thẻ body là thuộc tính của AngularJS. Nó đánh dấu vị trí mà code AngularJS bắt đầu có hiệu lực. Thuộc tính <kbd>ng-init</kbd> có nhiệm vụ khởi tạo giá trị cho các biến. ng-app và ng-init được gọi là _directive (điều hướng)_

### Controller
Trong AngularJS, controller có nhiệm vụ chính là điều khiển dữ liệu của ứng dụng. Một controller được định nghĩa bằng cách sử dụng directive <kbd>ng-controller</kbd>. Một controller là một đối tượng Javascript bao gồm các thuộc tính và các phương thức.

_Ví dụ 1:_

[Hiển thị dòng chữ Hello AngularJS trên màn hình](https://github.com/ntaback26/angular-tutorial/blob/master/controller/variable.html)

**Giải thích:** Trong đoạn code trên, controller và view đồng bộ dữ liệu với nhau thông qua đối tượng <kbd>$scope</kbd>. Giá trị của ng-app sẽ được truyền vào trong câu lệnh `angular.module('giá trị của ng-app', [])`

_Ví dụ 2:_

Ở ví dụ trên là ta truyền 1 biến vào đối tượng $scope. Ví dụ dưới đây ta sẽ thử truyền 1 hàm vào $scope

[Truyền hàm vào $scope](https://github.com/ntaback26/angular-tutorial/blob/master/controller/function.html)

_Ví dụ 3:_

[Truyền đối tượng vào $scope](https://github.com/ntaback26/angular-tutorial/blob/master/controller/object.html)

### Scope
Scope có nhiệm vụ đồng bộ dữ liệu giữa HTML (View) và Javascript (Controller). Một scope là 1 đối tượng Javascript đặc biệt bao gồm các thuộc tính và các phương thức. Các thuộc tính và phương thức này có thể được sử dụng ở cả View và Controller.<br />
Trong mô hình MVC của AngularJS thì:
- View chính là những đoạn mã HTML hiển thị phía người dùng
- Model là dữ liệu phục vụ cho view hiện tại
- Controller là những hàm Javascript có nhiệm vụ thêm, sửa, xóa, điều khiển dữ liệu

Và scope chính là Model. 

**$rootScope**
Nếu như $scope chỉ ảnh hưởng trong phạm vi của controller (tính từ phần tử HTML khai báo ng-controller), thì $rootScope ảnh hưởng lên toàn bộ ứng dụng (tính từ phần tử HTML khai báo ng-app).

[Demo rootScope](https://github.com/ntaback26/angular-tutorial/blob/master/scope/rootScope.html)

Trong ví dụ trên, ta có thể thấy nếu như $rootScope và $scope có một thuộc tính cùng tên, thì ở trong div khai báo ng-controller, thuộc tính của $scope sẽ ghi đè thuộc tính của $rootScope, nhưng ở bên ngoài div đó, thuộc tính của $rootScope sẽ không bị ghi đè.

## Directive
### Khái niệm
AngularJS cho phép chúng ta mở rộng các phần tử HTML bằng cách thêm các thuộc tính mới gọi là _directive_. Bên cạnh những directive mà AngularJS đã cung cấp sẵn thì chúng ta cũng có thể tự định nghĩa các directive của riêng mình. 

Các thuộc tính là directive thường có tiền tố **ng-** ở phía trước, ví dụ như: ng-app, ng-controller, ng-model, ... Danh sách các directive của AngularJS bạn có thể xem ở [đây](https://docs.angularjs.org/api/ng/directive)

Dựa theo chức năng, các directive có thể phân chia thành các nhóm như sau:

<img src="http://image.slidesharecdn.com/dc9765ab-3c86-4477-87d5-39c277594241-150303075043-conversion-gate01/95/bdotnet-angularjs-directives-uday-7-638.jpg?cb=1425390686" width="400" />
### Tự định nghĩa directive
Ví dụ dưới đây sẽ định nghĩa 1 directive có nhiệm vụ render ra 1 form đăng nhập

[Tự định nghĩa directive](https://github.com/ntaback26/angular-tutorial/blob/master/directive/define.html)

**Giải thích:** Ta đặt tên cho directive theo kiểu camel case <kbd>myLoginForm</kbd>, khi triệu gọi directive thì ta sẽ viết tên directive theo kiểu <kbd>my-login-form</kbd>. [Đọc thêm](http://www.w3schools.com/angular/angular_directives.asp)

### Data binding
**1. ng-model**

Directive ng-model có những nhiệm vụ sau:
- Đồng bộ giá trị của các HTML control (input, select, button, textarea) với dữ liệu của ứng dụng
- Cung cấp các validation như required, number, email, url,...
- Kiểm soát trạng thái của các HTML control (valid/invalid, dirty/pristine, touched/untouched, validation errors)
- Thêm vào hoặc xóa đi các class CSS ở các HTML control dựa theo trạng thái của model. Danh sách các class:
	- ng-valid: the model is valid
    - ng-invalid: the model is invalid
    - ng-valid-[key]: for each valid key added by $setValidity
    - ng-invalid-[key]: for each invalid key added by $setValidity
    - ng-pristine: the control hasn't been interacted with yet
    - ng-dirty: the control has been interacted with
    - ng-touched: the control has been blurred
    - ng-untouched: the control hasn't been blurred
    - ng-pending: any $asyncValidators are unfulfilled
    - ng-empty: the view does not contain a value or the value is deemed "empty", as defined by the ngModel.NgModelController method
    - ng-not-empty: the view contains a non-empty value


_Ví dụ 1: Cho 1 thẻ input, khi nhập giá trị vào input thì expression cùng tên cũng sẽ mang giá trị tương ứng_

[Two-Way Binding](https://github.com/ntaback26/angular-tutorial/blob/master/directive/two-way.html)

[Đọc thêm về Data Binding](https://docs.angularjs.org/guide/databinding)

_Ví dụ 2: Cho 1 thẻ input, kiểm tra xem giá trị nhập vào có phải là chữ số hay không_

[Input validation](https://github.com/ntaback26/angular-tutorial/blob/master/directive/input-validation)

**Giải thích:** Ta thử nhập 1 chữ cái vào ô input, bật firebug lên ta sẽ thấy thẻ \<input> có thêm 1 class <kbd>ng-invalid</kbd> 

**2. ng-model-options**
ng-model-options dùng để cấu hình một số thông số liên quan tới ng-model. Khi ứng dụng được chạy lên thì ng-model-options sẽ thực thi trước và sau đó ng-model mới được tạo. Các thông số bao gồm:
- updateOn: xác định thao tác nào (blur, default, kepress, ...) sẽ quyết định việc update $scope
- debounce: xác định khoảng thời gian sau bao lâu (tính bằng millisecond) thì update $scope
- getterSetter
- allowInvalid
- timezone

_Ví dụ 1: Cho 1 thẻ input, sau khi nhập giá trị, phải click chuột ra ngoài input thì expression mới thay đổi_

[updateOn](https://github.com/ntaback26/angular-tutorial/blob/master/directive/updateOn.html)

_Ví dụ 2: Cho 1 thẻ input, sau khi nhập giá trị, phải đợi 1s thì expression mới thay đổi_

[debounce](https://github.com/ntaback26/angular-tutorial/blob/master/directive/debounce.html)

**3. ng-bind**

ng-bind cũng có tác dụng giống như expression. So sánh expression và ng-bind:

**Expression:** Thỉnh thoảng khi load ứng dụng trên trình duyệt, ta có thể thấy đoạn mã expression sẽ nhấp nháy khoảng vài millisecond trước khi dữ liệu trong expression được load. Bởi vì template được load trước khi AngularJS biên dịch các phần tử. Để giải quyết vấn đề này ta có thể sử dụng directive [ng-cloak](https://docs.angularjs.org/api/ng/directive/ngCloak)

**ng-bind:** được sử dụng bên trong các phần tử HTML DOM. ng-bind sẽ được thực thi ngay khi dữ liệu thay đổi.

Trong [ví dụ 1](https://github.com/ntaback26/angular-tutorial/blob/master/directive/two-way.html) ở phần ng-model, thay vì sử dụng expression ta sẽ sử dụng ng-bind: [ng-bind](https://github.com/ntaback26/angular-tutorial/blob/master/directive/ng-bind.html)

**4. ng-bind-html**

Directive này cho phép chúng ta in ra 1 đoạn mã HTML, điều mà ta không thể làm với ng-bind. Khi sử dụng ng-bind-html, ta cần phải thêm thư viện [sanitize](http://ajax.googleapis.com/ajax/libs/angularjs/1.4.9/angular-sanitize.js)

_Ví dụ:_ Cho 1 thẻ input, nhập vào 1 đường link thì đường link đó sẽ hiện ra.

[ng-bind-html](https://github.com/ntaback26/angular-tutorial/blob/master/directive/ng-bind-html.html)

**5. ng-bind-template**

Directive này sẽ xác định nội dung cần thay thế thông qua expression {{}} đặt trong nó. Không giống như ng-bind, ng-bind-template có thể chứa nhiều expression trong nó, ví dụ như `ng-bind-template="{{firstName}} {{lastName}}"`

_Ví dụ:_ Cho 2 thẻ input nhập vào firstName và lastName, giá trị nhập vào 2 thẻ sẽ hiển thị trong cùng 1 thẻ \<span>

[ng-bind-template](https://github.com/ntaback26/angular-tutorial/blob/master/directive/ng-bind-template.html)


### DOM Manipulation
Trong AngularJS, chúng ta có 3 directive để liên kết dữ liệu của ứng dụng với thuộc tính của các phần tử HTML DOM là: **ng-disabled**, **ng-show** và **ng-hide**. Nếu biểu thức bên trong 3 thuộc tính này mà **true** thì các phần tử HTML DOM sẽ thay đổi như sau:
- Với phần tử có chứa thuộc tính ng-disabled: sẽ được thêm thuộc tính <kbd>disabled="disabled"</kbd>
- Với phần tử có chứa thuộc tính ng-show: sẽ xóa đi class <kbd>.ng-hide</kbd>
- Với phần tử có chứa thuộc tính ng-hide: sẽ thêm vào class <kbd>.ng-hide</kbd>

_Ví dụ:_ Cho 3 checkbox và 3 button. Khi click checkbox 1, button 1 sẽ bị disabled. Click checkbox 2, button 2 sẽ hiện ra. Click checkbox 3, button 3 sẽ bị ẩn đi.

[DOM manipulation](https://github.com/ntaback26/angular-tutorial/blob/master/directive/dom-manipulation.html)

**Giải thích:** Với checkbox 1 và button 1, checkbox 1 nếu chưa được tích vào thì biểu thức disableButton sẽ mang giá trị false, còn khi tích vào nó sẽ sẽ trả về giá trị true. Khi disbaleButton mang giá trị true, button 1 sẽ được thêm thuộc tính disabled="disabled". Tương tự với 2 checkbox và button còn lại.


### Events
AngularJS  cung cấp một số event directive cho phép chúng ta chạy hàm của AngularJS khi xảy ra sự kiện người dùng. Một sự kiện của AngularJS sẽ không ghi đè sự kiện tương ứng của HTML, cả 2 sự kiện sẽ được thực thi cùng nhau. 

Danh sách các event directive trong angular:
- ng-blur
- ng-change
- ng-click
- ng-copy
- ng-cut
- ng-dblclick
- ng-focus
- ng-keydown
- ng-keypress
- ng-keyup
- ng-mousedown
- ng-mouseenter
- ng-mouseleave
- ng-mousemove
- ng-mouseover
- ng-mouseup
- ng-paste

_Ví dụ 1:_ Mỗi lần click vào 1 button thì hiển thị ra số lần đã click

[count](https://github.com/ntaback26/angular-tutorial/blob/master/directive/ng-click.html)

_Ví dụ 2:_ Hiển thị ra 1 menu dọc khi click vào 1 button, và ẩn menu đó đi khi click lần nữa.

[toggle](https://github.com/ntaback26/angular-tutorial/blob/master/directive/toggle.html)




## Form

### Form submit
Để submit 1 form trong AngularJS, ta có thể sử dụng 2 cách sau:
- Sử dụng directive **ng-submit** trong thẻ form
- Sử dụng directive **ng-click** ở thẻ input hoặc button có <kbd>type="submit"</kbd> đầu tiên

Một vài lưu ý khi submit form:
- Nếu form chỉ có một thẻ input duy nhất thì form sẽ submit khi chúng ta nhấn Enter vào thẻ input đó
- Nếu form có hai thẻ input trở lên và không có button submit hoặc (input[type="submit"]) thì khi chúng ta nhấn Enter thì form sẽ không submit
- Nếu form có một hoặc nhiều field và có một hoặc nhiều button submit hoặc (input[type="submit"]) thì khi chúng ta nhấn Enter vào một field bất kỳ, AngularJS sẽ kích hoạt sự kiện Click trên button hoặc input đầu tiên (ng-click) cũng như sự kiện submit của form (ng-submit)

### Form and Input state
Để có thể kiểm tra dữ liệu đầu vào (validate data), AngularJs đã cung cấp cho chúng ta các **state** cho Input và Form
Input có các thuộc tính state sau:
- $untouched: trả về true nếu field chưa có tác động
- $touched: trả về true nếu field đã bị tác động    
- $pristine: trả về true nếu field chưa bị thay đổi
- $dirty: trả về true nếu field đã bị thay đổi
- $invalid: trả về true nếu field hợp lệ
- $valid: trả về true nếu field hợp lệ
- $error: đối tượng này bao gồm tất cả các thuộc tính validation (required, maxlength, minlength, ...)

Thuộc tính state của input có dạng: <kbd>formName.inputFieldName.propertyName</kbd>

Form có các thuộc tính state sau:
- $pristine: trả về true nếu không có field nào bị thay đổi
- $dirty: trả về true nếu có một hoặc nhiều field bị thay đổi
- $invalid: trả về true nếu nội dung của form không hợp lệ
- $valid: trả về true nếu nội dung của form hợp lệ
- $submitted: trả về true nếu form đã được submit

Thuộc tính state của form có dạng: <kbd>formName.propertyName</kbd>

Dựa trên các state, AngularJS sẽ thêm vào form và input các class CSS tương ứng
