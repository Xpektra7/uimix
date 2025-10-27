# Исправление центрирования компонента в полноэкранном режиме

## Проблема
Компонент был смещен вниз в полноэкранном режиме из-за того, что:
- Заголовок компонента занимал место в flexbox layout
- Кнопки влияли на позиционирование контента

## Решение

### 1. Абсолютное позиционирование заголовка
```tsx
{/* Component title - positioned absolutely to not affect centering */}
<div className="absolute top-0 left-1/2 transform -translate-x-1/2 mt-4">
  <h3 className="text-lg font-semibold text-center">{componentName}</h3>
</div>
```

### 2. Фиксированное позиционирование кнопок
```tsx
{/* Close button */}
<button className="group fixed top-6 right-6 z-20 ...">

{/* Show Code button */}
<button className="group fixed top-6 left-6 z-20 ...">
```

### 3. Идеальное центрирование компонента
```tsx
{/* Centered component */}
<div className="flex items-center justify-center w-full h-full">
  <ComponentPreview 
    component={component} 
    scale={1} 
    hideFullscreen 
  />
</div>
```

## Результат

Теперь в полноэкранном режиме:
- ✅ **Компонент точно по центру** видимой области экрана
- ✅ **Заголовок не влияет** на позиционирование (абсолютное позиционирование)
- ✅ **Кнопки не влияют** на центрирование (фиксированное позиционирование)
- ✅ **Полная высота и ширина** используется для центрирования компонента

Компонент теперь идеально центрирован относительно видимой области экрана! 🎯
