---
title: typescript에서 enum이 컴파일되면 어떻게 될까
date: "2020-03-01T00:00:00.000Z"
template: "post"
draft: false
slug: "typescript-enum-compile"
category: "Typescript"
tags:
  - "Typescript"
  - "Enum"
  - "Compile"
description: "typescript에서 enum이 컴파일되면 어떻게 될까"
socialImage: "/media/social-image.png"
---

typescript에서 enum이 컴파일되면 어떻게 될까

[Typescript playground](http://www.typescriptlang.org/play)에서 쉽게 확인할 수 있다.

```typescript
enum Errors {
  EvalError,
  RangeError,
  ReferenceError
}
```

```typescript
"use strict";
var Errors;
(function (Errors) {
    Errors[Errors["EvalError"] = 0] = "EvalError";
    Errors[Errors["RangeError"] = 1] = "RangeError";
    Errors[Errors["ReferenceError"] = 2] = "ReferenceError";
})(Errors || (Errors = {}));
```
