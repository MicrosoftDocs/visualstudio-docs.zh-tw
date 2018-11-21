---
title: 建立 WPF 工具箱控制項 |Microsoft Docs
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
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ad3edfa84ee64425a7a9fbc6b0dfc5098396907
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786024"
---
# <a name="creating-a-wpf-toolbox-control"></a>建立 WPF 工具箱控制項
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

(Windows Presentation Framework) 的 WPF 工具箱控制項 範本可讓您建立會自動新增至 WPF 控制項**工具箱**安裝擴充功能時。 本主題說明如何使用範本來建立**工具箱**可以散發給其他使用者的控制項。  
  
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-wpf-toolbox-control"></a>建立 WPF 工具箱控制項  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>建立 WPF 工具箱控制項擴充功能  
  
1.  建立 VSIX 專案，名為`MyToolboxControl`。 您可以找到在 VSIX 專案範本**新的專案**下方的對話方塊**Visual C# / 擴充性**。  
  
2.  當專案開啟時，新增**WPF 工具箱控制項**名為的項目範本`MyToolboxControl`。 在 **方案總管**，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**。 在 **加入新項目**對話方塊中，移至**Visual C# / 擴充性**，然後選取**WPF 工具箱控制項**。 在 **名稱**視窗的底部欄位中，將命令的檔案名稱變更為`MyToolboxControl.cs`。  
  
     方案現在包含使用者控制項、 `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> ，將控制項加入至**工具箱**，和**Microsoft.VisualStudio.ToolboxControl**資產的 VSIX 資訊清單中的項目 部署。  
  
#### <a name="to-create-the-control-ui"></a>若要建立 UI 控制項  
  
1.  在設計工具中開啟 MyToolboxControl.xaml。  
  
     設計工具會顯示包含了 <xref:System.Windows.Controls.Button> 控制項的 <xref:System.Windows.Controls.Grid> 控制項。  
  
2.  排列格線版面配置。 當您選取<xref:System.Windows.Controls.Grid>控制，藍色的控制列會出現在方格上方和左邊緣。 您可以按一下橫條圖，來將資料列和資料行新增至方格。  
  
3.  加入子控制項至格線。 您可以藉由將它從放置子控制項**工具箱**一節的方格中，或藉由設定其`Grid.Row`和`Grid.Column`XAML 中的屬性。 下列範例會將兩個標籤上方格的第二個資料列上的按鈕上方的資料列。  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>重新命名控制項  
 根據預設，您的控制項將會出現在**工具箱**作為**MyToolboxControl**群組中名為**MyToolboxControl.MyToolboxControl**。 您可以變更這些 MyToolboxControl.xaml.cs 檔案中的名稱。  
  
1.  在程式碼檢視中開啟 MyToolboxControl.xaml.cs。  
  
2.  尋找 MyToolboxControl 類別，並將它重新命名為 TestControl。 (若要這樣做最快的方法是重新命名類別，然後選取**重新命名**從內容功能表，並完成步驟。 (如需詳細資訊**重新命名**命令，請參閱[重新命名重構 (C#)](../csharp-ide/rename-refactoring-csharp.md)。)  
  
3.  移至`ProvideToolboxControl`屬性並將變更的第一個參數的值**測試**。 這是將包含控制項中的群組名稱**工具箱**。  
  
     產生的程式碼看起來應該像這樣：  
  
    ```csharp  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## <a name="building-testing-and-deployment"></a>建置、測試和部署  
 當您偵錯專案時，您應該會發現在安裝控制項**工具箱**的 Visual Studio 的實驗執行個體。  
  
#### <a name="to-build-and-test-the-control"></a>建置和測試控制項  
  
1.  重建專案並開始偵錯。  
  
2.  在 Visual Studio 的新執行個體中建立 WPF 應用程式專案。 請確定會開啟 XAML 設計工具。  
  
3.  在 [工具箱]  中尋找控制項，並將它拖曳至設計介面。  
  
4.  開始偵錯 WPF 應用程式。  
  
5.  請確認您的控制項，會出現。  
  
#### <a name="to-deploy-the-control"></a>部署內容  
  
1.  建置測試的專案之後，您可以在專案的 \bin\debug\ 資料夾中找到.vsix 檔案。  
  
2.  您可以在本機電腦上安裝它按兩下.vsix 檔，並遵循安裝程序。 若要解除安裝控制項，請前往**工具 / 擴充功能和更新**並尋找的控制項擴充功能，然後按一下**解除安裝**。  
  
3.  將 .vsix 檔案上傳到網路或網站。  
  
     如果您上傳檔案[Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkID=123847)網站，其他使用者可以使用**工具 / 擴充功能和更新**在 Visual Studio 中找不到線上的控制項，並將它安裝。

