---
title: Some new TypeScript features
date: "2019-01-30"
---

## No need for type guards
Using the JavaScript "in" operator for automatic type inference. There is no need for type guard functions.

```typescript
interface Admin {
    id: string;
    role: string;
}

interface User {
    email: string;
}

function redirect(user: Admin | User) {
    if ("role" in user) {
        redirectHome(user.email)
    } else {
        redirectAdminView(user.role)
    }
}
```
