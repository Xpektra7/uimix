# Продвинутые анимации с Framer Motion

## Что добавлено

### 1. Framer Motion интеграция
- **Импорт**: `motion`, `AnimatePresence` из `framer-motion`
- **Стабильные анимации** с spring physics
- **Плавные переходы** между состояниями

### 2. Анимация модального окна
```tsx
<motion.div 
  initial={{ opacity: 0 }}
  animate={{ opacity: 1 }}
  exit={{ opacity: 0 }}
  transition={{ duration: 0.3 }}
>
```

### 3. Анимированные кнопки
```tsx
<motion.button
  initial={{ opacity: 0, scale: 0.8 }}
  animate={{ opacity: 1, scale: 1 }}
  exit={{ opacity: 0, scale: 0.8 }}
  transition={{ duration: 0.2, delay: 0.1 }}
>
```

### 4. Плавная анимация колонки кода
```tsx
<motion.div 
  initial={{ 
    width: 0, 
    opacity: 0, 
    x: -300,
    paddingLeft: 0,
    paddingRight: 0
  }}
  animate={{ 
    width: '50%', 
    opacity: 1, 
    x: 0,
    paddingLeft: 24,
    paddingRight: 24
  }}
  exit={{ 
    width: 0, 
    opacity: 0, 
    x: -300,
    paddingLeft: 0,
    paddingRight: 0
  }}
  transition={{ 
    duration: 0.7, 
    ease: [0.4, 0.0, 0.2, 1],
    type: "spring",
    stiffness: 100,
    damping: 20
  }}
>
```

### 5. Spring анимации
- **Type**: `"spring"` для естественного движения
- **Stiffness**: 100 для отзывчивости
- **Damping**: 20 для плавности
- **Custom easing**: `[0.4, 0.0, 0.2, 1]` для Material Design

### 6. Последовательные анимации
- **Заголовок**: delay 0.2s
- **Installation**: delay 0.3s  
- **Code**: delay 0.4s
- **Компонент**: delay 0.4s

### 7. Анимация превью области
```tsx
<motion.div 
  animate={{
    width: showCode ? '50%' : '100%',
    padding: showCode ? 24 : 0
  }}
  transition={{ 
    duration: 0.7, 
    ease: [0.4, 0.0, 0.2, 1],
    type: "spring",
    stiffness: 100,
    damping: 20
  }}
>
```

### 8. Анимация полноэкранного компонента
```tsx
<motion.div 
  initial={{ opacity: 0, scale: 0.8 }}
  animate={{ opacity: 1, scale: 1 }}
  exit={{ opacity: 0, scale: 0.8 }}
  transition={{ duration: 0.6, delay: 0.4 }}
>
```

## Результат

Теперь все переходы анимированы:
- ✅ **Открытие модального окна** - fade in с масштабированием
- ✅ **Появление кнопок** - с задержкой и масштабированием
- ✅ **Открытие колонки кода** - плавное выезжание слева с spring physics
- ✅ **Закрытие колонки кода** - плавное уезжание влево
- ✅ **Возврат к полноэкранному режиму** - плавное масштабирование компонента
- ✅ **Последовательные анимации** - элементы появляются по очереди

Анимации стали намного более профессиональными и приятными! 🚀
