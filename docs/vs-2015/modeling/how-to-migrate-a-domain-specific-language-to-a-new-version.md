---
title: 如何： 將定義域專屬語言移轉至新的版本 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1d97e0204122e6dfcae89da7b04a0a303a0bd9a4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "47588697"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>如何：將網域指定的語言移轉至新的版本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 將定義域專屬語言移轉至新的版本](https://docs.microsoft.com/visualstudio/modeling/how-to-migrate-a-domain-specific-language-to-a-new-version)。  
  
您可以移轉專案定義及使用特定領域語言[!INCLUDE[vs2010](../includes/vs2010-md.md)]版本中的[!INCLUDE[dsl](../includes/dsl-md.md)]所散發之[!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)]。  
  
 移轉工具提供做為一部分[!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)]。 此工具會將轉換[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]專案和方案使用，或定義 DSL 的工具。  
  
 您必須明確執行移轉工具： 它會不自動啟動時開啟的方案中[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。 可以找到詳細的指引 > 文件與工具，在此路徑：  
  
 **%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## <a name="before-you-migrate-your-dsl-projects"></a>將 DSL 專案的移轉之前  
 移轉工具會修改[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]專案檔 (**.csproj**) 和方案檔 (**.sln**)。  
  
#### <a name="to-prepare-projects-for-migration"></a>若要準備移轉專案。  
  
-   請確定 **.csproj**並 **.sln**可以寫入檔案。 如果它們是在原始檔控制，請確定已簽出。  
  
-   建立一份您想要移轉的資料夾。  
  
## <a name="migrating-a-collection-of-projects"></a>移轉專案的集合  
  
#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>若要移轉至 Visual Studio 2010 的 DSL 專案和方案  
  
1.  啟動 DSL 移轉工具。  
  
    -   您可以按兩下 Windows 檔案總管 （或檔案總管） 中的工具，或從命令提示字元啟動此工具。 此工具會在這個位置：  
  
         **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2.  選擇包含方案和您想要轉換的專案的資料夾。  
  
    -   在頂端的工具，方塊中輸入的路徑，或按一下**瀏覽**。  
  
     移轉工具顯示的樹狀結構的定義，或使用 Dsl 的專案。 樹狀結構包含使用每個專案**Microsoft.VisualStudio.Modeling.Sdk**或是**無法使用 TextTemplating**組件。  
  
3.  檢閱樹狀目錄中的專案，並取消選取不想要轉換的專案。  
  
    -   選取專案或解決方案，以查看變更，讓此工具的清單。  
  
        > [!NOTE]
        >  顯示資料夾名稱旁邊的核取方塊會有任何作用。 您必須展開要檢查專案和方案的資料夾。  
  
4.  轉換專案。  
  
    1.  按一下 **轉換**。  
  
         每個專案檔轉換時，一份之前_專案_**.csproj**會另存為_專案_**。 vs2008.csproj**  
  
         每一份_解決方案_**.sln**會另存為_解決方案_**。 vs2008.sln**  
  
    2.  調查會報告任何失敗的轉換。  
  
         在文字視窗中，會報告失敗。 此外，[樹狀] 檢視會顯示紅色旗標，無法轉換每個節點上。 您可以按一下節點以取得有關該失敗的詳細資訊。  
  
5.  **轉換所有範本**解決方案中包含已成功轉換專案。  
  
    1.  開啟的方案。  
  
    2.  按一下 [**轉換所有範本**方案總管] 中的標頭中的按鈕。  
  
        > [!NOTE]
        >  您可以進行此步驟中不必要的。 如需詳細資訊，請參閱 <<c0> [ 如何自動執行轉換的所有範本](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a)。  
  
6.  更新已轉換的專案中自訂程式碼。  
  
    -   嘗試建置專案，並調查任何失敗。  
  
    -   測試您的設計工具。  
  
## <a name="see-also"></a>另請參閱  
 [Visualization and Modeling SDK 的新功能](../misc/what-s-new-in-visualization-and-modeling-sdk.md)



