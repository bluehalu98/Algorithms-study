# Algorithms-study

알고리즘 문제 원문/풀이를 md로 관리하는 저장소입니다.

## Directory Layout

```text
archive/
  boj/
    1000/
      alice/
        README.md
        solution.py
  programmers/
    12909/
      bob/
        README.md
        solution.py
templates/
  problem.md
  solution.md
scripts/
  new-problem.sh
  import-bjh.sh
```

## Quick Start

```bash
# 새 문제 폴더/템플릿 생성
./scripts/new-problem.sh boj 1000 alice "A+B"

# BaekjoonHub 원본 폴더를 팀 표준 경로로 복사
./scripts/import-bjh.sh 2562 alice "/path/to/백준/Bronze/2562.최댓값"

# source_dir 생략 시 ./백준/*/<problem_id>.* 자동 탐색
./scripts/import-bjh.sh 2562 alice
```

`import-bjh.sh`는 기본적으로 `archive/<platform>/<problem_id>/<user_id>/`를 생성하고,
원본 폴더의 `README.md`와 코드 파일 1개를 파일명 그대로 복사합니다.

## BaekjoonHub Rule

- BaekjoonHub는 디렉터리 템플릿은 지원하지만, 결과 파일명은 기본적으로 `문제제목.확장자`와 `README.md` 패턴입니다.
- 그래서 팀 표준(`archive/<platform>/<problem_id>/<user_id>/`)은 `import-bjh.sh`로 정규화합니다.

권장 흐름:
1. BaekjoonHub 자동 업로드(수집)
2. `./scripts/import-bjh.sh <problem_id> <user_id> <source_dir> [platform]`
3. `archive/<platform>/<problem_id>/<user_id>/` 기준으로 PR
