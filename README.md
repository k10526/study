19.2.1.1.1 런타임 시맨틱: CreateDynamicFunction(constructor, newTarget, kind, args)

추상 연산인 CreateDynamicFunction은 인자인 constructor, newTarget, kind arg와 함께 호출 된다. constructor는 이 액션을 수행하는 생성자 함수고, newTarget은 new가 처음으로 적용된 생성자고, kind는 "일반" 도는 "제너레이터"중 하나이고, arg는 constructor에 전달된 실제 인자값을 포함하는 리스트이다. 다음 단계를 따른다.

1. 만약 newTarget이 undefined면, newTarget은 constructor이다.
2. 만약 kind가 "일반" 이라면
  a. goal를 문법기호 FunctionBody로 둔다.
  b. parameterGoal를 문법기호 FormalParameters로 둔다.
  c. fallbackProto는 "%FunctionPrototype%이다.
3. 그렇지 않으면
  a. goal를 문법기호 GeneratorBody로 둔다.
  b. parameterGoal를 문법기호 FormalParameters로 둔다.
  c. fallbackProto는 "%Generator%"이다.
4. argCount는 args의 요소 수이다.
5. P는 빈 문자열이다.
6. argCount = 0이면, bodyText는 빈 문자열 이다.
7. 그렇지 않고 argCount = 1이면 bodyText는 arg[0]이다.
8. 그렇지 않다면 argCount > 1
  a. firstArg는 arg[0]으로 둔다.
  b. P는 ?ToString(firstArg)로 둔다.
  c. k는 1로 둔다.
  d. k < argCount-1 동안 반복한다.
    i. nextArg를 args[k]로 둔다.
    ii. nextArgString를 ? ToString(nextArg)로 둔다.
    iii. P를 P의 이전값 문자열 ","(쉼표) 와 nextArgString을 연결한 결과 값으로 둔다.
    iv k를 1 증가한다.
  e. bodyText를 args[k]로 둔다.


