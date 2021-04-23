---
title: 使用 XAML 設計工具的設計階段資料 Visual Studio
description: 瞭解如何在 XAML 中使用設計階段資料。
ms.date: 11/17/2020
ms.topic: overview
author: alihamie
ms.author: tglee
manager: jmartens
monikerRange: vs-2019
ms.openlocfilehash: 915fe38da63f0b3994a809b20515fdc18e0790ce
ms.sourcegitcommit: 5fb684ff8729eb118aa91ce9f049c79eeb9747b1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2021
ms.locfileid: "107913068"
---
# <a name="use-design-time-data-with-the-xaml-designer-in-visual-studio"></a>使用 XAML 設計工具的設計階段資料 Visual Studio

某些版面配置很難在沒有資料的情況下視覺化。 在這份檔中，我們將審視一個開發桌面專案的開發人員可以用來模擬 XAML 設計工具中資料的方法。 這種方法是使用現有的可忽略 "d：" 命名空間來完成。 使用這個方法，您可以快速地將設計階段資料加入至您的頁面或控制項，而不需要建立完整的模擬 ViewModel，或只需測試屬性變更可能會對您的應用程式造成什麼影響，而不必擔心這些變更會影響您的發行組建。 所有 d：資料只會由 XAML 設計工具使用，且不會將可忽略的命名空間值編譯到應用程式中。

> [!NOTE]
> 如果您使用的是 Xamarin，請參閱 [xamarin. Forms 設計階段資料](/xamarin/xamarin-forms/xaml/xaml-previewer/design-time-data)

## <a name="design-time-data-basics"></a>設計階段資料基本概念

設計階段資料是您設定的模擬資料，可讓您更輕鬆地在 XAML 設計工具中將控制項視覺化。 若要開始使用，請將下列程式程式碼新增至 XAML 檔的標頭（如果尚未存在）：

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

新增命名空間之後，您可以將 `d:` 它放在任何屬性或控制項之前，以便只在 XAML 設計工具中顯示，但不能在執行時間顯示。

例如，您可以將文字新增至通常有資料系結的 TextBlock。

```xml
<TextBlock Text="{Binding Name}" d:Text="Name!" />
```

[![使用 TextBlock 中的文字設計階段資料](media\xaml-design-time-textblock.png "使用文字 a 標籤的設計階段資料")](media\xaml-design-time-textblock.png#lightbox)

在此範例中，如果沒有 `d:Text` ，XAML 設計工具將不會顯示 TextBlock 的任何內容。 相反地，它會顯示「名稱！」 TextBlock 在執行時間會有實際的資料。

您可以 `d:` 針對任何 UWP 或 WPF .Net Core 控制項使用 with 屬性，例如色彩、字型大小及間距。 您甚至可以將它加入控制項本身。

```xml
<d:Button Content="Design Time Button" />
```

[![具有按鈕控制項的設計階段資料](media\xaml-design-time-button.png "具有按鈕控制項的設計階段資料")](media\xaml-design-time-button.png#lightbox)

在此範例中，按鈕只會出現在設計階段。 您可以使用這個方法，將預留位置放入自訂控制項，或試用不同的控制項。 所有 `d:` 屬性和控制項在執行時間都會被忽略。

## <a name="preview-images-at-design-time"></a>在設計階段預覽影像

您可以針對系結至頁面或動態載入的影像，設定設計階段來源。 將您想要在 XAML 設計工具中顯示的影像新增至您的專案。 然後，您可以在設計階段于 XAML 設計工具中顯示該影像：

```xml
<Image Source={Binding ProfilePicture} d:Source="DesignTimePicture.jpg" />
```

> [!NOTE]
> 此範例中的影像必須存在於方案中。

## <a name="design-time-data-for-listviews"></a>Listview 的設計階段資料

Listview 是在桌面應用程式中顯示資料的常用方式。 不過，它們不會在沒有任何資料的情況下進行視覺化。 您可以使用這項功能來建立內嵌設計階段資料 ItemSource 或專案。 XAML 設計工具會在設計階段顯示 ListView 中該陣列的內容。

### <a name="wpf-net-core--example"></a>WPF .NET Core 範例
若要使用 system： String 類型，請確定您已 `xmlns:system="clr-namespace:System;assembly=mscorlib` 在 XAML 標頭中包含。

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type system:String}">
                <system:String>Item One</system:String>
                <system:String>Item Two</system:String>
                <system:String>Item Three</system:String>
            </x:Array>
        </d:ListView.ItemsSource>
    <ListView.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding ItemName}" d:Text="{Binding .}" />
        </DataTemplate>
    </ListView.ItemTemplate>
   </ListView>
