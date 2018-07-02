# annotation_example
1) устанавливаем gradle https://gradle.org/install/ он нам понадобится для более удобной работы с зависимостями

2) у нас есть 2 модуля annotationProcessor и annotationUsage. Открвываем annotationProcessor в intellijIdea

3) Учим intellijIdea генерировать jar file c нужными дополнительными файлами. Зачем нужны дополнительные файлы написано здесь
http://hannesdorfmann.com/annotation-processing/annotationprocessing101


`File -> ProjectStructure -> Artifacts -> + -> Jar -> From Module dependencies`
слева еще раз кликаем `+ -> DirectoryContent` выбераем `additional_files` 

теперь собираем jar файл:
`Build -> Build Artifacts`

jar файл внутри должен иметь такую структуру:
```
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


4) идем в модуль annotationUsage и собраем его с помощью `gradle`
```
gradle clean build
```
должно вывестись `it works!` в логе

5) импортируем annotationUsage в intellijIdea как gradle project. Теперь билд можно вызывать из idea.

