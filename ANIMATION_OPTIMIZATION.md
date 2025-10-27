# Оптимизация анимаций - устранение лагов

## Проблема
Анимации все еще лагали даже после отключения канваса.

## Решение

### 1. Упрощение анимаций
- **Убрали Framer Motion** - заменили на простые CSS transitions
- **Уменьшили длительность** - с 700ms до 500ms
- **Упростили easing** - с spring physics на `ease-out`
- **Убрали сложные анимации** - нет последовательных delay анимаций

### 2. CSS оптимизации
```tsx
style={{
  willChange: 'transform, width, opacity',
  transform: 'translate3d(0, 0, 0)', // Force hardware acceleration
}}
```

### 3. Аппаратное ускорение
- **`willChange`** - предупреждает браузер об изменениях
- **`translate3d(0, 0, 0)`** - принудительно включает GPU ускорение
- **`transform`** вместо `left/top` - более эффективно

### 4. Упрощенная структура анимаций
```tsx
// Было: сложные Framer Motion анимации
<motion.div animate={{ width: '50%', opacity: 1, x: 0 }}>

// Стало: простые CSS transitions
<div className="transition-all duration-500 ease-out">
```

### 5. Оптимизированные переходы
- **Flexbox transitions** - `flex-row` ↔ `flex-col`
- **Width transitions** - `w-0` ↔ `w-1/2`
- **Opacity transitions** - `opacity-0` ↔ `opacity-100`
- **Transform transitions** - `translate-x-0` ↔ `-translate-x-full`

## Результат

Теперь анимации:
- ✅ **Работают на GPU** - аппаратное ускорение
- ✅ **Просты и быстры** - нет сложных вычислений
- ✅ **Оптимизированы** - `willChange` и `translate3d`
- ✅ **Стабильны** - простые CSS transitions
- ✅ **Плавные** - 500ms с `ease-out`

## Технические детали

- **Hardware acceleration**: `translate3d(0, 0, 0)`
- **Performance hints**: `willChange: 'transform, width, opacity'`
- **Simplified timing**: `duration-500 ease-out`
- **Reduced complexity**: убрали spring physics и delay анимации

Анимации теперь должны работать максимально плавно! 🚀
