# NoticeBoard 개인프로젝트

- 게시판과 oauth기능을 만들며, 백엔드와 nest에 대해 공부하는 repository입니다.

## 개발 기간

- 최소 1주 ~ 최대 2주로 생각하고 있습니다.

---

## nest

### decorator

- nest에선 데코레이터를 이용하여 get, post, delete등 rest api요청을 처리하고, dto를 따로 dto 이름이 들어간 파일을 만들어 선언해 데코레이터 옆에 정의 해준다.

### controler

- controler는 만들 때 모듈에 선언해주어서 작동한다.
- 콘솔 명령어로 controler를 만들 수 있다.

### provider

- provider 역시 콘솔 명령어로 만들 수 있다.
- provider는 DI 할 수 있다. 개체 인스턴스를 연결하는 기능이다.
- provider는 일반적으로 애플리케이션 생명주기와 같은 스코프를 갖고 있다

### module

```js
import { Module } from '@nestjs/common';
import { CatsController } from './cats.controller';
import { CatsService } from './cats.service';

@Module({
  controllers: [CatsController],
  providers: [CatsService],
})
export class CatsModule {}
```

이런식으로 만들고 imports[]안에다가 넣어 붙이면 된다. 전역적으로 쓰고 싶으면 global 데코레이터 쓰면 된다. 순환종속성으로 인해 공급자를 주입할 수 없다.

### middleware

- nest 만에 middleware는 없는듯 하다. express꺼 갖다 쓴다. 근데 decorator 잘 활용하면 middleware 쓸일 없을지도?

```js
import { Injectable, NestMiddleware } from '@nestjs/common';
import { Request, Response, NextFunction } from 'express';

@Injectable()
export class LoggerMiddleware implements NestMiddleware {
  use(req: Request, res: Response, next: NextFunction) {
    console.log('Request...');
    next();
  }
}
```

middleware파일 따로 만들어서 거기서 middleware을 생성한다.

```js
import {
  Module,
  NestModule,
  RequestMethod,
  MiddlewareConsumer,
} from '@nestjs/common';
import { LoggerMiddleware } from './common/middleware/logger.middleware';
import { CatsModule } from './cats/cats.module';

@Module({
  imports: [CatsModule],
})
export class AppModule implements NestModule {
  configure(consumer: MiddlewareConsumer) {
    consumer
      .apply(LoggerMiddleware)
      .forRoutes({ path: 'cats', method: RequestMethod.GET });
  }
}
```

module에서 middleware을 사용 한다.
