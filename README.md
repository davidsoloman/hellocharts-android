#HelloCharts for Android

Charting library for Android compatible with API 8+(Android 2.2).
Works best when hardware acceleration is available so I recommend using it with API 14+(Android 4.0).
Apache License, version 2.0.

##Supports

 - Line chart
 - Column chart
 - Pie chart
 - Bubble chart
 - Combo chart(columns/lines)
 - Preview charts(for column chart and line chart)
 - Animations
 - Zoom(pinch to zoom, double tap zoom), scroll and fling
 - Value selection
 - Customizable labels for values
 - Custom and auto-generated axes(most charts handles four axes: top, bottom, left, right)
 - Some other attributes like colours, fonts, lines thickness etc.

##Screens and Samples

![](screens/scr-line1.png)

![](screens/scr-tempo.png)

![](screens/scr-dependency.png)

![](screens/scr-combo.png)

![](screens/scr-column1.png)

![](screens/scr-preview-column.png)

![](screens/scr-pie1.png)

![](screens/scr-bubble1.png)

##Download and Import

###Eclipse

 - download hellocharts-library-<version>.jar from releases page and copy it into the `libs` folder of your
 application project.

 **or**

 - download/clone repository and import hellocharts-library project into your workspace: `File -> Import -> Android ->
 Existing Android Code` and select hellocharts-library directory.
 - right click on application project `Properties -> Android -> Add` and select hellocharts library project.

###Android Studio/Gradle

 - download/clone repository and import hellocharts-library as module: `File -> Import Module` and select hellocharts-library directory.
 - add dependency:
 ```groovy
     compile project(':hellocharts-library')
 ```

 **or**

 - download/clone repository and publish library artifact into your local or remote repository.
 - go to hellocharts-library directory and execute `gradle clean build publishToMavenLocal` to publish to maven local repository.
 - go to hellocharts-library directory and execute `gradle clean build publish` to publish to other repository
  configured in build.gradle(you need to modify repository url and credentials in build.gradle file)
 - add dependency:
 ```groovy
     compile 'lecho.lib.hellocharts:hellocharts-library:1.0@aar'
     compile 'com.android.support:support-v4:20+'
 ```

##Usage

Every chart view can be defined in layout xml file:
```xml
    <lecho.lib.hellocharts.LineChartView
        android:id="@+id/chart"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
```

 or created in code and added to layout later:

 ```java
    LineChartView chart = new LineChartView(context);
    layout.addView(chart);
 ```

 Use methods from *ChartView class to define chart behavior, for example:

 ```java
    Chart.setInteractive(boolean isInteractive);
    Chart.setZoomType(ZoomType zoomType);
    Chart.setContainerScrollEnabled(boolean isContainerScrollEnabled, ContainerScrollType containerScrollType);
 ```

 Use methods from data models to define how chart looks like, for example

 ```java
    ChartData.setAxisXBottom(Axis axisX);
    ColumnChartData.setStacked(boolean isStacked);
    Line.setStrokeWidth(int strokeWidthDp);
 ```

 Every chart has its own method to set chart data:

 ```java
    LineChartView.setLineChartData(LineChartData data);
 ```

 After you set chart data you can still modify its attributes but right after that you should call set*ChartData()
 method again to let chart recalculate and redraw data. There is also an option to use copy constructor for deep copy of
 chart data. You can safely modify copy in other threads and pass it to set*ChartData() method later.

#License

    Copyright 2014 Leszek Wach

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
