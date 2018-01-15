---
title: "如何： 移轉至新版本的網域特定定義域語言 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e15efdb40b21b187dfc8bec543fc48c91f9efcf6
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>如何：將網域指定的語言移轉至新的版本
您可以移轉專案定義及使用以網域特定語言[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]版[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]可散發之[!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)]。  
  
 會提供移轉工具的一部分[!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]。 此工具將轉換[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案和方案，使用或定義 DSL 工具。  
  
 您必須明確地執行 「 移轉工具： 它無法自動啟動時開啟的方案中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 在這個路徑可以找到的工具和詳細的指引文件：  
  
 **%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## <a name="before-you-migrate-your-dsl-projects"></a>您之前移轉 DSL 專案  
 移轉工具修改[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案檔 (**.csproj**) 和方案檔 (**.sln**)。  
  
#### <a name="to-prepare-projects-for-migration"></a>若要準備移轉專案。  
  
-   請確定**.csproj**和**.sln**可以寫入檔案。 如果它們是在原始檔控制，請確定已簽出。  
  
-   建立一份您想要移轉的資料夾。  
  
## <a name="migrating-a-collection-of-projects"></a>移轉專案的集合  
  
#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>若要移轉至 Visual Studio 2010 的 DSL 專案和方案  
  
1.  啟動 DSL 移轉工具。  
  
    -   您可以按兩下 Windows 檔案總管 （或檔案總管） 中的工具，或從命令提示字元啟動工具。 此工具是在這個位置：  
  
         **%ProgramFiles%\Microsoft visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2.  選擇包含方案和您想要轉換的專案的資料夾。  
  
    -   在工具，最上方的方塊中輸入路徑，或按一下**瀏覽**。  
  
     移轉工具顯示樹狀結構的定義，或使用 Dsl 的專案。 樹狀目錄中包含的所有專案，使用**Microsoft.VisualStudio.Modeling.Sdk**或**TextTemplating**組件。  
  
3.  檢閱樹狀目錄中的專案，並取消核取您不想要轉換的專案。  
  
    -   選取專案或解決方案，以查看此工具將進行變更的清單。  
  
        > [!NOTE]
        >  顯示資料夾名稱旁的核取方塊會有任何作用。 您必須展開資料夾，以檢查專案和方案。  
  
4.  轉換專案。  
  
    1.  按一下**轉換**。  
  
         每個專案檔轉換時，一份之前*專案 * * *.csproj** 會另存為*專案 * * *.vs2008.csproj**  
  
         每個複本*方案 * * *.sln** 會另存為*方案 * * *.vs2008.sln**  
  
    2.  調查所報告的任何失敗的轉換。  
  
         失敗會回報文字視窗中。 此外，樹狀檢視會顯示紅色旗標，無法轉換每個節點上。 您可以按一下節點以取得該失敗的詳細資訊。  
  
5.  **轉換所有範本**方案中包含已成功轉換專案。  
  
    1.  開啟的方案。  
  
    2.  按一下**轉換所有範本**方案總管 中的標頭中的按鈕。  
  
        > [!NOTE]
        >  您可以進行此步驟中不必要的。 如需詳細資訊，請參閱[如何自動化轉換的所有範本](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a)。  
  
6.  更新已轉換的專案中自訂程式碼。  
  
    -   嘗試建置專案，並調查任何失敗。  
  
    -   測試您的設計工具。  
  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>請參閱  
 [相關部落格文章](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)

