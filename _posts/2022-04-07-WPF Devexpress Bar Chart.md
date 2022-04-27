---
title: WPF + Devexpress Bar Chart
author: asy
date: 2022-01-04 18:30:00 -0500
categories: [C#, chart]
tags: [devexpress, bar chart]

---

## Bar Chart

> Devexpress 의 BarSideBySideSeries2D 를 이용하여 Bar Chart 를 그려봅니다.

### View

```xml
<Window x:Class="WpfApp1.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp1"
        xmlns:dxc="http://schemas.devexpress.com/winfx/2008/xaml/charts"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="800">
    <dxc:ChartControl DataSource="{Binding Data}">
        <dxc:ChartControl.CrosshairOptions>
            <dxc:CrosshairOptions ShowArgumentLabels="True" 
                                      ShowValueLabels="True" 
                                      ShowValueLine="True"/>
        </dxc:ChartControl.CrosshairOptions>
        <dxc:ChartControl.Titles>
            <dxc:Title Content="Sales by Regions" 
                           HorizontalAlignment="Center"/>
        </dxc:ChartControl.Titles>
        <dxc:XYDiagram2D Rotated="True">
            <dxc:BarSideBySideSeries2D DisplayName="Annual Statistics" 
                                           ArgumentDataMember="Argument" 
                                           ValueDataMember="Value" 
                                           CrosshairLabelPattern="${V:f2}M"/>
        </dxc:XYDiagram2D>
    </dxc:ChartControl>
</Window>
```

- `ChartControl.DataSource` 에 Bingding 하기 위해 `DataSource="{Binding Data}" 를 추가
- `CrosshairOptions`에서 지정한 옵션은 마우스 오버 시 해당 Bar 의 x값과 y값을 보여주는 옵션입니다.
- `XYDialgram2D.Rotated`를 이용해 Bar Chart 의 x,y 축 방향을 변경할 수 있습니다.
- `ArgumentDataMember`는 Bar 의 속성값이 될 바인딩된 모델 필드명을 지정합니다.
- `ValueDataMember` 는 Bar 의 값이 될 바인딩된 모델 필드명을 지정합니다.

### ViewModel

```cs
public partial class MainWindow : Window
{
    public ObservableCollection<DataPoint> Data { get; private set; }
    public MainWindow()
    {
        InitializeComponent();
        DataContext = this;
        Data = new ObservableCollection<DataPoint>
        {
            new DataPoint { Argument = "Bar1", Value = 5.42d },
            new DataPoint { Argument = "Bar2", Value = 15.42d },
            new DataPoint { Argument = "Bar3", Value = 25.42d }
        };
    }
}
```

- DataPoint Model 을 이용하여 ObservableCollection 값을 바인딩합니다.
- Bar 는 DataPoint 를 사용하여 x값과 y값을 정합니다.

### Model

```cs
public class DataPoint
{
    public string Argument { get; set; }
    public double Value { get; set; }
}
```

- `Argument` 는 X 축 값이 됩니다.
- `Value`는 bar 의 값이 됩니다.

![](https://github.com/asy0239/asy0239.github.io/tree/master/assets/img\BarChart.png)