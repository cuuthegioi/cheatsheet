# Git cheatsheet 1.1
#work

## Git config
- Copy ssh key
```
pbcopy < ~/.ssh/id_rsa.pub
```

- Show config
`git config --list`

`open ~/.ssh/config`

- Change config
```
git config --global user.name "Sean"
git config --global user.email thaison@react-plus.com
```

## Tạo Git và project
- Tạo git trong project
Vào thư mục dự án, chạy lệnh
`git init` 

- Set remote đến một git repository có sẵn
Khi đã tạo repository trên github và đã có thư mục dự án dưới local. Chạy câu lệnh này để link project 
`git remote add origin git@github.com:react-plus/git-training.git`

- Download source code từ 1 repository
`git clone git@github.com:react-plus/git-training.git`

## Thay đổi file dưới local
-  Kiểm tra tình trạng thay đổi (thêm/sửa/xóa)
`git status`

Các file mới tạo sẽ không được tự động add vào git, muốn add chạy 
`git add .`  (dấu chấm tương đương với add toàn bộ file, muốn add từng file thì thay dấu chấm bằng đường dẫn đến file đó)

xóa file khỏi git 
`git rm <đường dẫn đến file>`

- Commit 
Cứ mỗi đầu việc được hoàn thành thì hãy tạo commit 
`git commit -am 'noi dung commit'`
-a : (all) commit tất cả sự thay đổi ở local
m : (message) nội dung commit, thường sẽ là nội dung của thay đổi hoặc chức năng đó

```
git add -u
git reset — main/dontcheckmein.txt
```


- Stash
Lưu thay đổi tạm thời (nhưng không tạo commit)
`git stash`

lấy lại thay đổi để làm việc tiếp.
`git stash pop`

- Reset sự thay đổi của file dưới local
`git checkout <file>`

## Log
- Xem các commit
`git log`

- Kiểm tra lịch sử thay đổi của 1 file
Kiểm tra ai đã thay đổi những gì, vào lúc nào
`git blame <file>`

## Branches
Thường có 2 branch chính : master và develop
Luôn làm trên branch riêng rồi merge vào develop
Không code trên master
- List ra danh sách các branches
`git branch -av`

- Tạo branch mới
`git branch <tên branch>`
hoặc
`git checkout -b <tên branch>`

- Chuyển qua branch khác 
Lưu ý, phải commit các thay đổi của branch hiện tại trước khi chuyển qua branch khác
`git checkout <tên branch>`

- Push code từ local lên remote
`git push`

- Pull code từ remote về local
`git pull`

- Push(publish) branch local lên remote 
`git push origin <tên branch>`

push branch local lên remote với **tên khác**
`git push origin <local-name>:<remote-name>`

- Xóa local branch 
`git branch -d <tên branch>`

- Xóa branch trên remote
```
git push <remote_name> -—delete <branch_name>
git branch -d <branch_name>
```

ví dụ : git push origin —delete test-branch

## Merge
- Merge từ branch A sang branch B
1- checkout sang branch B
2- `git merge A`

- Khi có conflict
resolve bằng app, bằng cơm, hoặc
`git merge —strategy-option theirs` -> lấy hết code của người khác, không lấy code mình
hoặc `git checkout —theirs PATH/FILE`

`git checkout —ours PATH/FILE`  -> lấy code local, không lấy code của người khác

## Lấy code từ branch khác
