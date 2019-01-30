---
title: Advanced TypeScript features
date: "2019-01-30"
---

There are quite a few interesting features in TypeScript which are either new to the language itself or I have never heard about them before. I list a couple of them in this post. It is mostly about type inference and conditional types.

## Automatic type inference with the "in" operator

Let's say, we have a value that has a union type. Here, our pet may be either of type `Bird` or `Fish`.

```typescript
interface Bird {
  fly();
}

interface Fish {
  swim();
}

function getSmallPet(): Fish | Bird {
  // ...
}

let pet = getSmallPet();
```

If we want to know specifically whether we have a `Fish`, I would have normally used a [type guard](https://www.typescriptlang.org/docs/handbook/advanced-types.html).

```typescript
function isFish(pet: Fish | Bird): pet is Fish {
  return (<Fish>pet).swim !== undefined;
}

if (isFish(pet)) {
  pet.swim();
} else {
  pet.fly();
}
```

Now, I found out that it is also possible to make use of the JavaScript's "in" operator. There is no need for the type guard function, it looks really clean and the typescript compiler is also happy. :)

```typescript
if ("swim" in pet) {
  pet.swim();
} else {
  pet.fly();
}
```
