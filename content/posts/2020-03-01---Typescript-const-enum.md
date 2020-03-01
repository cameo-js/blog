---
title: Typescript에서 const enum이 컴파일되면 어떻게 될까
date: "2020-03-01T00:00:00.000Z"
template: "post"
draft: false
slug: "typescript-const-enum"
category: "Typescript"
tags:
  - "Typescript"
  - "Enum"
  - "Performance"
description: "Typescript에서 const enum이 컴파일되면 어떻게 될까"
socialImage: "/media/social-image.png"
---

[typescript에서 enum이 컴파일되면 어떻게 될까](https://cameo.lamplit.co/posts/Typescript-enum-compile)는 확인했는데 `const enum`이 컴파일되면 어떻게 될까.

마찬가지로 [Typescript playground](http://www.typescriptlang.org/play/?ssl=1&ssc=1&pln=5&pc=2#code/MYewdgzgLgBApmArgWxgUQE4ZBiMDeAUDOgG4CGANpthgLwBEaF1WODANMTAErlgBzODRyM+g4WwyduPOADM4GBMEm0xCpSrXtCAXyA)에서 쉽게 확인할 수 있다.

```typescript
const enum Errors {
  EvalError,
  RangeError,
  ReferenceError,
}
```

```typescript
"use strict";
```

하지만 결과를 보면 enum과는 다르게 const enum은 컴파일된 코드가 사라진 걸 볼 수 있다.

```typescript
const enum Errors {
  EvalError,
  RangeError,
  ReferenceError,
}

console.log(Errors.EvalError);
```

```typescript
"use strict";

console.log(0 /* EvalError */);
```

enum을 사용하는 코드를 추가하니 0이라는 값이 그대로 들어간 것을 볼 수 있다.

[typescript의 문서에 정의된 것처럼](https://www.typescriptlang.org/docs/handbook/enums.html#const-enums)
> In most cases, enums are a perfectly valid solution. However sometimes requirements are tighter. To avoid paying the cost of extra generated code and additional indirection when accessing enum values, it’s possible to use const enums. Const enums are defined using the const modifier on our enums:

const enum은 코드와 변수에 접근하는 비용을 줄여줘 성능 향상에 도움을 준다.