# annotation_example
1) у нас есть 2 модуля annotationProcessor и annotationUsage.
открывает оба модуля с помомощью intellijIdea

2) компилируем с помощью intellijIdea модуль annotationProcessor (только его, второй пока не компилируется)

3) теперь нам нужно создать jar файл со спецальной струкрурой в нем, смотри пример тут: http://hannesdorfmann.com/annotation-processing/annotationprocessing101
в командной строке находим директорию куда intellijIdea  положила скомпилированные классы.
скорее всего это `annotationProcessor/out/production/annotationProcessor`

копируем туда манифест: `cp -r ../../../META-INF .`

получаем такую структуру:
```
$~/IdeaProjects/annotation_example/annotationProcessor/out/production/annotationProcessor ls -R
META-INF	com

./META-INF:
services

./META-INF/services:
javax.annotation.processing.Processor

./com:
company

./com/company:
Factory.class		MyProcessor.class
```

теперь собираем jar файл
`jar cvf processor.jar *`

4) идем в модуль annotationUsage и собраем его с помощью `javac`
```
cd annotationUsage/src
javac -cp ../../annotationProcessor/out/production/annotationProcessor/processor.jar Main.java
```

