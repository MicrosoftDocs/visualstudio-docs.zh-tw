---
title: "Visual Studio 命令加入起始頁 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 973e0cfbceb6cbf67c5bc11cdde370607334809a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>將 Visual Studio 命令加入至 [開始] 頁面
當您建立自訂起始頁時，您可以將 Visual Studio 命令加入它。 本文將討論不同的方式將 Visual Studio 命令繫結至 XAML 開始頁面上的物件。  
  
 如需 XAML 中命令的詳細資訊，請參閱[指揮概觀](/dotnet/framework/wpf/advanced/commanding-overview)  
  
## <a name="adding-commands-from-the-command-well"></a>從命令中也加入命令  
 [開始] 頁面中建立[建立自訂起始頁](../extensibility/creating-a-custom-start-page.md)加入<xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>和<xref:Microsoft.VisualStudio.Shell?displayProperty=fullName>命名空間，如下所示。  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 從組件 Microsoft.VisualStudio.Shell.Immutable.11.0.dll Microsoft.VisualStudio.Shell 加入另一個命名空間。 （您可能需要將這個組件的參考加入您專案中）。  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 您可以使用`vscom:`繫結至 XAML 的 Visual Studio 命令別名控制頁面上，藉由設定<xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A>控制項的屬性`vscom:VSCommands.ExecuteCommand`。 然後您可以設定<xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>屬性設為要執行，如下列範例所示的命令名稱。  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  `x:`別名，XAML 結構描述是指，無須在所有命令的開頭。  
  
 您可以設定的值`Command`屬性可以存取從任何命令**命令**視窗。 如需可用命令的清單，請參閱[Visual Studio 命令別名](../ide/reference/visual-studio-command-aliases.md)。  
  
 如果命令來新增需要額外的參數，您可以將它加入的值`CommandParameter`屬性。 個別的使用空間，如下列範例所示的命令參數。  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>從命令中也呼叫擴充功能  
 您可以使用相同的語法，用來呼叫其他 Visual Studio 命令，從已註冊 Vspackage 呼叫命令。 比方說，如果已安裝的 VSPackage 新增**首頁**命令**檢視**功能表上，您可以藉由設定呼叫該命令`CommandParameter`至`View.HomePage`。  
  
> [!NOTE]
>  如果您呼叫 VSPackage 相關聯的命令時，必須載入封裝時叫用命令。  
  
## <a name="adding-commands-from-assemblies"></a>將命令加入從組件  
 若要從組件，或未與功能表命令相關聯的 VSPackage 中存取程式碼呼叫的命令，您必須建立組件別名，然後呼叫 別名。  
  
#### <a name="to-call-a-command-from-an-assembly"></a>若要從組件呼叫命令  
  
1.  在您的方案，加入組件的參考。  
  
2.  StartPage.xaml 檔案頂端加入命名空間指示詞的組件，如下列範例所示。  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  藉由設定叫用命令`Command`XAML 物件，如下列範例所示的屬性。  
  
     Xaml  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  您必須將您的組件複製並貼在...\\ *Visual Studio 安裝資料夾*\Common7\IDE\PrivateAssemblies\ 以確定它載入會在呼叫之前。  
  
## <a name="adding-commands-with-the-dte-object"></a>將命令加入與 DTE 物件  
 您可以從 [開始] 頁面上，在標記和程式碼中存取 DTE 物件。  
  
 在標記中，您可以存取該使用[繫結標記延伸](/dotnet/framework/wpf/advanced/binding-markup-extension)語法來呼叫<xref:EnvDTE.DTE>物件。 您可以使用此方法來繫結至簡單的屬性，例如所傳回的集合，但您無法繫結至方法或服務。 下列範例所示<xref:System.Windows.Controls.TextBlock>繫結至控制項<xref:EnvDTE._DTE.Name%2A>屬性，以及<xref:System.Windows.Controls.ListBox>列舉的控制項<xref:EnvDTE.Window.Caption%2A>屬性所傳回的集合<xref:EnvDTE._DTE.Windows%2A>屬性。  
  
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
  
 如需範例，請參閱[逐步解說： 起始頁上儲存使用者設定](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)。  
  
## <a name="see-also"></a>另請參閱  
 [將使用者控制項加入至起始頁](../extensibility/adding-user-control-to-the-start-page.md)