---
title: 在調試時檢查 XAML 屬性 |Microsoft Docs
description: 瞭解如何在偵錯工具時使用即時視覺化樹狀結構和即時屬性瀏覽器工具來檢查 XAML 屬性，並取得 UI 元素的樹狀檢視。
ms.custom: SEO-VS-2020
ms.date: 03/02/2021
ms.topic: how-to
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: 86310346566e8c937c2769a9fcc9f0d4e98b3ae2
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308437"
---
# <a name="inspect-xaml-properties-while-debugging"></a>在偵錯時檢查 XAML 屬性

您可以使用 [即時視覺化樹狀結構] 和 [即時屬性總管] 來即時檢視正在執行的 XAML 程式碼。 這些工具提供您執行中之 XAML 應用程式 UI 項目的樹狀檢閱，並且顯示任何您所選取之 UI 項目的執行階段屬性。

您可以在下列設定中使用這些工具：

|應用程式類型|作業系統與工具|
|-----------------|--------------------------------|
|Windows Presentation Foundation (4.0 和更新版本) 應用程式|Windows 7 和更新版本|
|通用 Windows 應用程式|使用[WINDOWS 10 SDK](https://dev.windows.com/downloads/windows-10-sdk) Windows 10 和更新版本|

## <a name="look-at-elements-in-the-live-visual-tree"></a>查看即時視覺化樹狀結構中的元素

首先我們使用一個非常簡單的 WPF 應用程式，而該程式具有清單檢視和按鈕。 每當您按一下按鈕，就會將另一個項目加入清單。 偶數的項目以灰色顯示，而奇數項目則以黃色顯示。

### <a name="create-the-project"></a>建立專案

::: moniker range=">=vs-2019"

1. 建立新的 c # WPF 應用 **程式 (檔案** > **新增** > **專案**、輸入 "c # WPF"、選擇 [ **WPF 應用程式**] 專案範本、將專案命名為 **TestXAML**，然後確認 [**目標 Framework** ] 下拉式清單中是否出現 **.net Core 3.1** 。

::: moniker-end

::: moniker range="vs-2017"

1. 建立新的 c # WPF 應用 **程式 (檔案**  >  **新**  >  **專案**，然後輸入 "c # wpf"，然後選擇 [ **wpf 應用程式 ( .NET Framework)**) 。 將其命名為 **TestXAML**。

::: moniker-end

1. 將 MainWindow.xaml 變更成如下：

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

1. 將下列的命令處理常式加入 MainWindow.xaml.cs 檔案：

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

1. 建置此專案並開始偵錯。 (組建組態必須為偵錯，而非發行。 如需組建組態的詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)。)

   當視窗出現時，您應該會看到應用程式中的工具列出現在執行中的應用程式內。

   ::: moniker range=">= vs-2019"
   ![應用程式的主視窗](../debugger/media/vs-2019/livevisualtree-app.png "LiveVIsualTree-App")
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![應用程式的主視窗](../debugger/media/livevisualtree-app.png "LiveVIsualTree-App")
   ::: moniker-end

1. 現在，按一下 [ **新增專案** ] 按鈕幾次，即可將新專案加入清單中。

### <a name="inspect-xaml-properties"></a>檢查 XAML 屬性

1. 接著，按一下應用程式內工具列 (或移至 [ **> Windows > 即時視覺化樹狀**]) ，開啟 [**即時視覺化樹狀結構**] 視窗。 開啟後，將其從停駐位置拖曳出，讓我們可以並排查看此視窗和 [ **即時屬性** ] 視窗。

