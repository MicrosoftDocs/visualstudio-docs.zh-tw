---
title: 使用設計階段範例資料搭配中的 XAML 設計工具 Visual Studio
description: 瞭解如何在 XAML 中使用設計階段範例資料。
ms.date: 05/28/2021
ms.topic: conceptual
author: alihamie
ms.author: tglee
manager: jmartens
monikerRange: vs-2019
ms.openlocfilehash: a987435d454771bdecf078e78af089405718d261
ms.sourcegitcommit: 5366c6bca3fb217a2fbf847998387578f51ec45c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748072"
---
# <a name="use-design-time-sample-data-with-the-xaml-designer-in-visual-studio"></a>使用設計階段範例資料搭配中的 XAML 設計工具 Visual Studio

某些資料相依的控制項（例如 ListView、ListBox 或 DataGrid）很難在沒有資料的情況下呈現。 在本檔中，我們將探討可讓開發人員使用 **wpf .Net Core** 專案或 **wpf .NET Framework** 專案的新方法，並以新的設計工具來啟用這些控制項中的範例資料。 

## <a name="sample-data-feature-basics"></a>範例資料功能基本概念

範例資料僅適用于設計階段視覺效果，這表示它只會出現在 XAML 設計工具中，而不會出現在執行中的應用程式。 因此，它會套用至 ItemsSource 屬性的設計階段版本 `d:ItemsSource` 。 範例資料需要設計階段命名空間才能運作。 若要開始使用，請將下列程式程式碼新增至 XAML 檔的標頭（如果尚未存在）：

> [!NOTE]
> 流覽 [xaml 設計階段屬性](/xaml/xaml-tools/xaml/xaml-designtime-data.md) ，以深入瞭解 xaml 中的設計階段屬性。

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

新增命名空間之後，您可以使用 `d:ItemsSource="{d:SampleData}"` 來啟用 ListView、Listbox 或 DataGrid 中的範例資料。 例如︰

```xml
<DataGrid d:ItemsSource="{d:SampleData}"/>
```

[![使用 DataGrid 的範例資料](media\xaml-sample-data-empty-datagrid.png "DataGrid 上啟用的範例資料")](media\xaml-sample-data-empty-datagrid.png#lightbox)

在此範例中，沒有 `d:ItemsSource="{d:SampleData}"` XAML 設計工具會顯示空白的 DataGrid。 相反地， `d:SampleData` 現在會顯示產生的預設範例資料。

依預設，會顯示5個專案。 不過，您可以使用 **ItemCount** 屬性來指定您要顯示的專案數目。 例如： `d:ItemsSource="{d:SampleData ItemCount=2}"`

## <a name="sample-data-works-with-datatemplates"></a>範例資料適用于 datatemplates

當您使用資料範本時，範例資料適用于 ListBox、ListView 或 DataGrid 控制項。 範例資料功能會分析 DataTemplate，並嘗試為其產生適當的資料。 只會針對使用系結之 DataTemplates 中的元素產生範例資料。 即使系結尚無來源，也會產生範例資料。
例如︰

```xml
<ListView d:ItemsSource="{d:SampleData ItemCount=3}">
     <ListView.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
                <Image Width="50" Source="{Binding ProfilePicture}"/>
                <StackPanel Orientation="Vertical">
                    <TextBlock Text="{Binding FirstName}" Margin="5"/>
                    <Label Content="{Binding LastName}"/>
                </StackPanel>
            </StackPanel>
        </DataTemplate>
    </ListView.ItemTemplate>
</ListView>
```

[![使用 DataTemplate 的範例資料 ListView](media\xaml-sample-data-templated-listview.png "使用 DataTemplate 的 ListView 中所使用的範例資料")](media\xaml-sample-data-templated-listview.png#lightbox)

## <a name="enable-sample-data-with-suggested-actions"></a>使用建議的動作啟用範例資料

若要從設計工具輕鬆地啟用或停用控制項的範例資料，您可以使用建議的動作功能。 建議的動作是設計工具上的燈泡，當您選取控制項時，會顯示在右上方。 您可以藉由選取控制項、按一下燈泡，然後按一下 [開啟]，來啟用範例資料 `Show Sample Data` 。 例如︰

[![範例資料建議的動作](media\xaml-sample-data-suggested-actions.png "使用建議的動作啟用範例資料")](media\xaml-sample-data-suggested-actions.png#lightbox)

## <a name="sample-data-with-ivalueconverters"></a>使用 IValueConverters 的範例資料 

範例資料功能並未完全支援轉換器。 不過，您可以執行下列其中一項或兩項作業，以使其運作：
- 確定您的函式 `Convert` 可以處理值已是您 targetType 的案例。

- 執行 `ConvertBack` 會將您的值轉換回原始類型的函式。 

## <a name="troubleshooting"></a>疑難排解

如果您的範例資料未顯示任何資料，或無法顯示正確的類型，您可以嘗試重新整理設計工具或關閉並重新開啟頁面。

如果您遇到本節未列出的問題，或者重新整理頁面無法修正問題，請使用 [回報 [問題](../ide/how-to-report-a-problem-with-visual-studio.md) ] 工具讓我們知道。

### <a name="requirements"></a>規格需求

- 範例資料需要 Visual Studio 2019 [16.10](/visualstudio/releases/2019/release-notes-v16.10) 版或更新版本。

- 使用新的設計工具時，支援以適用于 .NET Core 的 Windows Presentation Foundation (WPF) 或 .NET Framework 為目標的 Windows 桌面專案。 若要啟用 .NET Framework 的新設計工具，請移至 [工具] > [選項] > 環境 > 預覽功能]，選取 [新增 WPF XAML 設計工具進行 .NET Framework]，然後重新開機 Visual Studio。

## <a name="see-also"></a>另請參閱

- [XAML 設計階段屬性](/xaml/xaml-tools/xaml/xaml-designtime-data)
- [WPF 應用程式中的 XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP 應用程式中的 XAML](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms 應用程式中的 XAML](/xamarin/xamarin-forms/xaml/)