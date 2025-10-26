# Infinite Canvas Grid - Компонент галереи

## Обзор

Добавлен новый интерактивный компонент `InfiniteCanvasGrid` на главную страницу проекта, который предоставляет бесконечную галерею всех компонентов из registry с возможностью live preview, множественными способами навигации и оптимизированной загрузкой.

**Особенности:**
- 🖥️ Полностью fullscreen канвас без header и элементов управления
- 🎯 Apple-style навигация (drag, trackpad, touch, scroll с естественным скроллингом)
- 🔍 Zoom система (10% - 300%) с кнопками управления и pinch-to-zoom
- 🚀 One-time loading - компоненты загружаются только один раз и остаются видимыми навсегда
- ⚡ Оптимизированная производительность с viewport culling
- ✨ Красивые framer-motion анимации загрузки и переходов
- 🎨 Компоненты остаются видимыми после первого показа (нет мерцания)

## Возможности

### 🎯 Основные функции
- **Бесконечная сетка компонентов** - все компоненты из registry размещены в виде сетки на бесконечном холсте
- **Множественные способы навигации** - drag мышью, trackpad, touch gestures, scroll wheel
- **Lazy loading** - единоразовая загрузка только видимых компонентов с прогрессивной подгрузкой остальных
- **Live preview** - все компоненты отображаются вживую с полным функционалом и анимациями
- **Fullscreen modal** - клик по компоненту открывает полноразмерный preview
- **Интерактивные элементы управления** - кнопки для включения/выключения функций

### 🎨 Визуальные особенности
- **Анимированная фоновая сетка** - SVG-based grid pattern с динамическим позиционированием
- **Glass morphism UI** - полупрозрачные элементы управления с backdrop blur
- **Hover эффекты** - подсвечивание и увеличение компонентов при наведении
- **Responsive design** - адаптивные размеры и позиционирование
- **Dark theme** - темная цветовая схема для лучшего восприятия компонентов

### 📱 Компоненты в галерее

Галерея включает все компоненты из registry:

**Hero Components:**
- Hero Dock, Hero Minimalism, Hero Monochrome Launch, Hero Orbit Deck

**CTA Components:**
- CTA Marquee Base, Large, Reverse
- CTA with Video, Vertical Marquee variants
- CTA Horizontal Marquee

**Bento Components:**
- Bento Features (с золотой спиралью)
- Bento Monochrome (минималистичная сетка)

**Form Components:**
- Login Card (с анимированным фоном)

**Pricing Components:**
- Pricing Cards (с toggle анимациями)
- Pricing Cards variants 1 & 2

**FAQ Components:**
- FAQ Monochrome, FAQ with Spiral

**Utility Components:**
- Processing Card (с глитч эффектами)
- Fallback Card (элегантные fallback карточки)

## Использование

### Интеграция
Компонент уже интегрирован в главную страницу (`app/(home)/page.tsx`) и заменяет оригинальный Hero компонент.

### API
```tsx
import { InfiniteCanvasGrid } from '@/components/ui/infinite-canvas-grid';

<InfiniteCanvasGrid />
```

### Управление
- **Навигация** - drag мышью, trackpad, touch gestures, scroll wheel с Apple-style естественным скроллингом
- **Zoom** - кнопки +/-, scroll wheel (Ctrl+scroll), pinch-to-zoom на trackpad
- **Component Click** - открыть полноразмерный modal с красивой framer-motion анимацией
- **Loading** - компоненты загружаются только один раз при первом появлении и остаются видимыми навсегда
- **Fullscreen** - полностью immersive режим без header и UI элементов

## Способы навигации

- **Mouse Drag** - перетаскивание мышью (классический drag & drop)
- **Trackpad Gestures** - плавная навигация с повышенной чувствительностью
- **Touch Gestures** - поддержка касаний для мобильных устройств
- **Scroll Wheel** - прокрутка колесиком мыши для быстрой навигации

## Техническая реализация

### Архитектура
- **Fullscreen Canvas** - полностью immersive режим без header и UI элементов
- **React Hooks** - useState, useRef, useEffect, useCallback для управления состоянием
- **CSS Transforms** - GPU-ускоренная навигация через translate
- **SVG Grid Pattern** - динамически генерируемая фоновая сетка
- **Component Registry** - централизованная система управления компонентами
- **Modal System** - встроенная система полноразмерного preview с framer-motion анимациями
- **Global Scroll Prevention** - предотвращение скролла страницы на уровне document

### Оптимизации производительности
- **Intersection Observer** - отслеживание видимых компонентов для one-time loading
- **Viewport Culling** - рендеринг только компонентов в видимой области + margin
- **One-time Loading** - компоненты загружаются только один раз при первом появлении и остаются видимыми навсегда
- **Transform Optimization** - использование CSS transforms для GPU-ускорения
- **Persistent Components** - компоненты никогда не скрываются после загрузки, предотвращая мерцание
- **Framer Motion** - плавные анимации без влияния на производительность
- **Global Scroll Lock** - предотвращение скролла на уровне document

### Доступность
- **Keyboard Navigation** - поддержка навигации с клавиатуры
- **Screen Reader Support** - семантическая разметка для скринридеров
- **Focus Management** - правильное управление фокусом при модальных окнах
- **High Contrast** - поддержка высококонтрастных тем

## Файлы проекта

### Основные файлы
- `components/ui/infinite-canvas-grid.tsx` - основной компонент галереи
- `app/(home)/page.tsx` - главная страница с интеграцией
- `components/ui/README-InfiniteCanvasGrid.md` - детальная документация

### Зависимости
- Все компоненты из `@/registry/default/*`
- UI компоненты из `@/components/ui/*`
- Lucide React icons для интерфейса

## Запуск

```bash
npm run dev
```

Откройте http://localhost:3000 для просмотра галереи.

## Будущие улучшения

- [ ] Поиск и фильтрация компонентов
- [ ] Категоризация компонентов (Hero, CTA, Forms, etc.)
- [ ] Экспорт компонентов в CodeSandbox
- [ ] Анимации переходов между компонентами
- [ ] Bookmarking позиций в галерее
- [ ] Мини-карта для навигации
