## git-tips
> Tuyển tập `git-tips`, bạn muốn đóng góp thêm? Vui lòng xem chi tiết [contributing.md](./contributing.md)

[English](http://git.io/git-tips) | [中文](https://github.com/521xueweihan/git-tips) | [Русский](https://github.com/Imangazaliev/git-tips) | [한국어](https://github.com/mingrammer/git-tips) | [Tiếng Việt](https://github.com/hprobotic/git-tips)

### __Công cụ:__

* [git-tip](https://www.npmjs.com/package/git-tip) - Một công cụ tiện dụng dụng để bạn có thể sử dụng một cách tối ưu. ([Here in Docker container](https://github.com/djoudi5/docker-git-tip))

P.S: Tất cả các câu lệnh dưới đây đã được kiểm tra bằng `git version 2.7.4 (Apple Git-66)`.




<!-- @doxie.inject start -->
<!-- Don’t remove or change the comment above – that can break automatic updates. -->
## Sử dụng 
```sh
git help everyday
```

## Show helpful guides that come with Git
```sh
git help -g
```

## Tìm kiếm thay đổi bằng nội dung
```sh
git log -S'<a term in the source>'
```

## Đồng bộ với remote, ghi đè tất cả những thay đổi hiện tại
```sh
git fetch origin && git reset --hard origin/master && git clean -f -d
```

## Danh sách tất cả các tệp trong 1 commit
```sh
git ls-tree --name-only -r <commit-ish>
```

## Git reset first commit
```sh
git update-ref -d HEAD
```

## Danh sách tất cả tệp đã bị conflict
```sh
git diff --name-only --diff-filter=U
```

## Danh sách tất cả các file đã bị thay đổi trong 1 commit
```sh
git diff-tree --no-commit-id --name-only -r <commit-ish>
```

## Tất cả những thay đổi chưa được ghi nhận kể từ commit cuối cùng
```sh
git diff
```

## Những thay đổi đã được ghi nhận
```sh
git diff --cached
```


__Cách khác:__
```sh
git diff --staged
```

## Xem mọi thay đổi trên tệp kể từ commit cuối
```sh
git diff HEAD
```

## Danh sách tất cả các `branch` đã được `merged` vào `master`
```sh
git branch --merged master
```

## Quay lại branch gần nhất
```sh
git checkout -
```


__Cách khác:__
```sh
git checkout @{-1}
```

## Xóa tất cả `branch` đã được `merged` vào `master`
```sh
git branch --merged master | grep -v '^\*' | xargs -n 1 git branch -d
```


__Cách khác:__
```sh
git branch --merged master | grep -v '^\*\|  master' | xargs -n 1 git branch -d # will not delete master if master is not checked out
```

## Danh sách tất cả branch và thông tin cơ bản: upstream, commit gần nhất
```sh
git branch -vv
```

## Thông tin về upstream của branch
```sh
git branch -u origin/mybranch
```

## Xóa một branch trên máy
```sh
git branch -d <local_branchname>
```

## Xóa một remote branch
```sh
git push origin --delete <remote_branchname>
```


__Cách khác:__
```sh
git push origin :<remote_branchname>
```

## Xóa một tag trên máy
```sh
git tag -d <tag-name>
```

## Xóa một remote tag
```sh
git push origin :refs/tags/<tag-name>
```

## Undo local changes with the last content in head
```sh
git checkout -- <file_name>
```

## Revert: Hủy bỏ một commit bằng cách tạo thêm 1 commit
```sh
git revert <commit-ish>
```

## Reset: Hủy bỏ tất cả commit, khuyên dùng cho branch cá nhân
```sh
git reset <commit-ish>
```

## Sửa lại commit message gần vừa tạo
```sh
git commit -v --amend
```

## Xem lịch sử commit riêng branch hiện tại
```sh
git cherry -v master
```

## Người thay đổi.
```sh
git commit --amend --author='Author Name <email@address.com>'
```

## Reset tác giả, sau khi tác giả đã bị thay đổi trong cấu hình toàn hệ thống.
```sh
git commit --amend --reset-author --no-edit
```

## Thay đổi đường dẫn remote
```sh
git remote set-url origin <URL>
```

## Lấy danh sách của tất các remote
```sh
git remote
```


__Cách khác:__
```sh
git remote show
```

## Lấy danh sách branch trên local và remote
```sh
git branch -a
```

## Chỉ lấy danh sách branch trên remote
```sh
git branch -r
```

## Lưu thay đổi 1 phần của tệp, thay vì toàn bộ tệp
```sh
git add -p
```

## Lấy câu lệnh git tự động hoàn thành
```sh
curl http://git.io/vfhol > ~/.git-completion.bash && echo '[ -f ~/.git-completion.bash ] && . ~/.git-completion.bash' >> ~/.bashrc
```

## Những gì đã thay đổi trong 2 tuần gần nhất?
```sh
git log --no-merges --raw --since='2 weeks ago'
```


__Cách khác:__
```sh
git whatchanged --since='2 weeks ago'
```

## Xem tất cả những commit đã được tạo từ khi fork từ master
```sh
git log --no-merges --stat --reverse master..
```

## Chọn các commit từ nhiều branch sử dụng `cherry-pick`
```sh
git checkout <branch-name> && git cherry-pick <commit-ish>
```

## Tìm cách branch có chứa `commit-hash`
```sh
git branch -a --contains <commit-ish>
```


__Cách khác:__
```sh
git branch --contains <commit-ish>
```

## Gõ tắt Git
```sh
git config --global alias.<handle> <command> 
git config --global alias.st status
```

## Lưu trạng thái hiện tại của các tệp mà không commit
```sh
git stash
```


__Cách khác:__
```sh
git stash save
```

## Lưu trạng thái hiện tại của những thay đổi chưa được lưu vào những tệp đã được theo dõi
```sh
git stash -k
```


__Cách khác:__
```sh
git stash --keep-index
```


```sh
git stash save --keep-index
```

## Lưu trạng thái hiện tại bao gồm cả tệp chưa được theo dõi
```sh
git stash -u
```


__Cách khác:__
```sh
git stash save -u
```


```sh
git stash save --include-untracked
```

## Lưu trạng thái hiện tại với message
```sh
git stash save <message>
```

## Lưu trạng thái hiện tại của tất cả file (bị bỏ qua, chưa được theo dõi, và được theo dõi)
```sh
git stash -a
```


__Cách khác:__
```sh
git stash --all
```


```sh
git stash save --all
```

## Xem danh sách tất cả các lưu tạm
```sh
git stash list
```

## Áp dụng lưu tạm bất kỳ mà không xóa nó hỏi danh sách lưu tạm
```sh
git stash apply <stash@{n}>
```

## Áp dụng lưu tạm cuối cùng và xóa nó khỏi danh sách lưu tạm
```sh
git stash pop
```


__Cách khác:__
```sh
git stash apply stash@{0} && git stash drop stash@{0}
```

## Xóa tất cả lưu tạm
```sh
git stash clear
```


__Cách khác:__
```sh
git stash drop <stash@{n}>
```

## Lấy 1 file từ 1 lưu tạm
```sh
git checkout <stash@{n}> -- <file_path>
```


__Cách khác:__
```sh
git checkout stash@{0} -- <file_path>
```

## Hiển thị danh sách tệp được theo dõi
```sh
git ls-files -t
```

## Hiển thị danh sách tệp chưa được theo dõi
```sh
git ls-files --others
```

## Hiển thị danh sách tệp bị bỏ qua
```sh
git ls-files --others -i --exclude-standard
```

## Tạo nhánh làm việc mới từ một repo (git 2.5)
```sh
git worktree add -b <branch-name> <path> <start-point>
```

## Tạo một nhánh làm việc mới từ trạng thái HEAD
```sh
git worktree add --detach <path> HEAD
```

## Hủy bỏ theo dõi tệp mà không xóa nó
```sh
git rm --cached <file_path>
```


__Cách khác:__
```sh
git rm --cached -r <directory_path>
```

## Trước khi xóa những tệp/ thư mục chưa được theo dõi, thực thi việc lấy danh sách các tệp/ thư mục này
```sh
git clean -n
```

## Force: Xóa bỏ tất cả tệp chưa được theo dõi
```sh
git clean -f
```

## Force: Xóa bỏ tất cả thư mục chưa được theo dõi
```sh
git clean -f -d
```

## Cập nhật tất cả submodule
```sh
git submodule foreach git pull
```


__Cách khác:__
```sh
git submodule update --init --recursive
```


```sh
git submodule update --remote
```

## Hiển thị tất cả các commit chưa được `merged` vào `master` của `branch` hiện tại
```sh
git cherry -v master
```


__Cách khác:__
```sh
git cherry -v master <branch-to-be-merged>
```

## Đổi tên một branch
```sh
git branch -m <new-branch-name>
```


__Cách khác:__
```sh
git branch -m [<old-branch-name>] <new-branch-name>
```

## Rebases 'feature' thành 'master' và merges nó vào master
```sh
git rebase master feature && git checkout master && git merge -
```

## Khóa branch `master`
```sh
git archive master --format=zip --output=master.zip
```

## Thay đổi commit gần nhất mà không thay đổi commit message
```sh
git add --all && git commit --amend --no-edit
```

## Truy vấn đến cho các nhánh remote mà nó đã bị xóa trong remote.
```sh
git fetch -p
```


__Cách khác:__
```sh
git remote prune origin
```

## Truy xuất `commit-hash` của bản sửa đổi ban đầu.
```sh
 git rev-list --reverse HEAD | head -1
```


__Cách khác:__
```sh
git rev-list --max-parents=0 HEAD
```


```sh
git log --pretty=oneline | tail -1 | cut -c 1-40
```


```sh
git log --pretty=oneline --reverse | head -1 | cut -c 1-40
```

## Xem cây commit theo dạng đồ họa
```sh
git log --pretty=oneline --graph --decorate --all
```


__Cách khác:__
```sh
gitk --all
```

## Deploy một thư mục đã được theo dõi vào `gh-pages`
```sh
git subtree push --prefix subfolder_name origin gh-pages
```

## Thêm một dự án vào repo sử dụng subtree
```sh
git subtree add --prefix=<directory_name>/<project_name> --squash git@github.com:<username>/<project_name>.git master
```

## Lấy thay đổi mới nhất trong repo của bạn cho một dự án đã được liên kết dùng subtree
```sh
git subtree pull --prefix=<directory_name>/<project_name> --squash git@github.com:<username>/<project_name>.git master
```

## Xuất một branch với lịch sử ra một tệp
```sh
git bundle create <file> <branch-name>
```

## Nhập từ một bundle
```sh
git clone repo.bundle <repo-dir> -b <branch-name>
```

## Lấy tên của branch hiện tại
```sh
git rev-parse --abbrev-ref HEAD
```

## Bỏ qua 1 file trong commit (e.g. Changelog).
```sh
git update-index --assume-unchanged Changelog; git commit -a; git update-index --no-assume-unchanged Changelog
```

## Lưu tạm các thay đổi trước khi `rebase`
```sh
git rebase --autostash
```

## Cập nhật yêu cầu tích hợp bằng ID vào local branch
```sh
git fetch origin pull/<id>/head:<branch-name>
```


__Cách khác:__
```sh
git pull origin pull/<id>/head:<branch-name>
```

## Hiển thị tag gần nhất trên branch hiện tại.
```sh
git describe --tags --abbrev=0
```

## Hiển thị thay đổi tổng quát.
```sh
git diff --word-diff
```

## Hiển thị thay đổi sử dụng các công cụ.
```sh
git difftool -t <commit1> <commit2> <path>
```

## Không xem xét các thay đổi cho tệp đã theo dõi.
```sh
git update-index --assume-unchanged <file_name>
```

## Hủy assume-unchanged.
```sh
git update-index --no-assume-unchanged <file_name>
```

## Dọn dẹp các tệp từ `.gitignore`.
```sh
git clean -X -f
```

## Khôi phục tệp đã bị xóa.
```sh
git checkout <deleting_commit>^ -- <file_path>
```

## Khôi phục một file từ một `commit-hash` nhất định
```sh
git checkout <commit-ish> -- <file_path>
```

## Luôn `rebase` thay vì tích hợp khi pull.
```sh
git config --global pull.rebase true
```


__Cách khác:__
```sh
#git < 1.7.9
git config --global branch.autosetuprebase always
```

## Danh sách tất cả các lối tắt và cấu hình.
```sh
git config --list
```

## Cấu hình git phân biệt chữ hoa chữ thường
```sh
git config --global core.ignorecase false
```

## Thêm trình soạn thảo của bạn.
```sh
git config --global core.editor '$EDITOR'
```

## Tự động sửa lỗi chính tả.
```sh
git config --global help.autocorrect 1
```

## Kiểm tra nếu thay đổi đã là một phần của xuất bản.
```sh
git name-rev --name-only <SHA-1>
```

## Dry run. (tất cả các câu lệnh hộ trợ `dry-run` được gắn cờ nên sử dụng.)
```sh
git clean -fd --dry-run
```

## Gán commit của bạn là 1 fix của commit trước đó.
```sh
git commit --fixup <SHA-1>
```

## Squash fixup commits normal commits.
```sh
git rebase -i --autosquash
```

## Bỏ qua khu vực dàn trong quá trình commit.
```sh
git commit --only <file_path>
```

## Interactive staging.
```sh
git add -i
```

## Danh sách tệp bị bỏ qua.
```sh
git check-ignore *
```

## Trạng thái của tệp bị bỏ qua.
```sh
git status --ignored
```

## Các commit ở Branch1 mà không có ở Branch2
```sh
git log Branch1 ^Branch2
```

## Danh sách n commit gần nhất
```sh
git log -<n>
```


__Cách khác:__
```sh
git log -n <n>
```

## Reuse recorded resolution, record and reuse previous conflicts resolutions.
```sh
git config --global rerere.enabled 1
```

## Mở tất cả những tệp bị conflict bằng trình soạn thảo.
```sh
git diff --name-only | uniq | xargs $EDITOR
```

## Đếm số đối tượng và dung lượng ổ đĩa của file đã giải nén
```sh
git count-objects --human-readable
```

## Xoá tất cả các đối tượng không thể truy cập từ cơ sở dữ liệu đối tượng.
```sh
git gc --prune=now --aggressive
```

## Chuyển đến repo của bạn trên gitweb bằng trình duyệt.
```sh
git instaweb [--local] [--httpd=<httpd>] [--port=<port>] [--browser=<browser>]
```

## View the GPG signatures in the commit log
```sh
git log --show-signature
```

## Xóa bỏ mục trong cấu hình toàn hệ thống.
```sh
git config --global --unset <entry-name>
```

## Khởi tạo một branch mới không có lịch sử
```sh
git checkout --orphan <branch_name>
```

## Xem tệp của branch khác.
```sh
git show <branch_name>:<file_name>
```

## Chỉ liệt kê commit gốc và đã merge.
```sh
git log --first-parent
```

## Thay đổi 2 commit với một interactive rebase.
```sh
git rebase --interactive HEAD~2
```

## Danh sách tất cả branch là WIP
```sh
git checkout master && git branch --no-merged
```

## Tìm lỗi với tìm kiếm nhị phân
```sh
git bisect start                    # Search start 
git bisect bad                      # Set point to bad commit 
git bisect good v2.6.13-rc2         # Set point to good commit|tag 
git bisect bad                      # Say current state is bad 
git bisect good                     # Say current state is good 
git bisect reset                    # Finish search 

```

## Bỏ qua `pre-commit` và `commit-msg` khi commit
```sh
git commit --no-verify
```

## Danh sách các commit và thay đổi cho 1 file nhất định (kể cả file đã đổi tên)
```sh
git log --follow -p -- <file_path>
```

## Clone 1 branch duy nhất
```sh
git clone -b <branch-name> --single-branch https://github.com/user/repo.git
```

## Tạo và chuyển qua branch mới ngay lập tức
```sh
git checkout -b <branch-name>
```


__Cách khác:__
```sh
git branch <branch-name> && git checkout <branch-name>
```

## Bỏ qua kiểu thay đổi tệp trên các commit
```sh
git config core.fileMode false
```

## Tắt giao diện màu trong terminal
```sh
git config --global color.ui false
```

## Chỉ định cấu hình màu theo branch, diff..
```sh
git config --global <specific command e.g branch, diff> <true, false or always>
```

## Hiển thị tất cả các branch đã xếp đặt trong các commit gần đây
```sh
git for-each-ref --sort=-committerdate --format='%(refname:short)' refs/heads/
```

## Tìm các dòng thỏa điều kiện (regex hoặc chuỗi) trong những tệp được theo dõi
```sh
git grep --heading --line-number 'foo bar'
```

## Clone một sao chép bóng của repo
```sh
git clone https://github.com/user/repo.git --depth 1
```

## Tìm kiếm lịch sử commit trên toàn bộ branch bằng một từ khóa cho trước
```sh
git log --all --grep='<given-text>'
```

## Lấy commit đầu tiên trong một branch (từ `master`)
```sh
git log master..<branch-name> --oneline | tail -1
```

## Hủy lưu thay đổi tệp
```sh
git reset HEAD <file-name>
```

## Đẩy lên remote repo và bỏ qua mọi vật cản
```sh
git push -f <remote-name> <branch-name>
```

## Thêm tên Remote
```sh
git remote add <remote-nickname> <remote-url>
```

## Hiển thị tác giả, thời gian và bản ghi gần nhất lên từng dòng của 1 file cho trước
```sh
git blame <file-name>
```

## Nhóm các commit theo các tác giả và tiêu đề
```sh
git shortlog
```

## Forced push nhưng vẫn đảm bảo bạn không ghi đè lên những thay đổi của người khác
```sh
git push --force-with-lease <remote-name> <branch-name>
```

## Hiển số dòng đóng góp của một tác giả
```sh
git log --author='_Your_Name_Here_' --pretty=tformat: --numstat | gawk '{ add += <!-- @doxie.inject start -->; subs += <!-- @doxie.inject end -->; loc += <!-- @doxie.inject start --> - <!-- @doxie.inject end --> } END { printf "added lines: %s removed lines: %s total lines: %s
", add, subs, loc }' -
```


__Cách khác:__
```sh
git log --author='_Your_Name_Here_' --pretty=tformat: --numstat | awk '{ add += <!-- @doxie.inject start -->; subs += <!-- @doxie.inject end -->; loc += <!-- @doxie.inject start --> - <!-- @doxie.inject end --> } END { printf "added lines: %s, removed lines: %s, total lines: %s
", add, subs, loc }' - # on Mac OSX
```

## Revert: Hoàn nguyên toàn bộ một `merge`
```sh
git revert -m 1 <commit-ish>
```

## Số lượng commit trong 1 branch
```sh
git rev-list --count <branch-name>
```

## Gõ tắt: git undo
```sh
git config --global alias.undo '!f() { git reset --hard $(git rev-parse --abbrev-ref HEAD)@{${1-1}}; }; f'
```

## Thêm các ghi chú
```sh
git notes add -m 'Note on the previous commit....'
```

## Hiển thị tất cả `git-notes`
```sh
git log --show-notes='*'
```

## Áp dụng commit từ một repo khác
```sh
git --git-dir=<source-dir>/.git format-patch -k -1 --stdout <SHA1> | git am -3 -k
```

## Fetch từ một ref nhất định
```sh
git fetch origin master:refs/remotes/origin/mymaster
```

## Tìm gốc chung của 2 nhánh
```sh
diff -u <(git rev-list --first-parent BranchA) <(git rev-list --first-parent BranchB) | sed -ne 's/^ //p' | head -1
```

## Danh sách commit chưa push
```sh
git log --branches --not --remotes
```


__Cách khác:__
```sh
git log @{u}..
```


```sh
git cherry -v
```

## Thêm mọi thứ, nhưng bỏ qua thay đổi khoảng trắng
```sh
git diff --ignore-all-space | git apply --cached
```

## Chỉnh [local/global] git config
```sh
git config [--global] --edit
```

## Xem `blame` trong một khoảng nhất định
```sh
git blame -L <start>,<end>
```

## Xem một biến Git logical
```sh
git var -l | <variable>
```

## Tệp vá lỗi được định dạng sẵn.
```sh
git format-patch -M upstream..topic
```

## Lấy tên repo.
```sh
git rev-parse --show-toplevel
```

## Xem logs trong một khoảng ngày tháng
```sh
git log --since='FEB 1 2017' --until='FEB 14 2017'
```

## Xem logs ngoại trừ tác giả
```sh
git log --perl-regexp --author='^((?!excluded-author-regex).*)

```

## Tạo ra một bản tóm tắt các thay đổi đang chờ
```sh
git request-pull v1.0 https://git.ko.xz/project master:for-linus
```

## Danh sách các ref trong remote repository
```sh
git ls-remote git://git.kernel.org/pub/scm/git/git.git
```

## Sao lưu những file không được theo dõi.
```sh
git ls-files --others -i --exclude-standard | xargs zip untracked.zip
```

## Danh sách các lệnh gõ tắt
```sh
git config -l | grep alias | sed 's/^alias\.//g'
```


__Cách khác:__
```sh
git config -l | grep alias | cut -d '.' -f 2
```

## Hiển thị trạng thái git ở dạng rút gọn
```sh
git status --short --branch
```

## Quay về một commit tại 1 thời điểm nhất định trong quá khứ
```sh
git checkout master@{yesterday}
```

## Đẩy một branch từ local lên remote và theo dõi
```sh
git push -u origin <branch_name>
```

<!-- Don’t remove or change the comment below – that can break automatic updates. More info at <http://npm.im/doxie.inject>. -->
<!-- @doxie.inject end -->
