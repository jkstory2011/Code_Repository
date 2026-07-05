---
description: 카테고리와 주제를 받아 웹 검색 후 Vault_Storage에 지식 노트를 저장한다
argument-hint: <카테고리> <주제>
---

사용자가 `/research` 커맨드에 전달한 인자는 "$ARGUMENTS"이다. 첫 단어를 카테고리로, 나머지를 주제로 해석한다.

다음 절차를 따른다:

1. 카테고리가 다음 9개 중 하나와 정확히 일치하는지 확인한다: `3PL_물류`, `3PL_정산서`, `바이브코딩`, `코딩스킬`, `SNS컨텐츠`, `수익화`, `법인회사업무`, `개인회사업무`, `의류사업`. 일치하지 않으면 사용자에게 어느 카테고리인지 확인한다.
2. `g:\workspace\Vault_Storage\<카테고리>\` 폴더가 없으면 생성한다.
3. 그 폴더 안의 최근 노트 몇 개를 먼저 읽어, 이미 다룬 내용과 겹치지 않는 새로운 정보 위주로 웹 검색한다.
4. 검색 결과를 바탕으로 `g:\workspace\Vault_Storage\<카테고리>\<오늘날짜 YYYY-MM-DD>-<주제 요약>.md` 파일을 아래 형식으로 작성한다:

   ```markdown
   ---
   date: <오늘날짜 YYYY-MM-DD>
   category: <카테고리>
   sources: <검색에 사용한 출처 URL, 쉼표로 구분>
   ---

   # <주제>

   <검색 결과 요약 본문. 관련된 기존 노트가 있으면 [[노트파일명]] 형식의 위키링크로 연결한다.>
   ```

5. 노트 작성 후 아래 명령으로 그래프 데이터를 갱신한다:

   ```bash
   cd "g:/workspace/Vault_Storage" && node _dashboard/scan.js .
   ```

6. 변경된 파일(새 노트 + `_dashboard/graph-data.js`)을 커밋한다:

   ```bash
   cd "g:/workspace/Vault_Storage" && git add -A && git commit -m "지식 노트 추가: <카테고리>/<주제>"
   ```

7. 사용자에게 저장된 노트 경로를 알려준다.
