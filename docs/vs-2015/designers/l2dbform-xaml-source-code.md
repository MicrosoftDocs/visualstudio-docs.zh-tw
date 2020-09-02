---
title: L2DBForm.xaml 原始程式碼 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 624e96d4-6d27-4195-8ac2-2f3835f6c57e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc0ec53c35f87751efe78359f582e5f4297143c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664269"
---
# <a name="l2dbformxaml-source-code"></a>L2DBForm.xaml 原始程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題包含並描述 [使用 LINQ to XML 範例 >l2dbform.xaml 原始程式碼的 WPF 資料](../designers/wpf-data-binding-using-linq-to-xml-example.md)系結的 XAML 原始程式檔。

## <a name="overall-ui-structure"></a>UI 的整體結構
 如同 WPF 專案般，這個檔案包含一個父項目，也就是 <xref:System.Windows.Window> 命名空間中，與衍生類別 `L2XDBFrom` 相關聯的 `LinqToXmlDataBinding` XML 項目。

 用戶端區域包含在淡藍色背景的 <xref:System.Windows.Controls.StackPanel> 中。 這個面板包含四個 <xref:System.Windows.Controls.DockPanel> UI 區段，以 <xref:System.Windows.Controls.Separator> 列分隔。 如需了解這些區段的用途，請參閱[上一個主題](../designers/walkthrough-linqtoxmldatabinding-example.md)中的＜備註＞****。

 每個區段都包含一個可以識別自身的標籤。 在前兩個區段中，這個標籤會透過使用 <xref:System.Windows.FrameworkElement.LayoutTransform%2A>而旋轉 90 度。 區段的剩餘部分則包含適用於該區段目的的 UI 項目：文字區塊、文字方塊、按鈕等等。 有時候，子系 <xref:System.Windows.Controls.StackPanel> 用於調整這些子控制項。

## <a name="window-resource-section"></a>視窗資源區段
 第 9 行的 `<Window.Resources>` 開頭標記表示視窗資源區段的開頭， 並以第 35 行的結束標記表示結尾。

 跨越第 11 行到第 25 行的 `<ObjectDataProvider>` 標記會宣告名稱為 <xref:System.Windows.Data.ObjectDataProvider>的 `LoadedBooks`，並使用 <xref:System.Xml.Linq.XElement> 當做來源。 這個 <xref:System.Xml.Linq.XElement> 會藉由剖析內嵌的 XML 文件 ( `CDATA` 項目) 來初始化。 請注意，宣告內嵌的 XML 文件以及進行剖析時，會保留空白字元。 這會因為用於顯示原始 XML 的 <xref:System.Windows.Controls.TextBlock> 控制項沒有特殊的 XML 格式化功能而完成。

 最後在第 28 到 34 行會定義名稱為 <xref:System.Windows.DataTemplate> 的 `BookTemplate` 。 這個範本將用於顯示 [ **書籍清單** ] UI 區段中的項目。 它會使用資料繫結和 LINQ to XML 動態屬性，透過下列指派，擷取書籍 ID 和書籍名稱：

```
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"
```

## <a name="data-binding-code"></a>資料繫結程式碼
 除了 <xref:System.Windows.DataTemplate> 項目之外，資料繫結也會用在這個檔案的其他多個地方。

 在第 38 行的 `<StackPanel>` 開頭標記中，此面板的 <xref:System.Windows.FrameworkElement.DataContext%2A> 屬性會設定為 `LoadedBooks` 資料提供者。

```
DataContext="{Binding Source={StaticResource LoadedBooks}}
```

 這可以讓 (第 46 行) 名稱為 <xref:System.Windows.Controls.TextBlock> 的 `tbRawXml` 繫結至此資料提供者的 `Xml` 屬性以顯示原始 XML：

```
Text="{Binding Path=Xml}"
```

 第 58 到 62 行 [書籍清單] <xref:System.Windows.Controls.ListBox>**UI 區段中的** 會將其顯示項目的範本設定為視窗資源區段中定義的 `BookTemplate` ：

```
ItemTemplate ="{StaticResource BookTemplate}"
```

 接著在第 59 到 62 行，書籍的實際值會繫結到此清單方塊：

```
<ListBox.ItemsSource>
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
</ListBox.ItemsSource>
```

 第三個 UI 區段，也就是 [ **編輯選取的書籍**] 會先將父代 <xref:System.Windows.FrameworkElement.DataContext%2A> 的 <xref:System.Windows.Controls.StackPanel> 繫結到目前從 [ **書籍清單** ] UI 區段 (第 82 行) 選取的項目：

```
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"
```

 接著，它會使用雙向資料繫結，讓書籍項目的目前值顯示到此面板的兩個文字方塊中，或從其中更新。 動態屬性的資料繫結類似於 `BookTemplate` 資料範本中所使用的資料繫結：

