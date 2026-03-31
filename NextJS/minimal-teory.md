# 📘 Next.js: Краткая сводка для справки

## 1. Что такое Next.js?

**Next.js** — это React-фреймворк для production, предоставляющий:
- Серверный рендеринг (SSR)
- Статическую генерацию (SSG)
- Маршрутизацию на основе файловой системы
- API Routes
- Оптимизацию производительности из коробки

---

## 2. Основные концепции

### 2.1. Рендеринг

```javascript
// 1. Client-Side Rendering (CSR) - обычный React
'use client' // Директива для клиентских компонентов
import { useState, useEffect } from 'react'

function ClientComponent() {
  const [data, setData] = useState(null)
  
  useEffect(() => {
    fetch('/api/data').then(res => res.json()).then(setData)
  }, [])
  
  return <div>{data?.name}</div>
}

// 2. Server-Side Rendering (SSR) - динамический рендеринг на сервере
export default async function SSRPage() {
  const data = await fetch('https://api.example.com/data').then(res => res.json())
  return <div>{data.name}</div>
}

// 3. Static Site Generation (SSG) - статическая генерация
export async function getStaticProps() {
  const data = await fetch('https://api.example.com/data').then(res => res.json())
  return {
    props: { data },
    revalidate: 3600 // ISR - перегенерация каждые 3600 секунд
  }
}

// 4. Incremental Static Regeneration (ISR)
export async function getStaticProps() {
  return {
    props: { data },
    revalidate: 60 // Обновление каждые 60 секунд
  }
}
```

### 2.2. Серверные и клиентские компоненты

```javascript
// app/page.tsx - Серверный компонент (по умолчанию)
// ✅ Работает на сервере
// ✅ Может быть асинхронным
// ✅ Имеет доступ к бэкенду
// ❌ Не имеет хуков (useState, useEffect)

export default async function ServerComponent() {
  const data = await fetchData()
  return <ClientComponent data={data} />
}

// app/components/ClientComponent.tsx
'use client' // Обязательная директива

import { useState } from 'react'

export default function ClientComponent({ data }) {
  const [state, setState] = useState(data)
  return <div onClick={() => setState('updated')}>{state}</div>
}
```

---

## 3. Маршрутизация (App Router)

### 3.1. Файловая структура

```
app/
├── layout.tsx          # Корневой layout
├── page.tsx            # Главная страница
├── about/
│   └── page.tsx        # /about
├── blog/
│   ├── page.tsx        # /blog
│   ├── [slug]/
│   │   └── page.tsx    # /blog/:slug (динамический маршрут)
│   └── layout.tsx      # Лейаут для /blog/*
├── api/
│   └── posts/
│       └── route.ts    # API эндпоинт /api/posts
├── (auth)/             # Группа маршрутов (без влияния на URL)
│   ├── login/
│   │   └── page.tsx
│   └── register/
│       └── page.tsx
└── loading.tsx         # Общий loading state
```

### 3.2. Динамические маршруты

```javascript
// app/blog/[slug]/page.tsx
interface PageProps {
  params: { slug: string }
  searchParams: { [key: string]: string | string[] | undefined }
}

export default async function BlogPost({ params, searchParams }: PageProps) {
  const post = await getPost(params.slug)
  
  return (
    <article>
      <h1>{post.title}</h1>
      <p>{post.content}</p>
    </article>
  )
}

// Генерация статических параметров
export async function generateStaticParams() {
  const posts = await getPosts()
  return posts.map(post => ({
    slug: post.slug
  }))
}
```

### 3.3. Группы маршрутов

```javascript
// app/(marketing)/layout.tsx - Группа маршрутов для маркетинга
export default function MarketingLayout({
  children
}: {
  children: React.ReactNode
}) {
  return (
    <div>
      <MarketingHeader />
      {children}
      <MarketingFooter />
    </div>
  )
}

// app/(marketing)/pricing/page.tsx - URL: /pricing
// app/(marketing)/contact/page.tsx - URL: /contact
```

---

## 4. API Routes

```javascript
// app/api/posts/route.ts
import { NextResponse } from 'next/server'

// GET запрос
export async function GET(request: Request) {
  const { searchParams } = new URL(request.url)
  const id = searchParams.get('id')
  
  const posts = await db.posts.findMany()
  return NextResponse.json(posts)
}

// POST запрос
export async function POST(request: Request) {
  const body = await request.json()
  
  const post = await db.posts.create({
    data: body
  })
  
  return NextResponse.json(post, { status: 201 })
}

// PUT запрос
export async function PUT(request: Request) {
  const { id, ...data } = await request.json()
  
  const post = await db.posts.update({
    where: { id },
    data
  })
  
  return NextResponse.json(post)
}

// DELETE запрос
export async function DELETE(request: Request) {
  const { searchParams } = new URL(request.url)
  const id = searchParams.get('id')
  
  await db.posts.delete({ where: { id } })
  return NextResponse.json({ success: true })
}
```

