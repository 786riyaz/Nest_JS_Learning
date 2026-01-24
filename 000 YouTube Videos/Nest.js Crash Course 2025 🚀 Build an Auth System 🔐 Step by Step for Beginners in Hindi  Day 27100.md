Nest.js Crash Course 2025 🚀| Build an Auth System 🔐 Step by Step for Beginners in Hindi | Day 27/100
Coder's Gyan
https://www.youtube.com/watch?v=KMg_Qg0WCds&t=63s


[00:00:00] - Introduction: Scalable Backend Thinking
[00:00:20] Express vs. NestJS Comparison
[00:00:53] What and Why NestJS
[00:06:04] Website and Features Overview
[00:09:01] - Project Plan: LMS API
[00:09:11] User Auth and JWT Scheme
[00:09:57] Courses CRUD and Security
[00:11:17] Stack: Nest, MongoDB, Postman
[00:13:27] - Nest CLI Install and Project Setup
[00:14:06] CLI Help and Commands
[00:16:22] New Project Name and Setup
[00:19:12] Dev Server Run and Hello World
[00:19:20] - NestJS Basics: Architecture
[00:20:10] Requests Understanding the Flow
[00:22:40] The Concept of Modules
[00:24:04] Decorators and Services
[00:26:01] Controllers and @Get
[00:29:06] DI and AppModule
[00:31:48] main.ts and Port 3000
[00:33:00] - Auth Module and Register Route
[00:34:22] Module Generation and Register
[00:37:05] Controller Generation and Prefix
[00:40:26] POST /auth/register Skeleton
[00:43:02] - Service Generation and DI
[00:43:44] AuthService Generation and Provider
[00:45:41] Service Inject into Controller
[00:47:34] TypeScript Shorthand Constructor
[00:49:06] - Register Logic and User Module
[00:49:38] Registration Steps Outline
[00:50:44] Creating UserModule and Service
[00:53:26] Export/Import Providers
[00:55:11] Calling UserService from AuthService
[00:58:02] - DTOs and @Body Handling
[00:59:01] Understanding the DTO Concept
[01:01:05] Creating the RegisterDto Class
[01:02:49] Sending JSON from Postman
[01:03:21] Logging and Passing DTOs
[01:06:41] Password Hashing and Mongo Setup
[01:06:53] Installing and Hashing bcrypt
[01:11:12] Running Mongo from Docker
[01:13:17] Installing @nestjs/mongoose
[01:14:08] MongooseModule.forRoot Config
[01:16:18] ConfigModule and .env Load
[01:18:13] - User Schema and Model Injection
[01:19:10] Creating Schema from Decorators
[01:23:04] Required/unique and Default Roles
[01:26:06] Schema Register from forFeature
[01:27:40] InjectModel and Create Calls
[01:32:44] Record Verification in Compass
[01:35:03] - Duplicate Email Handling
[01:36:48] Try/Catch and Error Log
[01:38:32] Identifying 11000 Codes
[01:39:12] Throwing ConflictExceptions
[01:42:28] Magic Numbers as Constants Creating
[01:43:53] - JWT Token Generation and Config
[01:44:51] Installing @nestjs/jwt
[01:50:34] JwtModule Register and Secret
[01:54:43] Env Access Issue and Fix
[01:55:40] Token Payload and Return Format
[01:57:26] - Validation Pipe and DTO Validation
[01:59:49] Class-validator/transformer Install
[02:00:31] Global ValidationPipe Enabled
[02:02:06] Applying Decorators to DTOs
[02:03:42] 400 Bad Request Demo
[02:07:56] - Protected Routes: AuthGuard
[02:09:37] Guard Concept and Flow
[02:11:16] AuthGuard code and token extraction
[02:14:48] jwtService.verify and request.user
[02:19:09] Applying Guard to /auth/profile
[02:24:41] Token expiration demo and filtering
[02:27:45] - Courses Resource Scaffold
[02:28:44] Nest g resource courses
[02:30:29] Controller routes and methods
[02:31:34] Create/Update DTO placeholders
[02:33:55] - Course Schema and create
[02:34:38] Creating CourseSchema fields
[02:35:11] forFeature and InjectModel
[02:35:32] Create method implementation
[02:36:56] Create with Postman Test
[02:37:31] - Role-Based Authorization
[02:38:06] AuthGuard on Create Course
[02:39:21] Creating the Roles Decorator
[02:41:25] RolesGuard Implementation and Refactor
[02:48:52] Debug: Roles in Token Payload
[02:50:00] Incrementing the Token TTL and Testing 403
[02:53:21] Success with Admin Token
[02:54:21] - Rest of CRUD and Assignment
[02:55:02] Dynamic :id Param Access
[02:57:44] FindOne Implementation and Test
[02:58:36] Update Hint from PartialType
[02:59:18] Hints for the Delete Method
[03:00:01] - Conclusion and Further Learnings
[03:00:07] DI Deep-Dive Video Reference