**cocos2dx 2048**

Возможности:
 - произвольный размер (не только 4х4)
 - macos, ios and android support
 - прогресс сохраняется между запусками


MacOS, IOS: Запускать через Xcode. Файл проекта proj.ios_mac/Test2048.xcodeproj

Android: cocos run -p android
 

Алгоритм (левый свайп):
   -  бежим слева направо по колонкам строчек (сверху вниз)
   -  если ячейка пустая
         1) если нет сохраненной пустой, то сохраняем ее
   -  если ячейка не пустая, то
         1) двигаем ее в первую пустую (если есть), текущую заменяем нулем
         2) смотрим какая ячейка слева и склеиваем если это возможно
         3) если был сдвиг, то продолжаем с ячейки следующей за первой пустой (или с пустой, если склейка была)
            и обнуляем первую пустую

мердж только 1 за свайп, например (сдвиг влево)
- 2 2 2 2 -> 4 4 0 0
- 0 2 2 4 -> 4 4 0 0



todo:
 - проверять nullptr при вызове методов
 - tests
 - (fixed) вынести цвета (и не только) в константы
 - сохранять при выходе
 - (fixed: https://github.com/cocos2d/cocos2d-x/issues/19080) при запуске под mac черный экран пока не подвинешь окно с игрой
 
 
Дизайн заимствован: https://play2048.co


внешние использованные исходники
- RoundedRect::drawSolidRoundedRect - https://gist.github.com/dontangg/a7c3acec4bf05e61dd58
- Gestures - https://github.com/drakon-ag/cocos2dx-gesture-recognizers