```
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"
```

 最後一個 UI 區段，也就是 [ **加入新的書籍**] 不會將資料繫結用於其 XAML 程式碼中，而且在 L2DBForm.xaml.cs 檔案的事件處理程式碼中找不到這類的程式碼。

## <a name="example"></a>範例

### <a name="description"></a>描述

> [!NOTE]
> 建議您將下列程式碼複製到程式碼編輯器 (例如，Visual Studio 中的 C# 原始程式碼編輯器)，如此將更容易追蹤行號。

### <a name="code"></a>程式碼

```xml
<Window x:Class="LinqToXmlDataBinding.L2XDBForm"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:system="clr-namespace:System;assembly=mscorlib"
    xmlns:xlinq="clr-namespace:System.Xml.Linq;assembly=System.Xml.Linq"
    xmlns:local="clr-namespace:LinqToXmlDataBinding"
    Title="WPF Data Binding using LINQ-to-XML" Height="665" Width="500" ResizeMode="NoResize">

    <Window.Resources>
        <!-- Books provider and inline data -->
        <ObjectDataProvider x:Key="LoadedBooks" ObjectType="{x:Type xlinq:XElement}" MethodName="Parse">
            <ObjectDataProvider.MethodParameters>
                <system:String xml:space="preserve">
<![CDATA[
<books xmlns="http://www.mybooks.com">
  <book id="0">book zero</book>
  <book id="1">book one</book>
  <book id="2">book two</book>
  <book id="3">book three</book>
</books>
]]>
                </system:String>
                <xlinq:LoadOptions>PreserveWhitespace</xlinq:LoadOptions>
            </ObjectDataProvider.MethodParameters>
        </ObjectDataProvider>

        <!-- Template for use in Books List listbox. -->
        <DataTemplate x:Key="BookTemplate">
            <StackPanel Orientation="Horizontal">
                <TextBlock Margin="3" Text="{Binding Path=Attribute[id].Value}"/>
                <TextBlock Margin="3" Text="-"/>
                <TextBlock Margin="3" Text="{Binding Path=Value}"/>
            </StackPanel>
        </DataTemplate>
    </Window.Resources>

    <!-- Main visual content container -->
    <StackPanel Background="lightblue" DataContext="{Binding Source={StaticResource LoadedBooks}}">
        <!-- Raw XML display section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">XML
            <Label.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Label.LayoutTransform>
            </Label>
            <TextBlock Name="tbRawXml" Height="200" Background="LightGray" Text="{Binding Path=Xml}" TextTrimming="CharacterEllipsis" />
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- List box to display all books section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">Book List
                <Label.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Label.LayoutTransform>
            </Label>
            <ListBox Name="lbBooks" Height="200" Width="415" ItemTemplate ="{StaticResource BookTemplate}">
                <ListBox.ItemsSource>
                    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
                </ListBox.ItemsSource>
            </ListBox>
            <Button Margin="5" DockPanel.Dock="Right" Height="30" Width ="130" Content="Remove Selected Book" Click="OnRemoveBook">
            <Button.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Button.LayoutTransform>
            </Button>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Edit current selection section -->
        <DockPanel Margin="5">
            <TextBlock Margin="5" Height="30" Width="65" DockPanel.Dock="Right" Background="LightGray" TextWrapping="Wrap" TextAlignment="Center">
                    Changes are live!
                <TextBlock.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </TextBlock.LayoutTransform>
            </TextBlock>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Edit Selected Book</Label>
                <StackPanel Margin="1" DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="editAttributeTextBox" Width="410" Text="{Binding Path=Attribute[id].Value}">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book ID and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="editValueTextBox" Width="410" Text="{Binding Path=Value}" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book Value and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Add new book section -->
        <DockPanel Margin="5">
            <Button Margin="5" Height="30" DockPanel.Dock="Right" Click ="OnAddBook">Add Book
                <Button.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Button.LayoutTransform>
            </Button>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Add New Book</Label>
                <StackPanel Margin="1">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="tbAddID" Width="410">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="tbAddValue" Width="410" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="UltraBold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>
    </StackPanel>
</Window>

```

### <a name="comments"></a>註解
 如需與 WPF UI 元素相關聯之事件處理常式的 c # 原始程式碼，請參閱 [L2DBForm.xaml.cs 原始程式碼](../designers/l2dbform-xaml-cs-source-code.md)。

## <a name="see-also"></a>另請參閱
 [逐步解說： LinqToXmlDataBinding 範例](../designers/walkthrough-linqtoxmldatabinding-example.md) [L2DBForm.xaml.cs 來源程式碼](../designers/l2dbform-xaml-cs-source-code.md)