1. 在 [即時視覺化樹狀結構] 視窗中，展開 [ContentPresenter] 節點。 其應包含按鈕和清單方塊的節點。 展開清單方塊 (然後展開 [ScrollContentPresenter] 和 [ItemsPresenter]) 來尋找清單方塊項目。

   ::: moniker range=">= vs-2019"
   如果您沒有看到 [ **ContentPresenter** ] 節點，請切換工具列上的 [ **僅顯示我的 XAML** ] 圖示。 從 Visual Studio 2019 16.4 版開始，XAML 專案的觀看預設會使用 [僅我的 XAML] 功能來簡化。 您也可以在 [選項] 中 [停用這項設定](../debugger/general-debugging-options-dialog-box.md) ，永遠顯示所有的 XAML 元素。
   ::: moniker-end

   視窗類似下圖所示：

   ::: moniker range=">= vs-2019"
   ![即時視覺化樹狀結構中的 ListBoxItems](../debugger/media/vs-2019/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![即時視覺化樹狀結構中的 ListBoxItems](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")
   ::: moniker-end

1. 回到應用程式視窗並再加入一些項目。 您應該會看到多個清單方塊項目出現在 [即時視覺化樹狀結構] 中。

1. 現在，讓我們看看其中一個清單方塊專案的屬性。

   選取 [即時視覺化樹狀結構] 中的第一個清單方塊項目，然後按一下工具列上的 **顯示屬性** 圖示。 應該就會顯示 [即時屬性總管]。 請注意，[**內容**] 欄位是 "Item1"，而 **背景**  >  **色彩** 欄位是 **#FFFFFFE0**。

1. 返回 [即時視覺化樹狀結構] 並選取第二個清單方塊項目。 [**即時屬性瀏覽器**] 應該會顯示 [**內容**] 欄位是 "Item2"，而 [**背景**  >  **色彩**] 欄位則是根據主題) 而 **#FFD3D3D3** (。

   > [!NOTE]
   > **即時屬性瀏覽器** 中的屬性周圍有一個黃色框線，表示屬性值是透過系結（例如）設定 `Color = {BindingExpression}` 。 綠色框線表示值是使用資源（例如）設定 `Color = {StaticResource MyBrush}` 。

   XAML 的實際結構有許多您可能不會直接感興趣的項目，如果您不熟悉此程式碼，可能很難在巡覽樹狀結構時找到您要尋找的項目。 因此 [即時視覺化樹狀結構] 有好幾種方式可讓您使用應用程式的 UI 來協助找出您想要檢查的項目。

   ::: moniker range=">= vs-2019"
   **選取執行中應用程式的元素**。 只要選取 [即時視覺化樹狀結構] 工具列最左邊的按鈕，即可啟用此模式。 啟用此模式後，您便可以在應用程式中選取 UI 項目，而 [即時視覺化樹狀結構] (和 [即時屬性檢閱器]) 會自動更新，以顯示樹狀結構中的節點對應至該項目及其屬性。 從 Visual Studio 2019 版本16.4 開始，您可以 [設定元素選取的行為](../debugger/general-debugging-options-dialog-box.md)。

   **在執行中應用程式顯示版面配置提示**。 只要選取緊鄰 [啟用選取範圍] 按鈕右邊的按鈕時，即可啟用此模式。 [顯示版面配置提示] 開啟時，會使此應用程式視窗沿著所選取物件的界限顯示水平及垂直線條，讓您能夠查看其向何處對齊，以及查看顯示此邊界的矩形。 例如，開啟 [ **選取** 專案] 和 [ **顯示版面** 配置]，然後選取應用程式中的 [ **加入專案** ] 文字區塊。 您應該會看到 [即時視覺化樹狀結構] 中的文字區塊節點和 [即時屬性檢閱器] 中的文字區塊屬性，以及文字區塊界限內的水平和垂直線條。

   ![LivePropertyViewer 中的 DisplayLayout](../debugger/media/vs-2019/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

   **預覽選取範圍**。 只要選取 [即時視覺化樹狀] 工具列上從左邊數來的第三個按鈕，即可啟用這個模式。 如果您可存取該應用程式的原始程式碼，則此模式會顯示宣告此項目的 XAML。 選取 [ **選取** 專案] 和 [ **預覽選取範圍**]，然後選取測試應用程式中的按鈕。 MainWindow.xaml 檔案會在 Visual Studio 中開啟，而且游標會置於定義按鈕位置的那一行。
   ::: moniker-end

   ::: moniker range="vs-2017"
   **啟用執行中應用程式的選項**。 只要選取 [即時視覺化樹狀結構] 工具列最左邊的按鈕，即可啟用此模式。 啟用此模式後，您便可以在應用程式中選取 UI 項目，而 [即時視覺化樹狀結構] (和 [即時屬性檢閱器]) 會自動更新，以顯示樹狀結構中的節點對應至該項目及其屬性。

   **在執行中應用程式顯示版面配置提示**。 只要選取緊鄰 [啟用選取範圍] 按鈕右邊的按鈕時，即可啟用此模式。 [顯示版面配置提示] 開啟時，會使此應用程式視窗沿著所選取物件的界限顯示水平及垂直線條，讓您能夠查看其向何處對齊，以及查看顯示此邊界的矩形。 例如，同時開啟 [啟用選取範圍] 和 [顯示版面配置]，並在應用程式中選取 [新增項目] 文字區塊。 您應該會看到 [即時視覺化樹狀結構] 中的文字區塊節點和 [即時屬性檢閱器] 中的文字區塊屬性，以及文字區塊界限內的水平和垂直線條。

   ![LivePropertyViewer 中的 DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

   **預覽選取範圍**。 只要選取 [即時視覺化樹狀] 工具列上從左邊數來的第三個按鈕，即可啟用這個模式。 如果您可存取該應用程式的原始程式碼，則此模式會顯示宣告此項目的 XAML。 選取 [啟用選取範圍] 和 [預覽選取範圍]，然後選取在我們測試應用程式中的按鈕。 MainWindow.xaml 檔案會在 Visual Studio 中開啟，而且游標會置於定義按鈕位置的那一行。
   ::: moniker-end

## <a name="use-xaml-tools-with-running-applications"></a>搭配執行中的應用程式使用 XAML 工具

即使沒有原始程式碼，您仍可使用這些 XAML 工具。 當您附加至執行中 XAML 應用程式時，您也可以使用該應用程式 UI 項目上的 [即時視覺化樹狀結構]。 以下範例使用的 WPF 測試應用程式和我們之前使用的相同。

1. 在 [發行] 組態中啟動 **TestXaml** 應用程式。 您無法附加至正在 [偵錯] 組態中執行的處理序。

2. 開啟第二個 Visual Studio 執行個體，然後按一下 [偵錯] > [附加至處理序]。 在可用的處理序清單中尋找 **TestXaml.exe**，然後按一下 [附加]。

3. 應用程式會開始執行。

4. 在 Visual Studio 的第二個執行個體中，開啟 [即時視覺化樹狀結構] ([偵錯] > [視窗] > [即時視覺化樹狀結構])。 您應該會看到 **TestXaml** UI 項目，且應該可以如同直接對應用程式進行偵錯時一樣管理這些項目。

## <a name="see-also"></a>另請參閱

[使用 XAML 熱重新載入撰寫和偵測執行中的 XAML 程式碼](xaml-hot-reload.md)
