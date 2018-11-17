---
title: 將 Visual Studio 命令加入至起始頁 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a5a0e205d04fb219d000dd87e97735cdfd26162
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748752"
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>將 Visual Studio 命令新增至起始頁
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您建立自訂起始頁時，您可以加入 Visual Studio 命令。 本文件討論繫結至在 [開始] 頁面的 XAML 物件的 Visual Studio 命令的不同方式。  
  
 如需 XAML 中命令的詳細資訊，請參閱[命令概觀](http://msdn.microsoft.com/library/bc208dfe-367d-426a-99de-52b7e7511e81)  
  
## <a name="adding-commands-from-the-command-well"></a>從命令中也新增命令  
 [開始] 頁面中建立[建立自訂起始頁](../extensibility/creating-a-custom-start-page.md)加入<xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>和<xref:Microsoft.VisualStudio.Shell?displayProperty=fullName>命名空間，如下所示。  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 從組件 Microsoft.VisualStudio.Shell.Immutable.11.0.dll Microsoft.VisualStudio.Shell 新增另一個命名空間。 （您可能需要在您的專案中加入此組件的參考）。  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 您可以使用`vscom:`頁面上控制設定的繫結至 XAML 的 Visual Studio 命令別名<xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A>屬性來控制`vscom:VSCommands.ExecuteCommand`。 然後您可以設定<xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>的執行，如下列範例所示的命令名稱的屬性。  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  `x:`別名，這指的是 XAML 結構描述，是需要的所有命令開頭。  
  
 您可以設定的值`Command`屬性，您可以從存取任何命令**命令**視窗。 如需可用命令的清單，請參閱 < [Visual Studio 命令別名](../ide/reference/visual-studio-command-aliases.md)。  
  
 如果要新增的命令需要一個額外的參數，您可以將它加入的值`CommandParameter`屬性。 使用空格，如下列範例所示的命令從不同的參數。  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>從命令中也呼叫延伸模組  
 您可以使用相同的語法是用來呼叫其他 Visual Studio 命令，從已註冊 Vspackage 呼叫命令。 比方說，如果已安裝的 VSPackage 新增**首頁**命令以**檢視**功能表中，您可以藉由設定呼叫該命令`CommandParameter`至`View.HomePage`。  
  
> [!NOTE]
>  如果您呼叫 VSPackage 相關聯的命令時，必須載入封裝時叫用命令。  
  
## <a name="adding-commands-from-assemblies"></a>將命令加入從組件  
 若要呼叫的命令，從組件，或存取程式碼所關聯的功能表命令的 VSPackage 中，您必須建立組件別名，然後呼叫 別名。  
  
#### <a name="to-call-a-command-from-an-assembly"></a>若要從組件呼叫命令  
  
1.  在您的方案中，加入組件的參考。  
  
2.  在 StartPage.xaml 檔案頂端，新增命名空間指示詞組件，如下列範例所示。  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  叫用命令，藉由設定`Command`XAML 物件，如下列範例所示的屬性。  
  
     Xaml  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  您必須將您的組件複製並貼在...\\ *Visual Studio 安裝資料夾*\Common7\IDE\PrivateAssemblies\ 以確定它載入會在呼叫之前。  
  
## <a name="adding-commands-with-the-dte-object"></a>將命令加入與 DTE 物件  
 您可以從 [開始] 頁面中標記和程式碼中存取 DTE 物件。  
  
 在標記中，您可以存取使用它[Binding 標記延伸模組](http://msdn.microsoft.com/library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63)語法來呼叫<xref:EnvDTE.DTE>物件。 您可以使用這種方法來繫結至簡單的屬性，例如傳回集合，但您無法繫結至方法或服務。 下列範例所示<xref:System.Windows.Controls.TextBlock>繫結至的控制項<xref:EnvDTE._DTE.Name%2A>屬性，以及<xref:System.Windows.Controls.ListBox>列舉的控制<xref:EnvDTE.Window.Caption%2A>屬性所傳回的集合<xref:EnvDTE._DTE.Windows%2A>屬性。  
  
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
  
 如需範例，請參閱[逐步解說： 在 [開始] 頁面上儲存使用者設定](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)。  
  
## <a name="see-also"></a>另請參閱  
 [將使用者控制項加入至起始頁](../extensibility/adding-user-control-to-the-start-page.md)

