# Полноэкранный компонент с красивой анимацией Show Code

## Новые возможности

### 1. Полноэкранный режим по умолчанию
- **Компонент в полном размере** - `scale={1}` для максимального размера
- **Центрирование** - компонент размещен по центру видимой области экрана
- **Чистый интерфейс** - только название компонента и сам компонент
- **Flexbox layout** - `flex-col justify-center items-center` для идеального центрирования

### 2. Улучшенная кнопка "Show Code"
- **Визуальная индикация** - активное состояние с `bg-primary/20 border-primary/30`
- **Цветовая индикация** - иконка меняет цвет на `text-primary` когда активно
- **Плавные переходы** - `duration-300` для всех состояний кнопки

### 3. Красивая анимация перехода
- **Длительность**: 700ms с `ease-in-out` для плавности
- **Flexbox переход**: `flex-col justify-center items-center` → `flex-row`
- **Колонка кода**: 
  - Появление: `w-1/2 p-6 opacity-100 translate-x-0`
  - Скрытие: `w-0 p-0 opacity-0 -translate-x-full overflow-hidden`
- **Превью область**:
  - Полноэкранный: `w-full h-full flex items-center justify-center p-0`
  - С кодом: `w-1/2 p-6 overflow-y-auto`

### 4. Два режима отображения

#### Полноэкранный режим (`!showCode`)
```tsx
<div className="w-full h-full flex flex-col items-center justify-center">
  <div className="mb-6">
    <h3 className="text-lg font-semibold text-center">{componentName}</h3>
  </div>
  <div className="flex items-center justify-center">
    <ComponentPreview 
      component={component} 
      scale={1}  // Полный размер
      hideFullscreen 
    />
  </div>
</div>
```

#### Режим с кодом (`showCode`)
```tsx
<div className="space-y-4">
  <h3 className="text-lg font-semibold">Preview</h3>
  <div className="relative">
    <ComponentPreview 
      component={component} 
      scale={scale}  // Масштабированный размер
      hideFullscreen 
    />
  </div>
</div>
```

## Пользовательский опыт

1. **Клик на компонент** → Открывается полноэкранное превью в полном размере по центру
2. **Клик на кнопку Code** → Красивая анимация появления колонки с кодом слева (700ms)
3. **Повторный клик на Code** → Колонка плавно скрывается, возврат к полноэкранному режиму
4. **Клик на X** → Закрытие модального окна

## Технические детали

- **Flexbox layout** вместо Grid для лучшего контроля анимаций
- **Условное отображение** превью в зависимости от состояния
- **Плавные переходы** для всех элементов интерфейса
- **Визуальная обратная связь** через изменение цвета кнопки

Теперь пользователи получают максимально immersive опыт просмотра компонентов! 🚀
