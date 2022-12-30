# :star: 마크다운이란?

## :bulb: 개요

- 2004년 존 그루버가 만든 텍스트 기반의 가벼운 마크업 언어
  - Markdown is a **text-to-HTML conversion tool** for web writers.
  - Markdown allows you to write using an **easy-to-read, easy-to-write plain text format**, then convert it to structually valid XHTML (or HTML).
  - Thus, "Markdown" is two things:
    1. **a plain text formatting syntax**
    2. a software tool, written in Perl, **that converts the plain text formatting to HTML.**
  - The overriding **design goal for Markdown's formatting syntax is to make it as readable as possible.**

## :bulb: 특징

- 워드프로세서(한글/MS word)는 다양한 서식과 구조를 지원하며 문서에 즉각적으로 반영되지만 다른 프로그램으로 호환에 제약이 되며, 워드프로세서 상의 기능을 활용해야 함
- 마크다운은 최소한의 문법으로 구성되어 있으며 순수 텍스트로 작성 가능함
- 마크다운은 단순 텍스트 문법으로 내용을 작성하며, 다양한 환경에서 변환하여 보임
  - 다양한 text editor, 웹 환경 등에서 모두 지원(HTML 변환)

## :bulb: 활용 예시

- README.md
  - 오픈소스의 공식 문서를 작성하거나 개인 프로젝트의 프로젝트 소개서로 활용
  - 혹은 모든 페이지에 README.md를 넣어 문서를 바로 볼 수 있도록 활용
  - Github 등의 사이트에서는 파일명이 README.md인 것을 모두 보여줌
- 정적사이트생성기(Static site generator) 기반 블로그
  - Jekyll, Gatsby, Hugo, Hexo 등으로 작성된 마크다운을 HTML, CSS, JS 파일 등으로 변환하고, Github pages 기능을 통해 무료 호스팅이 가능함
- 마크다운 기반 SW
  - Jupyter notebook에는 별도의 마크다운 셀이 있어 데이터 분석 등을 하는 과정에서 프로젝트 내용과 분석 결과를 정리 가능함
  - Notion과 같은 메모/노트 필기 SW 역시 마크다운 기반 문서 작성을 기본으로 함

## :bulb: 마크다운 문법

- Heading: 문서의 제목이나 소제목
  - #의 개수에 따라 대응되는 수준(Heading level)이 있으며, h1~h6까지 표현 가능
  - 문서의 구조를 위해 작성되며 글자 크기를 조절하기 위해 사용되어서는 안됨
  - 예시
    # heading 1
    ## heading 2
    ### heading 3
    #### heading 4
    ##### heading 5
    ###### heading 6

- List 목록
  - 순서가 있는 리스트(ol)와 순서가 없는 리스트(ul)로 구성
  - ol: 숫자(1.) / ul: 하이픈, asterisk(\*)
  - Tab으로 하위 항목으로 구성할 수 있음
  - 예시
    - 모닝 루틴
      1. 이불 정리
      2. 스트레칭
      3. 유산균, 양배추즙 마시기
    - 아침 메뉴
      - 요거트+블루베리
      - 모닝커피

- Fenced Code block: 코드 블록
  - 코드 블록은 backtick 기호 3개를 활용하여 작성(\`\`\` \`\`\`)
  - 코드 블록에 특정 언어를 명시하면 Syntax Highlighting 적용 가능
  - 예시
    ```
    중요한 것은 꺾이지 않는 마음!
    ```

- Inline Code block: 코드 블록
  - 코드 블록은 backtick 기호 1개를 인라인에 활용하여 작성(\`\`)
  - 예시
    - 이것은 `예시`입니다.

- link: 링크
  - \[문자열](url)을 통해 링크 작성 가능
  - 특정 파일을 포함하여 연결할 수도 있음
  - 예시
    - [네이버](https://www.naver.com/)

- image: 이미지
  - \!\[문자열](url)을 통해 이미지를 사용 가능
  - 특정 파일을 포함하여 연결할 수도 있음
  - ./ : 지금 폴더(디렉토리)
  - b/ : b 폴더(디렉토리)
  - 예시  
    ![블랭키](./블랭키.png)

- Blockquotes: 인용문
  - \>로 인용문을 작성
    > There is nothing noble in being superior to your fellow men.  
    True nobility lies in being superior to your former self.  
    남보다 뛰어나다는 것은 고결한 것이 아니다.  
    진정한 고결함은 예전의 자신보다 뛰어난 데 있다.  
    \- 어니스트 헤밍웨이-

- 텍스트 강조
  - 굵게(bold), 기울임(italic)을 통해 특정 글자들을 강조
  - \*\* \*\*(bold), \* \*(italic)
  - 예시
    - **글씨를 굵게 강조합니다.**
    - *글씨를 기울여 강조합니다.*

- 수평선
  - 3개 이상의 asterisks(\*\*\*), dashes(---), underscores(\_\_\_)
  ***
  ---
  ___

- 취소선
  - 2개의 \~\~(물결표)를 이용해 취소선 사용 가능
  - 예시
    - ~~취소선입니다.~~

- 밑줄
  - \<u>\</u> 태그를 사용해 밑줄 사용 가능
  - 예시
    - <u>밑줄을 쳐주세요</u>

## :bulb: 마크다운 관련 참고자료
- [Github Flavored Markdown](https://github.github.com/gfm/)
- [Mastering Markdown](https://guides.github.com/features/mastering-markdown)
- [Markdown Guide](https://www.markdownguide.org)

## :bulb: Technical writing 관련 참고자료
- [백엔드 개발자를 꿈꾸는 학생 개발자들에게](https://d2.naver.com/news/3435170)
- [Google Technical Writing](https://developers.google.com/tech-writing)
- [Technical writing conference](https://engineering.linecorp.com/ko/blog/write-the-docs-prague-2018-recap/)