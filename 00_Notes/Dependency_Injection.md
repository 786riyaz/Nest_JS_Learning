## Dependency Injection (DI) in NestJS

**Dependency Injection (DI)** in NestJS is a **design pattern** where a class does **not create its own dependencies**. Instead, those dependencies are **provided (injected) by the NestJS framework** at runtime.

NestJS has a **built-in Inversion of Control (IoC) container** that manages object creation, lifecycle, and dependency resolution.

---

## Why Dependency Injection is Important

In real-world applications (including MERN backends), DI provides:

* Loose coupling between components
* Better code maintainability
* Easier unit testing (mocking dependencies)
* Clear separation of concerns
* Scalable architecture

---

## Problem Without Dependency Injection

### ❌ Tight Coupling (Bad Practice)

```ts
class UsersService {
  private db = new DatabaseService(); // tightly coupled

  getUsers() {
    return this.db.findAll();
  }
}
```

Issues:

* Hard to replace `DatabaseService`
* Difficult to test
* Violates SOLID principles

---

## How NestJS Solves This Using DI

### ✅ With Dependency Injection (NestJS Way)

### 1️⃣ Create a Provider

```ts
@Injectable()
export class DatabaseService {
  findAll() {
    return ['User1', 'User2'];
  }
}
```

### 2️⃣ Inject the Dependency

```ts
@Injectable()
export class UsersService {
  constructor(private readonly db: DatabaseService) {}

  getUsers() {
    return this.db.findAll();
  }
}
```

NestJS automatically:

* Creates `DatabaseService`
* Injects it into `UsersService`
* Manages its lifecycle

---

## Role of `@Injectable()`

`@Injectable()` tells NestJS:

> “This class can be managed by the DI container and injected elsewhere.”

Without it, NestJS **cannot inject** the class.

---

## How DI Works Internally (High-Level)

1. App starts
2. NestJS scans modules
3. Providers are registered in IoC container
4. Dependencies are resolved via constructor injection
5. Single instance is shared (singleton by default)

---

## DI in Modules

```ts
@Module({
  providers: [UsersService, DatabaseService],
})
export class UsersModule {}
```

* Providers must be **registered in a module**
* Otherwise, NestJS cannot inject them

---

## Dependency Injection in Controllers

```ts
@Controller('users')
export class UsersController {
  constructor(private readonly usersService: UsersService) {}
}
```

Here:

* `UsersService` is injected automatically
* Controller does not create the service

---

## Provider Scope in NestJS

| Scope               | Description                   |
| ------------------- | ----------------------------- |
| Singleton (default) | One instance per application  |
| Request             | New instance per HTTP request |
| Transient           | New instance per injection    |

Example:

```ts
@Injectable({ scope: Scope.REQUEST })
```

---

## Custom Providers (Advanced DI)

### `useClass`

```ts
{
  provide: 'DB_SERVICE',
  useClass: DatabaseService,
}
```

### `useValue`

```ts
{
  provide: 'CONFIG',
  useValue: { env: 'dev' },
}
```

### `useFactory`

```ts
{
  provide: 'CONNECTION',
  useFactory: () => createConnection(),
}
```

---

## DI vs Express (MERN Comparison)

| Feature      | Express      | NestJS   |
| ------------ | ------------ | -------- |
| DI           | Manual       | Built-in |
| Architecture | Unstructured | Modular  |
| Testability  | Hard         | Easy     |
| Scalability  | Manual       | Native   |

---

## Interview-Friendly Definition

> **Dependency Injection in NestJS is a design pattern where the framework automatically provides required dependencies to a class using its IoC container, instead of the class creating them itself.**

---

## Common Interview Follow-Up Questions

* Why is DI important?
* Difference between DI and IoC?
* What happens if provider is not registered?
* What is constructor injection?
* How does NestJS resolve circular dependencies?