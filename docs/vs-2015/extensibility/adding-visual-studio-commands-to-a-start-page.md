---
title: 將 Visual Studio 命令新增至起始頁 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a2042ef9a96eed99636ea0a2f5f09d99cd35ea2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699158"
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>將 Visual Studio 命令新增至起始頁
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您建立自訂起始頁時，可以在其中新增 Visual Studio 命令。 本檔討論在起始頁上將 Visual Studio 命令系結至 XAML 物件的不同方式。  
  
 如需 XAML 中命令的詳細資訊，請參閱 [命令總覽](https://msdn.microsoft.com/library/bc208dfe-367d-426a-99de-52b7e7511e81)  
  
## <a name="adding-commands-from-the-command-well"></a>從命令部分新增命令  
 建立 [自訂起始頁](../extensibility/creating-a-custom-start-page.md) 時建立的起始頁已加入 <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> 和 <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> 命名空間，如下所示。  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 從元件 Microsoft.VisualStudio.Shell.Immutable.11.0.dll 新增 VisualStudio 的另一個命名空間。  (您可能需要在您的專案中新增此元件的參考。 )   
  
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
  
### <a name="calling-extensions-from-the-command-well"></a>從命令妥善呼叫擴充功能  
 您可以使用用來呼叫其他 Visual Studio 命令的相同語法，從已註冊的 Vspackage 呼叫命令。 例如，如果已安裝的 VSPackage 將 **首頁** 命令新增至 [ **View** ] 功能表，您可以藉由將設定為來呼叫該命令 `CommandParameter` `View.HomePage` 。  
  
> [!NOTE]
> 如果您呼叫與 VSPackage 相關聯的命令，則在叫用命令時必須載入此封裝。  
  
## <a name="adding-commands-from-assemblies"></a>從元件新增命令  
 若要從元件呼叫命令，或存取未與功能表命令相關聯之 VSPackage 中的程式碼，您必須建立元件的別名，然後呼叫別名。  
  
#### <a name="to-call-a-command-from-an-assembly"></a>從元件呼叫命令  
  
1. 在您的方案中，加入元件的參考。  
  
2. 在 StartPage 檔案的頂端，加入元件的命名空間指示詞，如下列範例所示。  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3. 藉由設定 `Command` XAML 物件的屬性來叫用命令，如下列範例所示。  
  
     Xaml  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
> 您必須複製元件，然後將它貼入。 \\*Visual Studio 安裝資料夾*\Common7\IDE\PrivateAssemblies\，以確定它會在呼叫之前先載入。  
  
## <a name="adding-commands-with-the-dte-object"></a>新增具有 DTE 物件的命令  
 您可以從起始頁（在標記和程式碼中）存取 DTE 物件。  
  
 在標記中，您可以使用系結 [標記延伸](https://msdn.microsoft.com/library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63) 語法呼叫物件來存取它 <xref:EnvDTE.DTE> 。 您可以使用這個方法系結至簡單的屬性，例如傳回集合的屬性，但是您無法系結至方法或服務。 下列範例顯示系結 <xref:System.Windows.Controls.TextBlock> 至屬性的控制項 <xref:EnvDTE._DTE.Name%2A> ，以及 <xref:System.Windows.Controls.ListBox> 列舉屬性所 <xref:EnvDTE.Window.Caption%2A> 傳回之集合屬性的控制項 <xref:EnvDTE._DTE.Windows%2A> 。  
  
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
 [將使用者控制項加入至起始頁](../extensibility/adding-user-control-to-the-start-page.md)
