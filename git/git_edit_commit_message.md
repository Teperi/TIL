# Commit Message 수정

2019.03.10

- 과거 git commit messages 에 오타를 발견했을 때 사용

```bash
git reabase -i HEAD~N
# N 자리에 숫자를 넣어야 함
# 현재 commit 에서 오타난 commit 까지의 commit 개수만큼 적으면 됨

# 이후 수정하고 싶은 커밋 메시지 앞에 pick 글을 지우고 edit 로 변경하고 저장

git commit --amend
# 커밋 메시지 변경

git rebase --continue
# rebase 완료하고 다시 commit 해서 원래대로 돌아가기

git push origin master --force
# 서버에 있는 commit 파일 변경
```

출처: [How to change your commit messages in Git?](https://gist.github.com/nepsilon/156387acf9e1e72d48fa35c4fabef0b4)