
README.md ファイルの更新を考える。
	1.リモートリポジトリ（Github上）にあるREADME.mdをローカルリポジトリへクローンする。（git clone）
	2.ローカルリポのREADME.mdについて、ブランチを切る。(update-readme)
	3.ローカルリポのREADME.mdについて、更新を行いコミットする。
	4.ローカルリポをリモートリポジトリに反映する（git push）
	5.update-readmeをmainブランチにマージする
	6.リモートリポをローカルリポに反映する（git pull）
	7.不要なブランチを削除する

1.git clone <sshのアドレス>
git config -- user.name<>
git config -- user.email<>

cd Desketop :Desketop へ移動
mkdir :ファイルの作成

2.
git branch 現在の作業branchを表示する。
git branch＜branch-name＞ 　　新しいbranchを切る
git checkout＜branch-name＞ 　作業branchを切り替える
git checkout -b ＜branch-name＞ branchを切って、作業branchに切り替える

3.Working directory → staging area　に追加する
git status 作業状態を確認する
git add<filename> 作業内容をstaging areaに追加する

3.ローカルリポにcommit する
git commit -m "コミットメッセージ"
コミットメッセージは端的にわかりやすく