</StackPanel>
```

[![使用 ListView 的設計階段資料](media\xaml-design-time-listview-strings.png "使用 ListView 的設計階段資料")](media\xaml-design-time-listview-strings.png#lightbox)

上述範例顯示 XAML 設計工具中有三個 Textblock 的 ListView。

您也可以建立資料物件的陣列。 例如，您 `City` 可以將資料物件的公用屬性視為設計階段資料。

```csharp
namespace Cities.Models
{
    public class City
    {
        public string Name { get; set; }
        public string Country { get; set; }
    }
}
```

若要在 XAML 中使用類別，您必須在根節點中匯入命名空間。

```xaml
xmlns:models="clr-namespace:Cities.Models"
```

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type models:City}">
                <models:City Name="Seattle" Country="United States"/>
                <models:City Name="London" Country="United Kingdom"/>
                <models:City Name="Panama City" Country="Panama"/>
            </x:Array>
        </d:ListView.ItemsSource>
        <ListView.ItemTemplate>
            <DataTemplate>
                 <StackPanel Orientation="Horizontal" >
                    <TextBlock Text="{Binding Name}" Margin="0,0,5,0" />
                    <TextBlock Text="{Binding Country}" />
                 </StackPanel>
            </DataTemplate>
        </ListView.ItemTemplate>
    </ListView>
</StackPanel>
```

[![使用 ListView 設計階段資料中的實際模型](media\xaml-design-time-listview-models.png "使用 ListView 的實際模型設計階段資料")](media\xaml-design-time-listview-models.png#lightbox)

這裡的好處是您可以將控制項系結至模型的設計階段靜態版本。

### <a name="uwp-example"></a>UWP 範例 

UWP 中不支援 x:Array。 因此，我們可以 `<d:ListView.Items>` 改用。 若要使用 system： String 類型，請確定您已 `http://schemas.microsoft.com/winfx/2009/xaml` 在 XAML 標頭中包含。

```xml
    <StackPanel>
        <ListView>
            <d:ListView.Items>
                <system:String>Item One</system:String>
                <system:String>Item Two</system:String>
                <system:String>Item Three</system:String>
            </d:ListView.Items>
        </ListView>
    </StackPanel>
```

## <a name="use-design-time-data-with-custom-types-and-properties"></a>使用自訂類型和屬性的設計階段資料

這項功能預設僅適用于平臺控制項和屬性。 在本節中，我們將探討讓您將自訂控制項用作設計階段控制項的必要步驟，這是使用 Visual Studio 2019 [16.8](/visualstudio/releases/2019/release-notes/) 版或更新版本的客戶可使用的新功能。 啟用這項操作有三個需求：

- 自訂 xmlns 命名空間

    ```xml
    xmlns:myControls="http://MyCustomControls"
    ```

- 命名空間的設計階段版本。 這可以藉由直接在結尾附加/design 來達成。

     ```xml
    xmlns:myDesignTimeControls="http://MyCustomControls/design"
    ```

- 將您的設計階段前置詞加入至 mc：可忽略

    ```xml
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d myDesignTimeControls"
    ```

完成上述所有步驟之後，您可以使用 `myDesignTimeControls` 前置詞來建立設計階段控制項。

```xml
<myDesignTimeControls:MyButton>I am a design time Button</myDesignTimeControls:MyButton>
```

### <a name="creating-a-custom-xmlns-namespace"></a>建立自訂 xmlns 命名空間

若要在 WPF .NET Core 中建立自訂 xmlns 命名空間，您必須將自訂 XML 命名空間對應至控制項所在的 CLR 命名空間。 您可以 `XmlnsDefinition` 在檔案中加入元件層級屬性來完成這項作業 `AssemblyInfo.cs` 。 檔案會在專案的根階層中找到。

   ```C#
[assembly: XmlnsDefinition("http://MyCustomControls", "MyViews.MyButtons")]
   ```

## <a name="troubleshooting"></a>疑難排解

如果您遇到本節未列出的問題，請使用「回報 [問題](../ide/how-to-report-a-problem-with-visual-studio.md) 」工具讓我們知道。

### <a name="requirements"></a>規格需求

- 設計階段資料需要 Visual Studio 2019 [16.7](/visualstudio/releases/2019/release-notes-v16.7) 版或更新版本。

- 支援以適用于 .NET Core 和 UWP 的 Windows Presentation Foundation (WPF) 為目標的 Windows 桌面專案。 這項功能也適用于 [預覽通道](/visualstudio/releases/2019/release-notes-preview)中的 .NET Framework。 若要啟用它，請移至 [**工具**  >  **選項**  >  **環境**  >  **預覽功能**]，選取 [**新增 WPF XAML 設計工具進行 .NET Framework** ，然後重新開機 Visual Studio。

- 從 Visual Studio 2019 16.7 版開始，此功能可與 WPF 和 UWP 架構中的所有現成控制項搭配使用。 [16.8 版](/visualstudio/releases/2019/release-notes/)現在提供協力廠商控制項的支援。

### <a name="the-xaml-designer-stopped-working"></a>XAML 設計工具已停止運作

請嘗試關閉並重新開啟 XAML 檔案，並清除並重建您的專案。

## <a name="see-also"></a>另請參閱

- [使用 Xamarin 預覽設計階段資料](/xamarin/xamarin-forms/xaml/xaml-Designer/design-time-data/)
- [WPF 應用程式中的 XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP 應用程式中的 XAML](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms 應用程式中的 XAML](/xamarin/xamarin-forms/xaml/)