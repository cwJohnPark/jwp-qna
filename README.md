# 🚀 1단계 - 엔티티 매핑

## 요구 사항
- [x] Qna 서비스 엔티티 클래스 작성
- [x] @DataJpaTest를 사용하여 학습 테스트를 작성 - AnswerTest
- [x] @DataJpaTest를 사용하여 학습 테스트를 작성 - QuestionTest
- [x] @DataJpaTest를 사용하여 학습 테스트를 작성 - UserTest

# 🚀 2단계 - 연관 관계 매핑

## 요구 사항
- Question과 User의 다대일 양방향 연관관계 테스트
  - [x] 질문을 등록한 사용자를 조회할 수 있다.
  - [x] 사용자의 질문들을 조회할 수 있다.
  - [x] 질문의 작성자를 교체하면 이전 작성자는 해당 질문을 조회할 수 없다. 
 
- Answer와 Question의 다대일 양방향 연관관계 테스트
  - [x] 답변 질문들을 조회할 수 있다.
  - [x] 질문에 등록된 답변들을 조회할 수 있다.
  - [x] 답변의 질문을 교체하면 이전 질문의 해당 답변은 조회할 수 없다.

- Answer와 User의 다대일 양방향 연관관계 테스트
  - [x] 답변을 등록한 사용자를 조회할 수 있다.
  - [x] 사용자가 등록한 답변들을 조회할 수 있다.
  - [x] 답변의 작성자를 교체하면 이전 작성자는 해당 답변을 조회할 수 없다. 

# 🚀 3단계 - 질문 삭제하기 리팩터링

## 기능 요구 사항
- [x] 질문 데이터 삭제는 칼럼의 삭제 상태(deleted - boolean type)로 표현된다.
- [x] 질문은 로그인 사용자와 작성자가 같은 경우 삭제할 수 있다.
- [x] 질문은 답변이 없는 경우 삭제가 가능하다.
- [ ] 질문과 답변의 모든 작성자가 동일할 경우 삭제가 가능하다.
- [ ] 질문자와 답변자가 다른 경우 답변을 삭제할 수 없다.
- [ ] 질문을 삭제할 때 답변 또한 삭제돼야 한다.
- [ ] 답변 삭제는 삭제 상태(deleted)를 변경한다.
- [ ] 질문과 답변 삭제 이력에 대한 정보를 DeleteHistory에 저장한다

## 프로그래밍 요구 사항
- `qna.service.QnaService`의 `deleteQuestion()`는 질문 삭제 기능을 구현한 코드이다. 
- `deleteQuestion()` 메서드는 단위 테스트하기 어려운 코드와 단위 테스트 가능한 코드가 섞여 있다.
- 단위 테스트하기 어려운 코드와 단위 테스트 가능한 코드를 분리해 단위 테스트 가능한 코드에 대해 단위 테스트를 구현한다.
- 리팩터링을 완료한 후에도 src/test/java 디렉터리의 qna.service.QnaServiceTest의 모든 테스트가 통과해야 한다.
