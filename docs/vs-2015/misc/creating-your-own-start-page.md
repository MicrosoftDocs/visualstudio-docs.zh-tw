---
title: 建立您自己的起始頁 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Create start page
- custom start page
- customize start page
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
manager: jillfra
ms.openlocfilehash: ceb78d3310f37a58850199b11fb2b2fed86f6799
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299324"
---
# <a name="creating-your-own-start-page"></a>建立您自己的起始頁
您可以使用起始頁專案範本或建立空白起始頁，來建立自訂起始頁。  
  
 因為與 Visual Studio 應用程式模型的相依性，所以 XAML 設計工具可能無法以視覺方式完整精確地呈現自訂起始頁。  
  
## <a name="using-the-project-template"></a>使用專案範本  
 起始頁專案範本會建立本身為 Visual Studio 起始頁完整複本的起始頁專案。 接著，您可以編輯起始頁，以符合您的規格。  
  
#### <a name="to-create-a-custom-start-page-by-using-the-start-page-project-template"></a>使用起始頁專案範本來建立自訂起始頁  
  
1. 從 Visual Studio 組件庫，下載並安裝 [起始頁專案範本](https://go.microsoft.com/fwlink/?LinkId=186204) 。  
  
    > [!WARNING]
    > 目前，尚未升級 Visual Studio 2010 起始頁專案範本。 如需如何升級此範本的詳細資訊，請參閱[如何：升級 Visual Studio 自訂起始頁](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md)。  
  
2. 安裝範本之後，請使用它來建立新的起始頁專案。  
  
3. 在 [新增專案] 對話方塊左窗格的 [已安裝的範本]下，依序展開 [其他專案類型] 節點和 [擴充性]。  
  
4. 在中間窗格中，按一下 [自訂起始頁]，並命名您的專案，然後按一下 [確定]。  
  
     Visual Studio 會建立本身為 Visual Studio 起始頁完整複本的起始頁專案。  
  
5. 從 **方案總管**中，開啟 **StartPage.xaml**。  
  
6. 編輯 StartPage.xaml。  
  
     按 F5 鍵開啟已安裝自訂起始頁的 Visual Studio 實驗執行個體，以檢視您的工作。  
  
## <a name="creating-a-blank-start-page"></a>建立空白起始頁  
 建立空白起始頁的最簡單方式是使用起始頁專案範本，然後移除內容。  
  
#### <a name="to-create-a-blank-start-page-by-using-the-start-page-project-template"></a>使用起始頁專案範本來建立空白起始頁  
  
1. 使用起始頁專案範本來建立起始頁專案 (如先前程序中所述)。  
  
2. 開啟 StartPage.xaml。  
  
3. 移除所有頁面內容，僅保留外部 XML 項目和包含格線 <xref:System.Windows.Controls.Grid> 項目，因此您的 .xaml 檔案會與下列範例類似。  
  
   ```xaml
      <Grid xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
                xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
                xmlns:sp="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.StartPage"
                xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.10.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.10.0"
            mc:Ignorable="d" 
                d:DesignHeight="600" d:DesignWidth="800">
       <Grid>
           <!--Add content here.-->
       </Grid>
   </Grid>
   ```
      
4. 移除您不想要使用的任何支援檔案。  
  
    您應該保留 .vsix 和 .pkgdef 檔案，以進行部署。  
  
   或者，您可以建立具有 Visual Studio 可辨識之正確標記結構的 XAML 檔案，來建立空白起始頁。 接著，您可以加入標記和程式碼後置以取得所要的外觀和功能。 如需詳細資訊，請參閱[建立自訂起始頁](../extensibility/creating-a-custom-start-page.md)。  
  
## <a name="testing-and-applying-the-custom-start-page"></a>測試並套用自訂起始頁  
 除非您確認自訂起始頁未損毀，否則請不要設定主要執行個體來執行它。 測試過自訂起始頁之後，在 Visual Studio 的主要執行個體中重複這個程序的最後三個步驟，以將它套用至您的系統。  
  
#### <a name="to-test-a-custom-start-page"></a>測試自訂起始頁  
  
1. 請按 F5。  
  
    在已安裝但未選取新起始頁的情況下，開啟 Visual Studio 實驗執行個體。  
  
2. 在 Visual Studio 實驗執行個體中，按一下 [工具] 功能表上的 [選項]。  
  
3. 在 [選項] 對話方塊的 [環境]下，選取 [啟動]。 然後，在 [自訂起始頁] 清單上，選取您的 .xaml 檔案，然後按一下 [確定]。  
  
4. 在 [檢視] 功能表上，按一下 [起始頁]。  
  
    運作中起始頁隨即顯示。 您必須關閉實驗執行個體，並重新複製任何變更的檔案，然後重新開啟實驗執行個體以查看新的變更。  
  
   將 .vsix 檔案從 bin\debug 目錄上傳至[Visual Studio Marketplace](https://marketplace.visualstudio.com/)網站，或從另一個網站或內部網路共用，即可共用自訂起始頁。 如需詳細資訊，請參閱 [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md)。  
  
## <a name="see-also"></a>另請參閱  
 [自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)   
 [逐步解說︰將自訂的 XAML 加入至起始頁](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)