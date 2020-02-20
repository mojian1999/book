## git 基础
	-- 网址 (https://git-scm.com/book/zh/v2)
	--1.版本控制分类
		-- 本地版本控制
		-- 集中式版本控制
		-- 分布式版本控制  git  svn 
	--2.git 特点：
		-- 直接记录快照，而非差异比较
		-- 近乎所有操作都是本地执行
		-- Git 保证完整性
		-- Git 一般只添加数据
	--3. git的三种状态 ***
		-- 已提交（committed）已提交表示数据已经安全的保存在本地数据库中。 
		-- 已修改（modified）已修改表示修改了文件，但还没保存到数据库中。 
		-- 已暂存（staged） 已暂存表示对一个已修改文件的当前版本做了标记，使之包含在下次提交的快照中。
	--4.git基本的工作流程如下：
		-- 在工作目录中修改文件。
		-- 暂存文件，将文件的快照放入暂存区域。
		-- 提交更新，找到暂存区域的文件，将快照永久性存储到 Git 仓库目录。
## git 常用命令
	--1.基础配置和帮助
		-- git config --list 查看配置项
		-- git config --global user.name "写英文的名字的全拼"
		-- git config --global user.email 写自己的邮箱地址
		-- git help 显示帮助信息 英文的
	--2.git的基础三步命令	
		-- git init 初始化  ，会出现master (主分支), 表示文件目录已经备git管理了
		-- git add 文件名  将要跟踪的某个文件放入暂存区域
		-- git add * 将所有要跟踪的文件全部放入暂存区域
		-- git add . 将 所有新增或处于修改状态的文件，加入到暂存区域
		-- git commit -m "说明" 提交到git仓库
		-- git status 查看git的状态
	--3.新增、修改、删除后的各种状态
		--新增文件后
	    Untracked files:
	   (use "git add <file>..." to include in what will be committed)
	         tt1.txt
	
		--执行add命令后，输入 git status ，显示如下	
		On branch master
		Changes to be committed:
		  (use "git reset HEAD <file>..." to unstage)
		
		        new file:   test/test-1.txt
		        new file:   tt.js
		        new file:   yy.css
				
		-- 执行commit 操作后，输入 git status，显示如下：
		[master 8bb7414] 增加了 文件和文件夹
		 4 files changed, 0 insertions(+), 0 deletions(-)
		 create mode 100644 test/test-1.txt
		 create mode 100644 tt.js
		 create mode 100644 tt1.txt
		 create mode 100644 yy.css
		 
		-- 修改文件后，执行 git status，结果：
		 On branch master
		 Changes not staged for commit:
		   (use "git add <file>..." to update what will be committed)
		   (use "git checkout -- <file>..." to discard changes in working directory)
		 
		         modified:   bb.html
		 
		 no changes added to commit (use "git add" and/or "git commit -a")
		
		-- 修改后的文件执行了 git add 之后 ，输入 git status 命令 ,结果是：
		On branch master
		Changes to be committed:
		  (use "git reset HEAD <file>..." to unstage)
		
		        modified:   bb.html
		-- 修改后的文件执行了 git commit -m "***" 之后 ，输入 git status 命令 ,结果是：
			On branch master
			nothing to commit, working tree clean


​		
​		-- 删除文件
​		On branch master
​		Changes not staged for commit:
​		  (use "git add/rm <file>..." to update what will be committed)
​		  (use "git checkout -- <file>..." to discard changes in working directory)
​		
		        deleted:    aa.txt
		
		no changes added to commit (use "git add" and/or "git commit -a")
		-- 删除后 git add  aa.txt ， 执行 git status
		On branch master
		Changes to be committed:
		  (use "git reset HEAD <file>..." to unstage)
		
		        deleted:    aa.txt
		-- 删除文件后，执行 git commit -m "提交删除文件" ，
		[master 6467da4] 提交删除文件
		 1 file changed, 0 insertions(+), 0 deletions(-)
		 delete mode 100644 aa.txt
		-- 删除文件后 ，执行 git status
		On branch master
		nothing to commit, working tree clean
	
	-- 4.四.忽略文件的做法
		1.在hbuilder 中创建新的  .gitignore 文件 
		2.将该文件复制到 gittest 文件夹下
		3.将要忽略的文件名或者文件夹写在这个文件里
		hulue-1.txt
		hulue-2.txt
		/hulue
		.gitignore
		4.执行 git status ，查看该文件是否已经被忽略
	-- 5.修改文件时查看文件的具体差异
		git  diff
		结果：
			diff --git a/bb.html b/bb.html
			index c7f0891..c178737 100644
			--- a/bb.html
			+++ b/bb.html
			@@ -5,6 +5,7 @@
							<title></title>
					</head>
					<body>
			-       hello git
			+       <h1>git课程 操作比较麻烦</h1>
			+       <h2>好盼望使用小乌龟啊!</h2>
					</body>
			 </html>
			
	-- 6. 删除文件  将本地的文件删除，暂存区也清除。文件不可恢复
		git rm 文件名（tt.js） 
	移除后执行 git status命令，结果如下：
	On branch master
	Changes to be committed:
	  (use "git reset HEAD <file>..." to unstage)
	
	        deleted:    tt.js
	
	Changes not staged for commit:
	  (use "git add <file>..." to update what will be committed)
	  (use "git checkout -- <file>..." to discard changes in working directory)
	git commit -m "提交移除操作修改操作"
	
	--7. 想要从暂存区删除文件，但是在项目中文件还是存在的
	删除后它会被放到未被跟踪的列表中，如果想git仓库中的该文件也删除，需要 git commit
	如果想要他不被跟踪，需要将文件名加入到 .gitignore文件中 ，这种操作更安全一些
	git rm --cached 文件名    
	
	--8.移动文件
	 git mv 文件名 另一个地址/文件     
	 例： git mv yy.css test/yy.css


	--9.查看历史记录
		git log  
		注意：如果记录比较多，一屏不能显示全，到end时，光标还没有跳出，请输入 英文状态下的:q
		-- 查询近两次的历史记录
		git log -p -2
		-- 简单的统计操作
		git log -p -2 --stat
		-- 指定格式显示  oneline short full fuller
		git log --pretty=oneline
		-- 可以按照需要的配置显示内容
		git log --pretty="%h - %an - %ae - %s - %cr"
		-- 历史记录的区间查询
		git log --pretty="%h - %s"  --since="2020-02-01"  --before="2020-02-27" 
	-- 10.撤销提交 ，如：提交的信息写错了，需要修改
		git commit --amend
		按i键进入修改操作，修改完成后，按esc键退出，按:wq保存