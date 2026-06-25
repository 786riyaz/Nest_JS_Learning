## 🔹 Basics (1–15)

### 1. What is NestJS?

NestJS is a progressive Node.js framework for building efficient, scalable, and maintainable server-side applications using TypeScript and inspired by Angular architecture.

### 2. Is NestJS part of the MERN stack?

No. MERN uses Express directly, whereas NestJS is a framework built on top of Express or Fastify.

### 3. Which language does NestJS primarily use?

TypeScript (JavaScript is also supported).

### 4. What design pattern does NestJS follow?

It follows **MVC + Dependency Injection + Modular Architecture**.

### 5. Which HTTP platforms does NestJS support?

Express (default) and Fastify.

### 6. What is a module in NestJS?

A module is a class annotated with `@Module()` that organizes related components like controllers and providers.

### 7. What is a controller?

Controllers handle incoming HTTP requests and return responses.

### 8. What is a provider?

Providers are injectable classes (services, repositories, helpers) that contain business logic.

### 9. What decorator defines a controller?

`@Controller()`

### 10. What decorator defines a module?

`@Module()`

### 11. What decorator defines a service?

`@Injectable()`

### 12. What is Dependency Injection?

A design pattern where dependencies are provided externally instead of being created inside the class.

### 13. Why is NestJS preferred over Express?

Better structure, scalability, built-in DI, TypeScript support, testing utilities.

### 14. What is the entry file of a NestJS app?

`main.ts`

### 15. How do you start a NestJS application?

```bash
npm run start
```

---

## 🔹 Controllers & Routing (16–30)

### 16. How do you define a GET route?

```ts
@Get()
```

### 17. How do you access route parameters?

```ts
@Param('id')
```

### 18. How do you access query parameters?

```ts
@Query('page')
```

### 19. How do you access request body?

```ts
@Body()
```

### 20. How do you handle POST requests?

```ts
@Post()
```

### 21. How do you return JSON?

NestJS automatically serializes returned objects to JSON.

### 22. Can one controller have multiple routes?

Yes.

### 23. How do you set a global prefix?

```ts
app.setGlobalPrefix('api');
```

### 24. How do you inject a service into a controller?

Via constructor injection.

### 25. Can controllers call other controllers?

No, they should communicate via services.

### 26. How do you send HTTP status codes?

```ts
@HttpCode(201)
```

### 27. How do you access request object?

```ts
@Req()
```

### 28. How do you access response object?

```ts
@Res()
```

### 29. Is using `@Res()` recommended?

No, it bypasses NestJS response handling.

### 30. What is RESTful routing?

Designing APIs using HTTP methods and resource-based URLs.

---

## 🔹 Providers & Services (31–45)

### 31. What is a service in NestJS?

A provider that contains business logic.

### 32. Why use services?

To keep controllers thin and logic reusable.

### 33. How do you register a service?

Add it to `providers` array in module.

### 34. Are services singleton by default?

Yes.

### 35. Can a service inject another service?

Yes.

### 36. What is scope in providers?

Defines lifecycle: Singleton, Request, Transient.

### 37. What is `@Inject()` used for?

Inject custom providers.

### 38. What is a custom provider?

A provider defined using `useClass`, `useValue`, `useFactory`.

### 39. When to use `useFactory`?

When dynamic logic is required.

### 40. Can providers be async?

Yes.

### 41. What is circular dependency?

When two providers depend on each other.

### 42. How to resolve circular dependency?

Using `forwardRef()`.

### 43. Can services access request data?

Only with request-scoped providers.

### 44. What is provider token?

A unique identifier used for DI.

### 45. Can providers be exported?

Yes, using `exports` in module.

---

## 🔹 Middleware, Guards, Pipes, Interceptors (46–70)

### 46. What is middleware?

Functions executed before request reaches controller.

### 47. How to create middleware?

Implement `NestMiddleware`.

### 48. What is a guard?

Used for authorization.

### 49. Example use of guard?

JWT authentication.

### 50. What decorator applies guard?

```ts
@UseGuards()
```

### 51. What is a pipe?

Used for validation and transformation.

### 52. Common built-in pipe?

`ValidationPipe`

### 53. What library is used for validation?

`class-validator`

### 54. What decorator validates DTO?

```ts
@IsString()
```

### 55. What is DTO?

Data Transfer Object.

### 56. What is an interceptor?

Wraps request/response lifecycle.

### 57. Use cases of interceptor?

Logging, response transformation, caching.

### 58. What decorator applies interceptor?

```ts
@UseInterceptors()
```

### 59. Difference between middleware and interceptor?

Middleware runs before routing, interceptor wraps execution.

### 60. Can pipes be global?

Yes.

### 61. Can guards be global?

Yes.

### 62. Can interceptors be global?

Yes.

### 63. What is exception filter?

Handles exceptions globally or locally.

### 64. Built-in exception class?

`HttpException`

### 65. How to throw exception?

```ts
throw new BadRequestException();
```

### 66. Can filters be custom?

Yes.

### 67. Where are filters used?

Controllers or globally.

### 68. What is execution context?

Provides request details to guards/interceptors.

### 69. Can pipes modify data?

Yes.

### 70. Are pipes synchronous or async?

Both.

---

## 🔹 Database & Mongoose (71–85)

### 71. Does NestJS support MongoDB?

Yes, commonly via Mongoose.

### 72. NestJS Mongoose package?

`@nestjs/mongoose`

### 73. What is Schema in Mongoose?

Blueprint for MongoDB documents.

### 74. What decorator defines schema?

```ts
@Schema()
```

### 75. What decorator defines property?

```ts
@Prop()
```

### 76. How to inject model?

```ts
@InjectModel()
```

### 77. What is Repository pattern?

Abstraction over database operations.

### 78. Difference between MERN and NestJS DB handling?

NestJS uses structured modules and DI.

### 79. Can NestJS use TypeORM?

Yes.

### 80. Can NestJS use Prisma?

Yes.

### 81. Where should DB logic reside?

Services or repositories.

### 82. Can you use raw MongoDB driver?

Yes.

### 83. How to handle DB connection?

Via async module configuration.

### 84. Can multiple DBs be used?

Yes.

### 85. Is transaction supported?

Yes (depends on ORM).

---

## 🔹 Advanced & Production (86–100)

### 86. What is Fastify?

A high-performance alternative to Express.

### 87. How to enable Fastify?

Use `NestFastifyApplication`.

### 88. What is Swagger in NestJS?

API documentation tool.

### 89. Swagger package?

`@nestjs/swagger`

### 90. What is ConfigModule?

Manages environment variables.

### 91. How to secure secrets?

Using `.env` files and ConfigModule.

### 92. What is rate limiting?

Restricting API requests per user.

### 93. NestJS rate limit package?

`@nestjs/throttler`

### 94. How to handle file uploads?

Using Multer.

### 95. What is CQRS?

Command Query Responsibility Segregation.

### 96. Does NestJS support microservices?

Yes.

### 97. Message brokers supported?

Kafka, RabbitMQ, Redis, NATS.

### 98. How to test NestJS apps?

Using Jest.

### 99. What is e2e testing?

Testing complete request lifecycle.

### 100. Why NestJS is enterprise-ready?

Strong architecture, DI, testing, scalability.