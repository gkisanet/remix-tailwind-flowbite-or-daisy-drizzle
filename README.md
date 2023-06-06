# Remix-tailwind-flowbite-or-daisyui-drizzle

## 설치준비

- remix.config.js에서 tawilwind 설정\
- tailwind.config.ts에서 content 확장자 지정
- app폴더에 tailwind.css 디렉티브 설정
- root.tsx 에 컴파일된 tailwind.css 불러오기
- styles 폴더위치와 package.json의 tailwindcss 커맨드 조합 추가 설명

## Setup Routes Gen

authentication pages & protected routes 설정

> - \_index.tsx - app main route
> - auth.tsx - authentication page(s) layout
> - auth.sign-in.tsx - page where we are going to log in
> - auth.sign-up.tsx - page where we will create a new account
> - protected.tsx - protected page(s) layout, and we are going to add protection to ensure that you can only access it if you have a session
> - protected.\_index.tsx - main route of the protected pages and in this article it is where we will see the user information and we will log out

## setup Drizzle ORM

- server.schema 설정
- db:migrations 스크립트 추가

## Domain Functions

```sh
npm install zod domain-functions argon2
```

- zod 역할
  - schema validation
- domain function
  - 컨트롤러에서 비즈니스 로직을 분리한다라..
  - https://github.com/seasonedcc/domain-functions
- argon2

  - hash, verify

- Type safe ? Schema Validation?

  - 컴파일 시점에서 타입을 검사한다..
  - zod로 response 값을 스키마 에러 검사
  - https://mugglim.tistory.com/entry/Schema-Validation-Layer

- authSchema.ts 에 form validation, domain functions에 사용할 스키마 지정.

- account.server.ts 에 function 정의

## Resuable components

재사용할 컴포넌트를 만들기 (iInput, Button)

```sh
npm install remix-validated-form @remix-validated-form/with-zod
```

## Authentication setup

```sh
npm install remix-auth remix-auth-form
```

튜토리얼에서는 formstrategy 를 사용하는데, 프로젝트에서는 oauth2전략을 사용해보기를!

- [Strategy 리스트](https://github.com/sergiodxa/remix-auth/discussions/111)

- 세션을 저장할 스토리지 만들기
  - storage.server.ts

## Creating the app pages

- main route

- [Remix Docs](https://remix.run/docs)

## Development

From your terminal:

```sh
npm run dev
```

This starts your app in development mode, rebuilding assets on file changes.

## Deployment

First, build your app for production:

```sh
npm run build
```

Then run the app in production mode:

```sh
npm start
```

Now you'll need to pick a host to deploy it to.

### DIY

If you're familiar with deploying node applications, the built-in Remix app server is production-ready.

Make sure to deploy the output of `remix build`

- `build/`
- `public/build/`

### Using a Template

When you ran `npx create-remix@latest` there were a few choices for hosting. You can run that again to create a new project, then copy over your `app/` folder to the new project that's pre-configured for your target server.

```sh
cd ..
# create a new project, and pick a pre-configured host
npx create-remix@latest
cd my-new-remix-app
# remove the new project's app (not the old one!)
rm -rf app
# copy your app over
cp -R ../my-old-remix-app/app app
```
