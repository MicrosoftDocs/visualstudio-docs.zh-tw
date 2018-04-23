---
title: 建立自訂起始頁 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 71892262d98b175b111218068a02d03ad3d04caa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-custom-start-page"></a>建立自訂起始頁
您可以依照此文件中的步驟來建立自訂起始頁。  
  
## <a name="creating-a-blank-start-page"></a>建立空白起始頁  
 首先，請藉由建立具有 Visual Studio 會將標記結構的.xaml 檔案的空白起始頁。 然後，加入標記和程式碼後置產生的外觀和您想要的功能。  
  
#### <a name="to-create-a-blank-start-page"></a>若要建立空白起始頁  
  
1.  建立新的專案類型的**WPF 應用程式**(**Visual C# / Windows 桌面**。  
  
2.  加入 `Microsoft.VisualStudio.Shell.14.0` 的參考。  
  
3.  在 XML 編輯器中開啟 XAML 檔案，並變更最上層\<視窗 > 項目\<UserControl > 項目，但不會移除任何命名空間宣告。  
  
4.  移除`x:Class`從最上層元素宣告。 這使得相容於裝載 開始 頁面 Visual Studio 工具視窗的 XAML 內容。  
  
5.  將下列命名空間宣告加入至最上層\<UserControl > 項目。  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     這些命名空間可讓您存取 Visual Studio 命令、 控制項和 UI 設定。 如需詳細資訊，請參閱[加入 Visual Studio 命令起始頁](../extensibility/adding-visual-studio-commands-to-a-start-page.md)。  
  
     下列範例會顯示空白起始頁的.xaml 檔案中的標記。 任何自訂內容應該放在內部<xref:System.Windows.Controls.Grid>項目。  
  
    ```vb  
    <UserControl  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"  
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
        xmlns:local="clr-namespace:StartPageHost"  
        mc:Ignorable="d"  
         Height="350" Width="525">  
        <Grid>  
        <!--Add content here.-->  
        </Grid>  
    </UserControl>  
    ```  
  
6.  將控制項加入空\<UserControl > 填寫自訂起始頁的項目。 如需如何新增功能的 Visual Studio 的特定資訊，請參閱[加入 Visual Studio 命令起始頁](../extensibility/adding-visual-studio-commands-to-a-start-page.md)。  
  
## <a name="testing-and-applying-the-custom-start-page"></a>測試並套用自訂起始頁  
 未設定執行自訂起始頁，直到您確認它並未損毀 Visual Studio 的 Visual Studio 的主要執行個體。 相反地，在測試實驗執行個體。  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>若要測試手動建立的自訂起始頁  
  
1.  將您的 XAML 檔案，並支援文字檔或標記檔案，以複製**%USERPROFILE%\My Documents\Visual Studio 2015 \startpages\\** 資料夾。  
  
2.  如果您的起始頁參考任何控制項或在 Visual Studio 不會安裝的組件中的類型，將組件複製和貼在 * Visual Studio 安裝資料夾 ***\Common7\IDE\PrivateAssemblies\\** .  
  
3.  在 Visual Studio 命令提示字元中，輸入**devenv /rootsuffix Exp**若要開啟的 Visual Studio 的實驗執行個體。  
  
4.  在實驗執行個體中，移至**工具 / 選項 / 環境 / 啟動**頁面，然後選取您的 XAML 檔案從**自訂起始頁**下拉式清單。  
  
5.  在 [檢視]  功能表上，按一下 [起始頁] 。  
  
     應該會顯示自訂起始頁。 如果您想要變更的任何檔案，您必須關閉實驗執行個體、 進行變更、 複製並貼變更的檔案，然後再重新開啟實驗執行個體，以檢視變更。  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>若要套用自訂起始頁在 Visual Studio 的主要執行個體  
  
-   您已經測試您的起始頁，並找到它的穩定性之後，請使用**自訂起始頁**選項**選項**對話方塊來選取做為 Visual Studio 的主要執行個體中的 [開始] 頁面  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 在 [開始] 頁面中加入自訂的 XAML](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [將使用者控制項加入至 [開始] 頁面](../extensibility/adding-user-control-to-the-start-page.md)   
 [將 Visual Studio 命令加入至 [開始] 頁面](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [逐步解說： 在 [開始] 頁面上儲存使用者設定](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [部署自訂起始頁](../extensibility/deploying-custom-start-pages.md)