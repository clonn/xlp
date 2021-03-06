##纠纷解决程序

* 立案程序：获取起诉状模板：

 	1. 资格认证（参见开户流程）
 	1. 下载起诉状模板（参见原告流程1）撰写并提交起诉状：参见原告流程2、3、4接收立案决定:即原告流程5，被告流程1

* 诉讼程序：

	- 收集并提交证据（包括任务回执时间戳、专利证书、物证等），参见原告流程6、7，被告流程2、3
	- 参加调解
	- 接收简易程序判决书
	- 参加庭审：

		1. 陈述诉讼请求
		1. 举证质证
		2. 法庭辩论
		3. 接收判决书

* 其他规则：
	- 在得到具有法律效力的调解书、判决书（包括简易程序和一般程序判决书）后，应严格依照法律文书之规定的要求、期限加以履行
	- 如法院做出开庭审理的决定，则应原被告及第三人应携带相关证据原件（或复印件），遵循法院发出的庭审理通知书中规定的时间准时到庭参加诉讼。如果原告无正当理由缺席或未准时出席，按撤诉处理；若被告无正当理由缺席或未准时出席，按败诉处理。如果原告或被告一方或双方人数（组数）为两者或以上，则由本方推选出一组为代表组，代表本方参与诉讼，代表组所谓的法律行为推定为本方全体意志，代表组在审理结束后所享有的权利及应履行的义务对本方全体成员有效。

* 流程
* 开户

	1. 各个团队的法律总监（以下简称总监）在GITLAB网页上找到THUXLP_Court项目，向挑战方管理团队的法官李智发送issue，标题为法律总监开户，标签为Law开户，内容为总监的git用户名，以获取THUXLP_Court的developer权限
	1. 总监收到邮件提示获得权限后，将THUXLP_Court项目的reception分支克隆到本地工作空间，使用以下命令：

	```
	git clone git@166.111.59.15:toyhouse/thuxlp_court.git -b reception
	```

* 原告
	1. 总监执行git checkout -b A_sues_B，新建一个分支，其中A为本组编号，B为被诉组编号。总监在data文件夹中新建一个名为A_sues_B的文件夹，其中A为本组编号，B为被诉组编号总监到docs文件夹里将XLP_Court_Indictment.md复制到data/A_sues_B中
	2. 打开文件，按照模板撰写*起诉书*。
	3. 保存文件，在git中add、commit提交起诉书。commit的信息写明：GroupA_sues_GroupB(起诉组对被起诉组)。通过

	```
	git push origin A_sues_B:A_sues_B
	```
上传起诉书。
	4. 打开issue，通知法官李智新建的branch，标题为：GroupA_sues_GroupB(起诉组对被起诉组), Labels为：Law起诉
	5. 等待反馈，若案件被受理，执行git pull origin A_sues_B
	6. 收集证据，将证据放在data/A_sues_B/evidence_A中，其中A为本组编号，commit（message为:uploaded evidence from accuser)、push
	7. 向法官发issue，告知证据收集完毕，格式为：原告A证据收集完毕
	8. 等待处理结果，执行git checkout reception切换到模板分支

* 被告
	1. 在issue中被告知，执行git fetch origin A_sues_B:A_sues_B，将案件信息取回本地执行git checkout A_sues_B切换到该分支
	2. 收集证据，将证据放在data/A_sues_B/evidence_B，其中B为本组编号，commit（message为:uploaded evidence from defendant)、push时执行：git push origin A_sues_B
	3. 证据收集完毕，向法官发issue，告知证据收集完毕，格式为：被告B证据收集完毕
	4. 等待处理结果，执行git checkout reception切换到模板分支
