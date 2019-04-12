# .gitignore

- 2019.04.09: 첫 작성

## git ignore

- 프로젝트에 들어가면 안되는 파일 제외목적으로 사용
  - 백업, 로그 등 굳이 git에 들어갈 필요가 없는 파일들
  - 설정 등 공개되서는 안되는 정보

## 사용법

1. root 폴더에 .gitignore 파일 생성
2. 내용 기록

   - .gitignore 파일에 입력하는 패턴은 아래 규칙을 따른다.
     - 아무것도 없는 라인이나, `#`로 시작하는 라인은 무시한다.
     - 표준 Glob 패턴을 사용한다. 이는 프로젝트 전체에 적용된다.
     - 슬래시(/)로 시작하면 하위 디렉토리에 적용되지(Recursivity) 않는다.
     - 디렉토리는 슬래시(/)를 끝에 사용하는 것으로 표현한다.
     - 느낌표(!)로 시작하는 패턴의 파일은 무시하지 않는다.
   - 예시

     ```bash
     # 확장자가 .a인 파일 무시
     *.a

     # 윗 라인에서 확장자가 .a인 파일은 무시하게 했지만 lib.a는 무시하지 않음
     !lib.a

     # 현재 디렉토리에 있는 TODO파일은 무시하고 subdir/TODO처럼 하위디렉토리에 있는 파일은 무시하지 않음
     /TODO

     # build/ 디렉토리에 있는 모든 파일은 무시
     build/

     # doc/notes.txt 파일은 무시하고 doc/server/arch.txt 파일은 무시하지 않음
     doc/*.txt

     # doc 디렉토리 아래의 모든 .pdf 파일을 무시
     doc/**/*.pdf
     ```

   - TIP : GitHub은 다양한 프로젝트에서 자주 사용하는 .gitignore 예제를 관리하고 있다. 어떤 내용을 넣을지 막막하다면 [Github gitignore repo](https://github.com/github/gitignore) 사이트에서 적당한 예제를 찾을 수 있다.

3. commit & push

## 출처

- [Github: Ignoring files](https://help.github.com/en/articles/ignoring-files)
- [Nesoy Blog: Git .gitignore 적용하기](https://nesoy.github.io/articles/2017-01/Git-Ignore)
- [Pro Git: 2.2 Git의 기초 - 수정하고 저장소에 저장하기 > 파일 무시하기](https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EC%88%98%EC%A0%95%ED%95%98%EA%B3%A0-%EC%A0%80%EC%9E%A5%EC%86%8C%EC%97%90-%EC%A0%80%EC%9E%A5%ED%95%98%EA%B8%B0)
