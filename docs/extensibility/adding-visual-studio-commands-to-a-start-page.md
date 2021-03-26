---
title: 將 Visual Studio 命令新增至起始頁 |Microsoft Docs
description: 瞭解在 Visual Studio 的自訂起始頁上，將 Visual Studio 命令系結至 XAML 物件的不同方式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 4e2ec238d3cb8c2e7d843018fc45e97207c6d5f4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097522"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>將 Visual Studio 命令新增至起始頁

當您建立自訂起始頁時，可以在其中新增 Visual Studio 命令。 本檔討論在起始頁上將 Visual Studio 命令系結至 XAML 物件的不同方式。

如需 XAML 中命令的詳細資訊，請參閱 [命令總覽](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>從命令妥善新增命令

在 [ [建立自訂起始頁](../extensibility/creating-a-custom-start-page.md) ] 中建立的起始頁加入了 <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> 和 <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> 命名空間，如下所示。

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

從元件 *Microsoft.VisualStudio.Shell.Immutable.11.0.dll* 新增 VisualStudio 的另一個命名空間。  (您可能需要在您的專案中新增此元件的參考。 ) 

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

您可以使用別名，將 `vscom:` 控制項的屬性設定為，以將 Visual Studio 命令系結至頁面上的 XAML 控制項 <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> `vscom:VSCommands.ExecuteCommand` 。 然後，您可以將 <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> 屬性設定為要執行的命令名稱，如下列範例所示。

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> 在 `x:` 所有命令的開頭都需要別名（參考 XAML 架構）。

 您可以將屬性的值設定 `Command` 為可從 **命令** 視窗存取的任何命令。 如需可用命令的清單，請參閱 [Visual Studio 命令別名](../ide/reference/visual-studio-command-aliases.md)。

 如果要新增的命令需要額外的參數，您可以將它新增至屬性的值 `CommandParameter` 。 使用空格將參數與命令分開，如下列範例所示。

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>從命令部分呼叫延伸模組
 您可以使用用來呼叫其他 Visual Studio 命令的相同語法，從已註冊的 Vspackage 呼叫命令。 例如，如果已安裝的 VSPackage 將 **首頁** 命令新增至 [ **View** ] 功能表，您可以藉由將設定為來呼叫該命令 `CommandParameter` `View.HomePage` 。

> [!NOTE]
> 如果您呼叫與 VSPackage 相關聯的命令，則在叫用命令時必須載入此封裝。

## <a name="add-commands-from-assemblies"></a>從元件新增命令
 若要從元件呼叫命令，或存取未與功能表命令相關聯之 VSPackage 中的程式碼，您必須建立元件的別名，然後呼叫別名。

### <a name="to-call-a-command-from-an-assembly"></a>從元件呼叫命令

1. 在您的方案中，加入元件的參考。

2. 在 *StartPage* 檔案的頂端，加入元件的命名空間指示詞，如下列範例所示。

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. 藉由設定 `Command` XAML 物件的屬性來叫用命令，如下列範例所示。

     Xaml

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> 您必須複製元件，然後將它貼到 * 中。 \\{Visual Studio 安裝資料夾} \Common7\IDE\PrivateAssemblies \* ，以確定它會在呼叫之前先進行載入。

## <a name="add-commands-with-the-dte-object"></a>新增具有 DTE 物件的命令
 您可以從起始頁（在標記和程式碼中）存取 DTE 物件。

 在標記中，您可以使用系結 [標記延伸](/dotnet/framework/wpf/advanced/binding-markup-extension) 語法呼叫物件來存取它 <xref:EnvDTE.DTE> 。 您可以使用這個方法系結至簡單的屬性，例如傳回集合的屬性，但是您無法系結至方法或服務。 下列範例顯示系結 <xref:System.Windows.Controls.TextBlock> 至屬性的控制項 <xref:EnvDTE._DTE.Name%2A> ，以及 <xref:System.Windows.Controls.ListBox> 列舉屬性所 <xref:EnvDTE.Window.Caption%2A> 傳回之集合屬性的控制項 <xref:EnvDTE._DTE.Windows%2A> 。

```xml
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>
<ListBox ItemsSource="{Binding Path=DTE.Windows}">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding Path=Caption}"/>
        </DataTemplate>
    </ListBox.ItemTemplate>
</ListBox
```

 如需範例，請參閱 [逐步解說：在起始頁儲存使用者設定](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)。

## <a name="see-also"></a>另請參閱

- [將使用者控制項新增至起始頁](../extensibility/adding-user-control-to-the-start-page.md)
