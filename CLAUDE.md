# CLAUDE.md — my-devlog

이 파일은 `my-devlog` 저장소에서 Claude Code가 따를 규칙과 상호작용 방식을 정의한다.

## 프로젝트 소개
- 목적: **Astro를 학습하면서 만들어 가는 개인 데브로그 블로그.** 공부한 내용과 작업하면서 느낀 점을 기록한다.
- 스택: Astro `^6.1.1`, TypeScript, Node `>=22.12.0`.
- 구조(현재):
  - `src/pages/` — 라우트(`index.astro`, `about.astro`)
  - `src/layouts/BaseLayout.astro` — 공용 레이아웃
  - `public/` — 정적 자산
  - `astro.config.mjs`, `tsconfig.json`

## 상호작용 원칙 (가장 중요)
1. **응답 언어는 한국어 기본.** 코드·식별자·명령어·에러 메시지는 영어 원문을 유지한다.
2. **코드 수정은 명시적 요청이 있을 때만.**
   - 사용자가 "수정해줘 / 고쳐줘 / 바꿔줘 / 적용해줘" 같은 **명시적 편집 지시**를 한 경우에만 `Edit`·`Write` 등 파일 편집 도구를 사용한다.
   - 그 외의 질문(예: "이거 왜 안 돼?", "이건 뭐야?", "어떻게 하면 돼?")에는 **파일을 건드리지 말고** 설명 + 코드 예시(코드 블록) 형태로만 답한다.
   - 애매하면 편집하지 말고 먼저 물어본다.
3. **학습 도우미 톤.** 결론만 툭 던지지 말고 "왜 그렇게 되는지" 맥락을 함께 설명한다. 단, 불필요한 사족·반복은 피한다.
4. **Astro 공식 문서(https://docs.astro.build)를 1순위 근거로 삼는다.** 확신이 없는 부분은 추측하지 말고 "확실하지 않다"고 밝힌다.
5. 보안·개인정보·외부 서비스 자동 호출 등 파괴적/비가역 작업은 먼저 확인을 구한다.

## 코딩 / 파일 규칙
- 디렉터리: Astro 표준을 따른다.
  - 라우트 → `src/pages/`
  - 레이아웃 → `src/layouts/`
  - 컴포넌트 → `src/components/` (필요 시)
  - 콘텐츠 컬렉션 → `src/content/` (필요 시)
- 파일명
  - `.astro` 레이아웃/컴포넌트: **PascalCase** (`BaseLayout.astro`)
  - 페이지 파일: 소문자 kebab-case 또는 단수형 (`about.astro`, `blog-post.astro`)
- 페이지는 가급적 `BaseLayout`으로 감싸 `<html>`/`<head>`/`<title>` 일관성을 유지한다.
- 들여쓰기·따옴표 등은 **기존 파일 스타일을 따라간다.** (현재는 탭 들여쓰기 혼용 중)

## 커밋 메시지 규칙
**Conventional Commits** 형식을 사용한다.

```
type(scope): subject
```

- 주요 type
  - `feat` — 새 기능/페이지/컴포넌트 추가
  - `fix` — 버그 수정
  - `docs` — 문서(README, CLAUDE.md 등)
  - `style` — 포맷팅·공백 등 동작에 영향 없는 변경
  - `refactor` — 동작은 그대로, 구조만 개선
  - `chore` — 빌드 설정, 의존성 업데이트 등
  - `post` — 블로그 글(게시물) 추가/수정 (프로젝트 정의)
- `scope`는 선택. 예: `layout`, `pages`, `config`.
- `subject`는 한국어 허용, 72자 이내 권장, 마침표 생략.
- 예시
  - `feat(layout): BaseLayout에 meta description prop 추가`
  - `fix(pages): index에 BaseLayout 적용 누락 수정`
  - `post: Astro 슬롯 학습 노트 작성`

## 실행 명령 참고
| 명령 | 설명 |
| --- | --- |
| `npm run dev` | 개발 서버 실행 (`localhost:4321`) |
| `npm run build` | 프로덕션 빌드 (`./dist/`) |
| `npm run preview` | 빌드 결과 로컬 미리보기 |
| `npm run astro ...` | Astro CLI (`astro add`, `astro check` 등) |

## TODO (나중에 추가)
- 블로그 포스트 작성 톤·형식 가이드
- 배포 환경(Vercel / Netlify / GitHub Pages 등) 관련 규칙
- 콘텐츠 컬렉션(`src/content/`) 도입 시 스키마 규칙
