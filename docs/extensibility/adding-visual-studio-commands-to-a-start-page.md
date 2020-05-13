---
title: 將可視化工作室命令添加到「開始」頁面 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 13dd40006039209b06cc6a71760fdbaa240db4fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740121"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>將視覺化工作室指令加入到「開始」頁

創建自訂「開始頁」時,可以將 Visual Studio 命令添加到其中。 本文件討論了將 Visual Studio 命令綁定到「開始」頁上的 XAML 物件的不同方法。

有關 XAML 中指令的詳細資訊,請參閱[命令概述](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>從命令井新增命令

在[創建自訂「開始頁」](../extensibility/creating-a-custom-start-page.md)中創建的「<xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>開始<xref:Microsoft.VisualStudio.Shell?displayProperty=fullName>頁 」 添加了和命名空間,如下所示。

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

從程式集微軟 *.VisualStudio.Shell*添加另一個命名空間。 (您可能需要在專案中添加對此程式集的引用。

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

以將控制項`vscom:`<xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A>的屬性設定為,可以使用別名將 Visual Studio 命令繫結至頁面上的 XAML 控制件`vscom:VSCommands.ExecuteCommand`。 然後,<xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>您可以將該屬性設置為要執行的命令的名稱,如以下範例所示。

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> 該`x:`別名(引用 XAML 架構)在所有命令的開頭都是必需的。

 您可以將`Command`屬性的值設定為可以從**命令**視窗存取的任何命令。 有關可用的指令清單,請參閱[可視化工作室命令別名](../ide/reference/visual-studio-command-aliases.md)。

 如果要添加的命令需要其他參數,則可以將其添加到`CommandParameter`屬性的值。 通過使用空格將參數與命令分開,如以下示例所示。

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>從命令井呼叫分機
 您可以使用用於呼叫其他 Visual Studio 命令的相同語法從已註冊的 VSPackages 調用命令。 例如,如果已安裝的 VSPackage 將**主頁**命令添加到 **「檢視」** 選單中`CommandParameter`,則可以`View.HomePage`通過設定為調用該 命令。

> [!NOTE]
> 如果調用與 VSPackage 關聯的命令,則必須在調用該命令時載入套件。

## <a name="add-commands-from-assemblies"></a>從程式集加入指令
 要從程式集調用命令,或訪問未與功能表命令關聯的 VSPackage 中的代碼,必須為程式集創建別名,然後調用別名。

### <a name="to-call-a-command-from-an-assembly"></a>從程式集呼叫指令

1. 在解決方案中,添加對程式集的引用。

2. 在*StartPage.xaml*檔的頂部,為程式集添加命名空間指令,如以下範例所示。

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. 通過設置 XAML`Command`物件的屬性來調用命令,如以下示例所示。

     Xaml

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> 您必須複製程式集,然後將其貼上至 *中。\\{可視化工作室安裝資料夾{通用 7}IDE_私有程式\*集 ,以確保在調用之前載入它。

## <a name="add-commands-with-the-dte-object"></a>使用 DTE 物件加入指令
 您可以在標記和代碼中從起始頁訪問 DTE 物件。

 在標記中,可以使用[綁定標記擴展語法](/dotnet/framework/wpf/advanced/binding-markup-extension)來調<xref:EnvDTE.DTE>用 對象來訪問它。 可以使用此方法綁定到簡單屬性,例如返回集合的屬性,但不能綁定到方法或服務。 下面的範例顯示<xref:System.Windows.Controls.TextBlock>綁定到<xref:EnvDTE._DTE.Name%2A>屬性的控制項,以及枚舉<xref:System.Windows.Controls.ListBox>屬性返回<xref:EnvDTE.Window.Caption%2A>的集合<xref:EnvDTE._DTE.Windows%2A>的屬性的控制項。

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

 例如,請參閱[演練:在「開始頁」上儲存使用者設定](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)。

## <a name="see-also"></a>另請參閱

- [將使用者控制件添加到"開始頁"](../extensibility/adding-user-control-to-the-start-page.md)
