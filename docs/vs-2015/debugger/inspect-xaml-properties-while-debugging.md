---
title: 偵錯時檢查 XAML 屬性 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a30f04c3d2b2d109816ff8bcfbf17fe483f24886
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758864"
---
# <a name="inspect-xaml-properties-while-debugging"></a>在偵錯時檢查 XAML 屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以取得與您執行 XAML 程式碼的即時檢視**即時視覺化樹狀結構**並**即時屬性總管**。 這些工具提供您執行中之 XAML 應用程式 UI 項目的樹狀檢閱，並且顯示任何您所選取之 UI 項目的執行階段屬性。  
  
 您可以在下列設定中使用這些工具：  
  
|應用程式類型|作業系統與工具|  
|-----------------|--------------------------------|  
|Windows Presentation Foundation (4.0 和更新版本) 應用程式|Windows 7 和更新版本|  
|Windows 市集和 Windows Phone 8.1 應用程式|Windows 10 及更新版本，與[Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)|  
|通用 Windows 應用程式|Windows 10 及更新版本，與[Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)|  
  
## <a name="looking-at-elements-in-the-live-visual-tree"></a>查看即時視覺化樹狀中的項目  
 首先我們先來使用一個非常簡單的 WPF 應用程式，而該程式具有清單檢視和按鈕。 每當您按一下按鈕，就會將另一個項目加入清單。 偶數的項目以灰色顯示，而奇數項目則以黃色顯示。  
  
 建立新的 C# WPF 應用程式 ([檔案] / [新增] / [專案]，然後選取 [C#]，並尋找 [WPF 應用程式])。 命名**TestXAML**。  
  
 將 MainWindow.xaml 變更成如下：  
  
```xaml  
<Window x:Class="WpfApplication1.MainWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:local="clr-namespace:WpfApplication1"  
    mc:Ignorable="d"  
     Title="MainWindow" Height="350" Width="525">  
    <Grid>  
        <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>  
        <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>  
    </Grid>  
</Window>  
```  
  
 將下列的命令處理常式加入 MainWindow.xaml.cs 檔案：  
  
```csharp  
private void button_Click(object sender, RoutedEventArgs e)  
{  
    ListBoxItem item = new ListBoxItem();  
    item.Content = "Item" + ++count;  
    if (count % 2 == 0)  
    {  
        item.Background = Brushes.LightGray;  
    }  
    else  
    {  
        item.Background = Brushes.LightYellow;  
    }  
    listBox.Items.Add(item);  
}  
```  
  
 建置此專案並開始偵錯。 (組建組態必須為偵錯，而非發行。 如需組建組態的詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)。)  
  
 當視窗出現時，按一下**加入項目**按鈕數次。 您應該會看到類似下面的內容：  
  
 ![應用程式的主視窗](../debugger/media/livevisualtree-app.png "LiveVIsualTree 應用程式")  
  
 現在，請開啟**即時視覺化樹狀結構** 視窗 (**偵錯 / Windows / 即時視覺化樹狀結構**，或 IDE 左側找到它)。 將它拖曳離開停駐位置，讓我們來看看此視窗並**即時屬性**視窗並排顯示。 在 [**即時視覺化樹狀結構**] 視窗中，展開**ContentPresenter**節點。 其應包含按鈕和清單方塊的節點。 展開清單方塊 (然後**展開 ScrollContentPresenter**並**ItemsPresenter**) 來尋找清單方塊項目。 視窗類似下圖所示：  
  
 ![即時視覺化樹狀結構中的 ListBoxItems](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree ListBoxItems")  
  
 回到應用程式視窗並再加入一些項目。 您應該會看到更多的清單方塊項目，會出現在**即時視覺化樹狀結構**。  
  
 現在讓我們看看其中一個清單方塊項目的屬性。 選取中的第一個清單方塊項目**即時視覺化樹狀結構**然後按一下**顯示內容**工具列上的圖示。 **即時屬性總管**應該會出現。 請注意，**內容**欄位是"Item1"，而**背景**欄位 **#ffffffe0** （淺黃色）。 請返回**即時視覺化樹狀結構**，然後選取 第二個清單方塊項目。 **即時屬性總管**應該會顯示**內容**欄位是"Item2"，而**背景**欄位 **#ffd3d3d3** （淺灰色).  
  
 XAML 的實際結構有許多您可能不會直接感興趣的項目，且如果您不熟悉此程式碼，可能很難在巡覽樹狀時找到您要尋找的項目。 因此**即時視覺化樹狀結構**有幾種方式可讓您使用應用程式的 UI 來協助您找出您想要檢查的項目。  
  
 **啟用執行中應用程式中的選取範圍**。 當您選取最左邊的按鈕上時，即可啟用此模式**即時視覺化樹狀結構**工具列。 在此模式中，您可以選取 UI 項目中應用程式，而**即時視覺化樹狀結構**(而**即時屬性檢閱器**) 會自動更新以顯示節點在樹狀目錄中對應至該項目，和其屬性。  
  
 **執行的應用程式顯示版面配置提示**。 只要選取緊鄰 [啟用選取範圍] 按鈕右邊的按鈕時，即可啟用此模式。 當**顯示版面配置提示**已開啟，它會導致應用程式視窗中，若要顯示水平和垂直線條，沿著所選物件的界限，讓您可以看到什麼其向何處對齊，以及顯示此邊界的矩形。 比方說，同時開啟**啟用選取項目**並**顯示版面配置**，然後選取**加入項目**應用程式中的文字區塊。 您應該會看到的文字區塊節點**即時視覺化樹狀結構**的文字區塊的屬性和**即時屬性檢閱器**，以及文字區塊的範圍的水平和垂直格線。  
  
 ![LivePropertyViewer 中的 DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer 的 DisplayLayout")  
  
 **預覽選取範圍**。 只要選取 [即時視覺化樹狀] 工具列上從左邊數來的第三個按鈕，即可啟用這個模式。 如果您可存取該應用程式的原始程式碼，則此模式會顯示宣告此項目的 XAML。 選取**啟用選取項目**並**預覽選取範圍**，然後您在我們的測試應用程式，會在選取按鈕時。 MainWindow.xaml 檔案會在 Visual Studio 中開啟，而且游標會置於定義按鈕位置的那一行。  
  
## <a name="using-xaml-tools-with-running-applications"></a>搭配執行中的應用程式使用 XAML 工具  
 即使沒有原始程式碼，您仍可使用這些 XAML 工具。 當您附加至執行中 XAML 應用程式時，您可以使用**即時視覺化樹狀結構**上該應用程式的 UI 項目太。 以下範例使用的 WPF 測試應用程式和我們之前使用的相同。  
  
1.  開始**TestXaml**發行組態中的應用程式。 您無法附加至執行中的處理序**偵錯**組態。  
  
2.  開啟 Visual Studio 的第二個執行個體，然後按一下**偵錯] / [附加至處理序**。 尋找**TestXaml.exe**在清單中可用的處理序，然後按一下**附加**。  
  
3.  應用程式會開始執行。  
  
4.  在 Visual Studio 的第二個執行個體，開啟**即時視覺化樹狀結構**(**偵錯 / Windows / 即時視覺化樹狀結構**)。 您應該會看到**TestXaml** UI 項目，而且您應該能夠操作這些時直接偵錯應用程式一樣。