---

## 5. Data Fetching

### 5.1. Fetch в серверных компонентах

```javascript
// Автоматическое кэширование и дедупликация
export default async function Page() {
  // fetch автоматически кэшируется
  const data = await fetch('https://api.example.com/data')
  
  // Отключаем кэширование
  const freshData = await fetch('https://api.example.com/data', {
    cache: 'no-store'
  })
  
  // Ревалидация каждые 60 секунд
  const revalidatedData = await fetch('https://api.example.com/data', {
    next: { revalidate: 60 }
  })
  
  return <div>{data}</div>
}
```

### 5.2. Server Actions

```javascript
// app/actions/posts.ts
'use server'

import { revalidatePath } from 'next/cache'

export async function createPost(formData: FormData) {
  const title = formData.get('title')
  const content = formData.get('content')
  
  // Валидация
  if (!title || !content) {
    throw new Error('Missing fields')
  }
  
  // Сохранение в БД
  await db.posts.create({
    data: { title, content }
  })
  
  // Ревалидация страницы
  revalidatePath('/posts')
}

// app/posts/create/page.tsx
'use client'

import { createPost } from '@/actions/posts'
import { useFormStatus } from 'react-dom'

function SubmitButton() {
  const { pending } = useFormStatus()
  return (
    <button type="submit" disabled={pending}>
      {pending ? 'Создание...' : 'Создать пост'}
    </button>
  )
}

export default function CreatePostPage() {
  return (
    <form action={createPost}>
      <input name="title" placeholder="Заголовок" required />
      <textarea name="content" placeholder="Содержание" required />
      <SubmitButton />
    </form>
  )
}
```

---

## 6. Оптимизация

### 6.1. Image компонент

```javascript
import Image from 'next/image'

export default function OptimizedImage() {
  return (
    <Image
      src="/hero.jpg"
      alt="Hero image"
      width={1200}
      height={600}
      priority // Приоритетная загрузка
      quality={85}
      sizes="(max-width: 768px) 100vw, 50vw"
      placeholder="blur"
      blurDataURL="data:image/jpeg..."
    />
  )
}
```

### 6.2. Font оптимизация

```javascript
// app/layout.tsx
import { Inter, Roboto_Mono } from 'next/font/google'

const inter = Inter({
  subsets: ['latin', 'cyrillic'],
  display: 'swap',
  variable: '--font-inter'
})

const robotoMono = Roboto_Mono({
  subsets: ['latin'],
  variable: '--font-roboto-mono'
})

export default function Layout({ children }) {
  return (
    <html lang="ru" className={`${inter.variable} ${robotoMono.variable}`}>
      <body>{children}</body>
    </html>
  )
}
```

### 6.3. Script оптимизация

```javascript
import Script from 'next/script'

export default function Analytics() {
  return (
    <>
      <Script
        src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"
        strategy="afterInteractive"
      />
      <Script id="google-analytics" strategy="afterInteractive">
        {`
          window.dataLayer = window.dataLayer || [];
          function gtag(){dataLayer.push(arguments);}
          gtag('js', new Date());
          gtag('config', 'GA_MEASUREMENT_ID');
        `}
      </Script>
    </>
  )
}
```

### 6.4. Dynamic Imports

```javascript
import dynamic from 'next/dynamic'

// Динамический импорт с отключением SSR
const HeavyComponent = dynamic(() => import('@/components/HeavyComponent'), {
  loading: () => <p>Загрузка...</p>,
  ssr: false
})

// Динамический импорт с ленивой загрузкой
const LazyModal = dynamic(() => import('@/components/Modal'))

export default function Page() {
  const [showModal, setShowModal] = useState(false)
  
  return (
    <>
      <button onClick={() => setShowModal(true)}>Открыть</button>
      {showModal && <LazyModal />}
    </>
  )
}
```

---

## 7. Middleware

```javascript
// middleware.ts
import { NextResponse } from 'next/server'
import type { NextRequest } from 'next/server'

export function middleware(request: NextRequest) {
  const token = request.cookies.get('token')
  const isAuthPage = request.nextUrl.pathname.startsWith('/login')
  
  // Редирект на логин если нет токена
  if (!token && !isAuthPage) {
    return NextResponse.redirect(new URL('/login', request.url))
  }
  
  // Редирект на дашборд если уже авторизован
  if (token && isAuthPage) {
    return NextResponse.redirect(new URL('/dashboard', request.url))
  }
  
  // Добавляем заголовки
  const response = NextResponse.next()
  response.headers.set('x-custom-header', 'value')
  
  return response
}

// Конфигурация для каких маршрутов применять
export const config = {
  matcher: [
    '/((?!api|_next/static|_next/image|favicon.ico).*)',
  ]
}
```

---

## 8. Metadata и SEO

