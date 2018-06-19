---
title: 偵錯時檢查 XAML 屬性 |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: fcb2877a79afc310985102972d870caae560b393
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480211"
---
# <a name="inspect-xaml-properties-while-debugging"></a>在偵錯時檢查 XAML 屬性
您可以取得與您執行的 XAML 程式碼的即時檢視**即時視覺化樹狀結構**和**即時屬性總管**。 這些工具提供您執行中之 XAML 應用程式 UI 項目的樹狀檢閱，並且顯示任何您所選取之 UI 項目的執行階段屬性。  
  
 您可以在下列設定中使用這些工具：  
  
|應用程式類型|作業系統與工具|  
|-----------------|--------------------------------|  
|Windows Presentation Foundation (4.0 和更新版本) 應用程式|Windows 7 和更新版本|  
|通用 Windows 應用程式|Windows 10 和更新版本，與[Windows 10 SDK](https://dev.windows.com/en-us/downloads/windows-10-sdk)|  
  
## <a name="looking-at-elements-in-the-live-visual-tree"></a>查看即時視覺化樹狀中的項目  
 讓我們開始使用非常簡單的 WPF 應用程式具有清單檢視和按鈕。 每當您按一下按鈕，就會將另一個項目加入清單。 偶數的項目以灰色顯示，而奇數項目則以黃色顯示。  
  
 建立新的 C# WPF 應用程式 (檔案 > 新增 > 專案，然後選取 C# 和尋找 WPF 應用程式)。 命名**TestXAML**。  
  
 將 MainWindow.xaml 變更成如下：  
  
```xaml  
<Window x:Class="TestXAML.MainWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:local="clr-namespace:TestXAML"  
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
int count;

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
  
 建置此專案並開始偵錯。 (組建組態必須為偵錯，而非發行。 如需建置組態的詳細資訊，請參閱[了解建置組態](../ide/understanding-build-configurations.md)。)  
  
 當視窗出現時，按一下 **加入項目**按鈕數次。 您應該會看到類似下面的內容：  
  
 ![應用程式的主視窗](../debugger/media/livevisualtree-app.png "LiveVIsualTree 應用程式")  
  
 現在開啟**即時視覺化樹狀結構**視窗 (**偵錯 > Windows > 即時視覺化樹狀結構**，或沿著此 IDE 的左側尋找)。 將它拖曳離開停駐位置，讓我們來看看此視窗和**即時屬性**視窗並排顯示。 在**即時視覺化樹狀結構**視窗中，展開  **ContentPresenter**節點。 其應包含按鈕和清單方塊的節點。 展開清單方塊 (然後**展開 ScrollContentPresenter**和**ItemsPresenter**) 來尋找清單方塊項目。 視窗類似下圖所示：  
  
 ![即時視覺化樹狀結構中的 ListBoxItems](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree ListBoxItems")  
  
 回到應用程式視窗並再加入一些項目。 您應該會看到更多的清單方塊項目，會出現在**即時視覺化樹狀結構**。  
  
 現在讓我們看看其中一個清單方塊項目的屬性。 選取第一個清單方塊項目中的**即時視覺化樹狀結構**按一下**顯示屬性**工具列上的圖示。 **即時屬性總管**應該會出現。 請注意，**內容**欄位是"Item1"，而**背景**欄位是 **#FFFFFFE0** （淺黃色）。 請返回**即時視覺化樹狀結構**並選取第二個清單方塊項目。 **即時屬性總管**應該會顯示**內容**欄位是"Item2"，而**背景**欄位是 **#FFD3D3D3** （淺灰色).  
  
 XAML 的實際結構有許多您可能不是直接興趣的項目，如果您不熟悉程式碼您可能會很難在巡覽樹狀結構時找到您要尋找的。 所以**即時視覺化樹狀結構**有好幾種方式可讓您使用應用程式的 UI 來協助您找出您想要檢查的項目。  
  
 **在執行中應用程式中啟用選取**。 當您選取最左邊的按鈕上時，即可啟用此模式**即時視覺化樹狀結構**工具列。 使用此模式後，您可以選取 UI 項目在應用程式，而**即時視覺化樹狀結構**(和**即時屬性檢閱器**) 會自動更新以顯示的節點在樹狀目錄中對應至該項目，和其屬性。  
  
 **在執行中應用程式顯示版面配置提示**。 只要選取緊鄰 [啟用選取範圍] 按鈕右邊的按鈕時，即可啟用此模式。 當**顯示版面配置提示**已開啟，它會導致應用程式視窗以顯示所選物件的界限沿著水平和垂直線條，好讓您可以看到什麼其向何處對齊，以及顯示此邊界的矩形。 例如，同時開啟**啟用選取**和**顯示版面配置**，並選取**加入項目**應用程式中的文字區塊。 您應該會看到中的文字區塊節點**即時視覺化樹狀結構**和中的文字區塊屬性**即時屬性檢閱器**，以及文字區塊界限內的水平和垂直線條。  
  
 ![在 DisplayLayout LivePropertyViewer](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer DisplayLayout")  
  
 **預覽選取範圍**。 只要選取 [即時視覺化樹狀] 工具列上從左邊數來的第三個按鈕，即可啟用這個模式。 如果您可存取該應用程式的原始程式碼，則此模式會顯示宣告此項目的 XAML。 選取**啟用選取**和**預覽選取範圍**，然後在測試應用程式中選取 [] 按鈕。 MainWindow.xaml 檔案會在 Visual Studio 中開啟，而且游標會置於定義按鈕位置的那一行。  
  
## <a name="using-xaml-tools-with-running-applications"></a>搭配執行中的應用程式使用 XAML 工具  
 即使沒有原始程式碼，您可以使用這些 XAML 工具。 當您附加至執行中 XAML 應用程式時，您可以使用**即時視覺化樹狀結構**上該應用程式的 UI 項目太。 以下是使用相同我們之前使用的 WPF 測試應用程式的範例。  
  
1.  啟動**TestXaml**發行組態中的應用程式。 您無法附加至執行中的處理序**偵錯**組態。  
  
2.  開啟 Visual Studio 的第二個執行個體，然後按一下**偵錯 > 附加至處理序**。 尋找**TestXaml.exe**可用的處理序，然後按一下清單中**附加**。  
  
3.  應用程式會開始執行。  
  
4.  在 Visual Studio 的第二個執行個體，開啟**即時視覺化樹狀結構**(**偵錯 > Windows > 即時視覺化樹狀結構**)。 您應該會看到**TestXaml** UI 項目，而且您應該要能夠直接偵錯應用程式時一樣管理它們。