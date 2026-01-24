# 📁 Project Structure

```
src/
 ├── app.module.ts
 ├── main.ts
 └── users/
     ├── users.module.ts
     ├── users.controller.ts
     ├── users.service.ts
     ├── user.schema.ts
     └── dto/create-user.dto.ts
```

---

## 1️⃣ `main.ts`

```ts
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  app.setGlobalPrefix('api');
  await app.listen(3000);
}
bootstrap();
```

---

## 2️⃣ `app.module.ts`

```ts
import { Module } from '@nestjs/common';
import { MongooseModule } from '@nestjs/mongoose';
import { UsersModule } from './users/users.module';

@Module({
  imports: [
    MongooseModule.forRoot('mongodb://127.0.0.1:27017/nest_crud'),
    UsersModule,
  ],
})
export class AppModule {}
```

---

## 3️⃣ `users/user.schema.ts`

```ts
import { Prop, Schema, SchemaFactory } from '@nestjs/mongoose';
import { Document } from 'mongoose';

export type UserDocument = User & Document;

@Schema({ timestamps: true })
export class User {
  @Prop({ required: true })
  name: string;

  @Prop({ required: true, unique: true })
  email: string;

  @Prop()
  age: number;
}

export const UserSchema = SchemaFactory.createForClass(User);
```

---

## 4️⃣ `users/dto/create-user.dto.ts`

```ts
import { IsEmail, IsNumber, IsString } from 'class-validator';

export class CreateUserDto {
  @IsString()
  name: string;

  @IsEmail()
  email: string;

  @IsNumber()
  age: number;
}
```

---

## 5️⃣ `users/users.service.ts`

```ts
import { Injectable, NotFoundException } from '@nestjs/common';
import { InjectModel } from '@nestjs/mongoose';
import { Model } from 'mongoose';
import { User, UserDocument } from './user.schema';
import { CreateUserDto } from './dto/create-user.dto';

@Injectable()
export class UsersService {
  constructor(
    @InjectModel(User.name)
    private userModel: Model<UserDocument>,
  ) {}

  create(dto: CreateUserDto) {
    return this.userModel.create(dto);
  }

  findAll() {
    return this.userModel.find();
  }

  findOne(id: string) {
    const user = this.userModel.findById(id);
    if (!user) throw new NotFoundException('User not found');
    return user;
  }

  delete(id: string) {
    return this.userModel.findByIdAndDelete(id);
  }
}
```

---

## 6️⃣ `users/users.controller.ts`

```ts
import { Controller, Get, Post, Delete, Param, Body } from '@nestjs/common';
import { UsersService } from './users.service';
import { CreateUserDto } from './dto/create-user.dto';

@Controller('users')
export class UsersController {
  constructor(private readonly usersService: UsersService) {}

  // 1️⃣ CREATE
  @Post()
  create(@Body() dto: CreateUserDto) {
    return this.usersService.create(dto);
  }

  // 2️⃣ READ ALL
  @Get()
  findAll() {
    return this.usersService.findAll();
  }

  // 3️⃣ READ BY ID
  @Get(':id')
  findOne(@Param('id') id: string) {
    return this.usersService.findOne(id);
  }

  // 4️⃣ DELETE
  @Delete(':id')
  delete(@Param('id') id: string) {
    return this.usersService.delete(id);
  }
}
```

---

## 7️⃣ `users/users.module.ts`

```ts
import { Module } from '@nestjs/common';
import { MongooseModule } from '@nestjs/mongoose';
import { UsersController } from './users.controller';
import { UsersService } from './users.service';
import { User, UserSchema } from './user.schema';

@Module({
  imports: [
    MongooseModule.forFeature([
      { name: User.name, schema: UserSchema },
    ]),
  ],
  controllers: [UsersController],
  providers: [UsersService],
})
export class UsersModule {}
```

---

# 🚀 API Endpoints Summary

| Method | Endpoint         | Description    |
| ------ | ---------------- | -------------- |
| POST   | `/api/users`     | Create user    |
| GET    | `/api/users`     | Get all users  |
| GET    | `/api/users/:id` | Get user by ID |
| DELETE | `/api/users/:id` | Delete user    |

---

# 🧪 Sample POST Body

```json
{
  "name": "Riyaz",
  "email": "riyaz@gmail.com",
  "age": 25
}
```

---

# 🧠 Interview Notes (Important)

* Uses **Mongoose + DI**
* DTO validation ready
* Clean module separation
* Production-friendly structure