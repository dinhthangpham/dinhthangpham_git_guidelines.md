# Hướng dẫn sử dụng project trong git
1, Git

![thang](https://raw.githubusercontent.com/elsewhencode/project-guidelines/master/images/branching.png)

1.1, Một số tắc ở git.
Một số quy tắc cần nhớ:
* Thực hiện công việc trong 1 nhánh tính năng 

&nbsp; _Tại sao_: 
>  Bởi vì cách này, tất cả các công việc được thực hiện trong sự cô lập trên một nhánh chuyên dụng chứ không phải là nhánh chính. Nó cho phép bạn gửi đi nhiều yêu cầu mà không bị nhầm lẫn. Bạn có thể lặp đi lặp lại mà không làm rối nhánh chính với khả năng không ổn định, lập trình chưa hoàn thành, [đọc thêm](https://www.atlassian.com/git/tutorials/comparing-workflows#feature-branch-workflow),..
* Chi nhánh từ nhà phát triển
&nbsp; _Tại sao_:
> Tại cách này, bạn có thể chắc chắn rằng code sẽ luôn được xây lên mà không có vấn đề gì, và nó còn được sử dụng trực tiếp cho nhà phát hành (nó có thể quá mức cần thiết cho 1 số dự án) 
* Đừng bao giờ đẩy lên nhà phát triển hoặc nhánh chính. Hãy tạo 1 yêu cầu
&nbsp; _Tại sao_:
> Nó thông báo các thành viên trong nhóm rằng họ đã hoàn thành một tính năng. Nó còn dễ dàng để đánh giá của code và dành riêng cho để thảo luận về tính năng được đề xuất.
* Cập nhật vị trí nhánh chính của bạn và thực hiện 1 rebase (là 1 chức năng được dùng để gắn nhánh công việc đã hoàn thành vào nhánh gốc) trước khi đẩy tính năng của bạn và đưa ra 1 yêu cầu.

&nbsp; _Tại sao_:
> (giáo sư hoặc nhà phát triển) và áp dụng vào cam kết mà bạn thực hiện vào đầu lịch sử mà không tạo ra một cam kết hợp nhất. Dẫn đến một kết quả tốt và lịch sử sạch sẽ. [Đọc thêm](https://www.atlassian.com/git/tutorials/merging-vs-rebasing)...
* Giải quyết các xung đột tiềm ẩn trong khi đánh giá lại và trước khi đưa ra yêu cầu

* Xóa các nhánh chính cục bộ và từ xa sau khi hợp nhất

&nbsp; _Tại sao_:
> Nó sẽ làm lộn xộn lên danh sách nhánh với các nhánh chết. Nó bảo đảm bạn chỉ gộp các nhánh bởi (`giáo sư` hoặc `nhà phát triển`)
* Trước khi tạo một yêu cầu, chắc chắn rằng các nhánh chức năng của bạn đã được xây dựng thành công và đã vượt qua tất cả các kiểm thử (bao gồm cả kiểm tra phong cách lập trình)

&nbsp; _Tại sao_:
> Bạn sắp thêm code của bạn vào nhánh ổn định. Nếu nhánh tính năng kiểm thử thất bại, nó là cơ hội cao răng xây dựng chi nhánh đích của bạn cũng sẽ thất bại. Ngoài ra, bạn cần áp dụng kiểm tra phong cách code trước khi gửi yêu cầu. Nó hỗ trợ khả năng đọc, giảm cơ hội định dạng các bản sửa lỗi với những thay đổi trong thực tế.
* Sử dụng `.gitignore` file

&nbsp; _Tại sao_:
> Nó sẵn sàng có một danh sách tệp tin hệ thống không nên gửi với code của bạn vào kho lưu trữ từ xa. Thêm vào đó, nó loại trừ cài đặt thư mục và tệp tin cho hầu hết các trình soạn thảo sử dụng, cũng giống như các thư mục phổ biến nhất.
* Bảo vệ `nhà phát triển ` của bạn và nhánh `chủ`

&nbsp; _Tại sao_:
> Nó bảo vệ những chi nhánh sẵn sàng sản xuất của bạn khỏi những thay đổi không mong muốn và không thể đảo ngược. Đọc thêm... [Github](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/about-protected-branches), [Bitbucket](https://confluence.atlassian.com/bitbucketserver/using-branch-permissions-776639807.html) và [Gitlab](https://docs.gitlab.com/ee/user/project/protected_branches.html)

1.2 Git workflow
Bởi vì một số nguyên nhân ở trên, chúng ta sử dụng [Feature-branch-workflow](https://www.atlassian.com/git/tutorials/comparing-workflows#feature-branch-workflow) với [ Interactive Rebasing](https://www.atlassian.com/git/tutorials/merging-vs-rebasing#the-golden-rule-of-rebasing) và một số yếu tố của [Gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows#gitflow-workflow) (đặt tên và có một nhánh phát triển). Các bước chính :
* Đối với một dự án mới, khởi tạo kho thư mục git trong thư mục dự án. Đối với các tính năng/thay đổi tiếp theo, bước này nên được bỏ qua.
``` 
cd <project directory>
git init
```
* Kiểm tra một tính năng mới/ lỗi nhánh
```
git checkout -b <branchname>
```
* Tạo sự thay đổi
```
git add <file1> <file2> ...
git commit
```
&nbsp; _Tại sao_:
> `git add <file1> <file2> ...` - Bạn nên chỉ thêm một tệp tin tạo sự thay đổi nhỏ.

> `git commit` sẽ bắt đầu một trình soạn thảo giúp bạn tách chủ đề khỏi thân.

> Đọc thêm nó về phiên bản 1.3

&nbsp; _Mẹo_:
> Thay vào đó, bạn có thể sử dụng `git add -p`, điều này sẽ cho bạn cơ hội xem xét tất cả các thay đổi được giới thiệu từng người một và quyết định có nên đưa chúng vào cam kết hay không.
* Đồng bộ từ xa để tránh những thay đổi mà bạn bỏ lỡ
```
git checkout develop
git pull
```

&nbsp; _Tại sao_:
> Nó sẽ cho bạn một cơ hội đối phó những xung đột của máy tính của bạn trong khi rebasing (sau này) thay vì tạo ra yêu cầu có chứa xung đột
* Cập nhật các nhánh chức năng cùng với sự thay đổi cuối từ phía nhà phát triển bởi tương tác rebase 
```
git checkout <branchname>
git rebase -i --autosquash develop
```
&nbsp; _Tại sao_:
> Bạn có thể sử dụng --Autosquash để đè bẹp tất cả các cam kết của bạn cho một cam kết duy nhất. Không ai muốn nhiều cam kết cho một tính năng duy nhất trong phát triển nhánh. [Xem thêm](https://thoughtbot.com/blog/autosquashing-git-commits).
* Nếu bạn không có xung đột, bỏ qua tới bước tiếp theo. Nếu bạn có xung đột, giải quyết chúng và tiếp tục rebase
```
git add <file1> <file2> ...
git rebase --continue
```
* Đẩy cánh của bạn. Rebase sẽ thay đỏi lịch sử, sau đó bạn phải sử dụng `-f` để buộc thay đổi vào nhánh từ xa. Nếu ai đó khác làm tại nhánh của bạn , sử dụng ít phá hoại hơn `--force-with-lease`.

```
git push -f
```
&nbsp; _Tại sao_:
> Khi bạn làm rebase, bạn đang thay đổi chính lịch sử của bạn tại các nhánh chức năng. Kết quả là, git sẽ từ chối bình thường `git push`. Thay vì, bạn sẽ cần tới `-f` hoặc `--force flag`. [Đọc thêm](https://blog.developer.atlassian.com/force-with-lease/)
* Tạo một yêu cầu
* Yêu cầu sẽ được chấp nhận, gộp và đóng bởi người dùng
* Điều khiển vị trí nhánh chức năng của bạn nếu bạn đã xong
```
git branch -d <branchname> 
``` 
để xóa bỏ tất cả các nhánh không quá dài từ xa
```
git fetch -p && for branch in `git branch -vv --no-color | grep ': gone]' | awk '{print $1}'`; do git branch -D $branch; done
```
1.3 Viết một tin nhắn cam kết tốt
Có một hướng dẫn tốt cho việc khởi tạo cam kết và bám sát nó làm cho nó hoạt động với git và hợp tác với người khác dễ hơn nhiều. Đây là một số quy tắc ngón tay cái ([Nguồn](https://chris.beams.io/posts/git-commit/#seven-rules)) :
* Tách một chủ đề khỏi cơ thể  với dòng mưới giữa 2
&nbsp; _Tại sao_:
> Git đủ nhỏ để phân biệt dòng đầu tiên trong tin nhắn cam kết của bạn như bản tóm tắt. Mặt khác, Nếu bạn cố rút ngắn git, thay vì git dài, bạn sẽ nhìn 1 danh sách dài trong tin nhắn cam kết của bạn, bao gồm id của bản tóm tắt và chỉ 1 bản tóm tắt.
* Giới hạn dòng chủ thể  50 kí tự và xuống dòng ở cơ thể tại 72 kí tự.
&nbsp; _Tại sao_:
> Bản cam kết nên được tập trung, tránh không bị rời rạc. [Xem thêm](https://medium.com/@preslavrachev/what-s-with-the-50-72-rule-8a906f61f09c)
* Viết hoa dòng chủ đề 
* Không kết thúc dòng chủ đề với một khoảng thời gian
* Sử dụng [imperative mood](https://en.wikipedia.org/wiki/Imperative_mood) trong dòng chủ đề.
&nbsp; _Tại sao_:
> Thay vì viết tin nhắn nói những gì một người đi làm đã làm. Tốt hơn là xem xét các tin nhắn này là hướng dẫn cho những gì sẽ được thực hiện sau khi cam kết được áp dụng trên kho lưu trữ. [Đọc thêm](https://news.ycombinator.com/item?id=2079612)...
* Sử dụng cơ thể để giải nghĩa cái gì và tại sao như trái ngược như thế nào.