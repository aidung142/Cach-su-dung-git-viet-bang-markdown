# Cách dùng git

## Cách thức mà git hoạt động 

![image-20211028223456612](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20211028223456612.png)

các trạng thái mà 1 file có thể có: 

1. untracked: file chưa được git theo dõi

2. unmodified: file đã được theo dõi và không có thay đổi gì so với lần commit cuối

3. modified: file đã được theo dõi và có thay đổi so với lần commit cuối

4. staged: được đánh dấu để chuẩn bị lưu vào cơ sở dữ liệu 

   **Một file mới cứng khi muốn đưa lên cơ sở dữ liệu phải(đang ở trạng thái untracked) cần đưa tới trạng thái staged nếu muốn commit**

   **Khi tải 1 file về và sửa đổi nó (đang ở modified) ta cũng cần đưa về stage để có thể commit **

## Các lệnh git 

1. **Khởi tạo kho chứa git với git init** 

   ```
   git init
   ```

   

   sau câu lệnh trong tệp muốn đẩy lên git hub 

   ![image-20211028222602875](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20211028222602875.png)

2. **Để kiểm tra trạng thái thư mục làm việc ta dùng lệnh: git status**

   ```
   git status 
   ```

   ![image-20211028223052160](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20211028223052160.png)

Ở đây thông báo 2 file git chưa theo dõi, muốn theo dõi sử dụng lệnh git add 

```
git add
```

3. Lệnh git add: đưa 1 file vào vùng staged

   ```
   git add bai 1.txt
   ```

   để đưa tất cả file vào vùng staged ta dùng lệnh 

   ```
   git add .
   ```

   

4. **Lệnh commit: sau khi đã đưa các file vào trạng thái staged. Dùng lệnh commit để đưa dữ liệu lên cơ sở dữ liệu** 

   ví dụ 

   ```
   git commit -m "C1 - lan dau lam chuyen ay"
   ```

   ở đây là lần đầu commit có ghi chú: lan dau lam chuyen ay 

   ![image-20211028225512820](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20211028225512820.png)

sau khi commit thì sẽ có mã, ở đây là 6af9e41. nó giúp cho mình sau này chỉ ra một commit nào đó

5. **Để kiểm tra số lần commit, thông tin các lần đó ta dùng lệnh** 

   ```
   git log
   ```

   ![image-20211028225838386](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20211028225838386.png)

ở đây ta thấy được HEAD cho ta biết đang ở nhánh nào và vị trí nào trong lịch sử commit. ở đây mới có 1 lần commit nên ta chưa thấy rõ việc nó đang nằm ở commit nào 

Ta thử kiểm tra bằng lệnh 

```
git status
```

![image-20211028230113182](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20211028230113182.png)

Báo rằng toàn bộ file ta đang làm việc không có thay đổi gì so với lần cuối commit. Mọi thứ đã được lưu an toàn lên git



6. **Khôi phục file**

Giả sử ta xóa file bai2.txt

kiểm tra lại ta thấy 

![image-20211028230550143](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20211028230550143.png)

dùng lệnh 

```
git restore bai2.txt 
```

file bai2.txt sẽ được lấy lại 

Trong trường hợp xóa tất cả và muốn lấy lại hết ở lần commit cuối ta dùng lệnh 

```
git restore .
```

7. **Thay đổi dữ liệu trong 1 file **

   ví dụ thay đổi nội dung trong file bai1.txt 

   ![image-20211028231303901](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20211028231303901.png)

báo lại rằng có thay đổi ở file bai1.txt 

sử dụng lệnh 	

```
git diff
```

trả về 

![image-20211028231438800](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20211028231438800.png)

Ở đây thấy  a/ thư mục làm việc  b/ là thư mục commit cuối 

được sửa thêm chữ "hello world"

commit lại 

![image-20211028231811161](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20211028231811161.png)

Kiểm tra lại các lần commit 

![image-20211028231918960](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20211028231918960.png)

8. **Thêm file vào vùng làm việc**

ví dụ thêm file bai3.txt Khi đó để kiểm tra sự khác nhau so với lần commit cuối ta dùng 

```
git diff --staged
```

![image-20211028232625067](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20211028232625067.png)

kiểm tra lại

![image-20211028232950166](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20211028232950166.png)

9. **Để lấy thông tin các lần commit vắn tắt**

```
git log --oneline
```

![image-20211028233140511](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20211028233140511.png)

10. **Phục hồi 1 file ở lần commit nào đó**

ví dụ muốn phục hồi file bai1.txt về lần commit đầu 

```
git checkout 6af9e41 -- bai1.txt
```

![image-20211028233656731](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20211028233656731.png)

file bai1.txt  được sửa đổi đã vào luôn staged và sẵn sàng commit 

để đưa ra vùng staged dùng lệnh 

```
git restore --staged .
```

đưa các file về trạng thái commit cuối : 

```
git checkout -- . 
```