```javascript
// app/layout.tsx
export const metadata = {
  metadataBase: new URL('https://example.com'),
  title: {
    default: 'Мой сайт',
    template: '%s | Мой сайт'
  },
  description: 'Описание сайта',
  keywords: ['next.js', 'react', 'typescript'],
  authors: [{ name: 'Имя автора' }],
  openGraph: {
    title: 'Мой сайт',
    description: 'Описание для соцсетей',
    url: 'https://example.com',
    siteName: 'Мой сайт',
    images: [
      {
        url: '/og-image.jpg',
        width: 1200,
        height: 630
      }
    ],
    locale: 'ru_RU',
    type: 'website'
  },
  robots: {
    index: true,
    follow: true,
    googleBot: {
      index: true,
      follow: true
    }
  }
}

// app/posts/[slug]/page.tsx - Динамические метаданные
export async function generateMetadata({ params }: PageProps) {
  const post = await getPost(params.slug)
  
  return {
    title: post.title,
    description: post.excerpt,
    openGraph: {
      title: post.title,
      description: post.excerpt,
      images: [post.coverImage]
    }
  }
}
```

---

## 9. Переменные окружения

```javascript
// .env.local (не коммитится)
DATABASE_URL="postgresql://..."
API_SECRET="secret-key"

// .env (коммитится)
NEXT_PUBLIC_API_URL="https://api.example.com"

// Использование
// Серверные переменные (только на сервере)
const dbUrl = process.env.DATABASE_URL

// Публичные переменные (доступны на клиенте)
const apiUrl = process.env.NEXT_PUBLIC_API_URL
```

---

## 10. Часто используемые хуки

### 10.1. useRouter

```javascript
'use client'
import { useRouter, usePathname, useSearchParams } from 'next/navigation'

export default function Navigation() {
  const router = useRouter()
  const pathname = usePathname()
  const searchParams = useSearchParams()
  
  const page = searchParams.get('page') || '1'
  
  return (
    <button onClick={() => router.push('/about')}>
      О нас
    </button>
  )
}
```

### 10.2. usePathname и useSearchParams

```javascript
'use client'
import { usePathname, useSearchParams } from 'next/navigation'

export default function ActiveLink() {
  const pathname = usePathname()
  const searchParams = useSearchParams()
  
  const isActive = pathname === '/about'
  const category = searchParams.get('category')
  
  return <div>Active: {isActive}, Category: {category}</div>
}
```

---

## 11. Рекомендации

### 11.1. Оптимизация производительности

```javascript
// ✅ Используйте серверные компоненты по умолчанию
// ✅ Добавляйте 'use client' только когда нужны хуки или события
// ✅ Используйте next/image для изображений
// ✅ Используйте next/font для шрифтов
// ✅ Используйте динамические импорты для тяжелых компонентов
// ✅ Настройте кэширование для fetch запросов
```

### 11.2. Структура проекта

```
project/
├── app/
│   ├── (auth)/
│   │   ├── login/
│   │   └── register/
│   ├── dashboard/
│   │   ├── layout.tsx
│   │   ├── page.tsx
│   │   └── loading.tsx
│   ├── api/
│   └── layout.tsx
├── components/
│   ├── ui/
│   ├── forms/
│   └── shared/
├── lib/
│   ├── db.ts
│   ├── auth.ts
│   └── utils.ts
├── types/
├── hooks/
├── public/
├── middleware.ts
├── next.config.js
└── package.json
```

### 11.3. Полезные команды

```bash
# Создание нового проекта
npx create-next-app@latest my-app

# Разработка
npm run dev

# Сборка
npm run build

# Запуск в production
npm run start

# Проверка типов
npm run type-check

# Линтинг
npm run lint
```

---

## 12. Быстрые ответы

| Вопрос | Ответ |
|--------|-------|
| **Серверный или клиентский компонент?** | По умолчанию серверный. `'use client'` для клиентского |
| **Как получить данные?** | В серверных: `fetch()`. В клиентских: `useEffect` или `SWR`/`TanStack Query` |
| **Как обновить данные после мутации?** | `revalidatePath()` или `revalidateTag()` в Server Actions |
| **Как сделать API?** | `app/api/route.ts` |
| **Как добавить метаданные?** | `export const metadata` в layout/page |
| **Как добавить middleware?** | `middleware.ts` в корне |
| **Как оптимизировать изображения?** | `next/image` |
| **Как добавить аналитику?** | `next/script` |
| **Как работать с формами?** | Server Actions или клиентские формы с API |
| **Как деплоить?** | Vercel (рекомендуется), Netlify, AWS, любой Node.js хостинг |

---

## 13. Полезные ссылки

- [Официальная документация](https://nextjs.org/docs)
- [App Router](https://nextjs.org/docs/app)
- [Server Actions](https://nextjs.org/docs/app/building-your-application/data-fetching/server-actions)
- [Оптимизация](https://nextjs.org/docs/app/building-your-application/optimizing)
- [Деплой](https://nextjs.org/docs/deployment)

---

Эта сводка покрывает основные концепции Next.js для быстрой справки. Для глубокого изучения рекомендуется обратиться к официальной документации.
