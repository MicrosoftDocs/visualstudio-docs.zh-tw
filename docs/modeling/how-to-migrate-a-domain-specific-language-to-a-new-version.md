---
title: 如何：將網域指定的語言移轉至新的版本
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8bdaea1267d0bf69078aec5739291e72db8dfda
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532607"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>如何：將網域指定的語言移轉至新的版本
您可以 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] 從與一起散發的版本中，將定義和使用特定領域語言的專案遷移至 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] 。

 會提供遷移工具做為的一部分 [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] 。 此工具會轉換使用或定義 DSL 工具的 Visual Studio 專案和解決方案。

 您必須明確地執行遷移工具：當您在 Visual Studio 中開啟方案時，它不會自動啟動。 您可以在此路徑找到工具和詳細的指引檔：

 **% Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>遷移 DSL 專案之前
 遷移工具會修改 Visual Studio 專案檔（**.csproj**）和方案檔（**.sln**）。

#### <a name="to-prepare-projects-for-migration"></a>準備專案以進行遷移。

- 請確定可以寫入 **.csproj**和 **.sln**檔案。 如果它們是在原始檔控制之下，請確定它們已簽出。

- 建立您想要遷移的資料夾複本。

## <a name="migrating-a-collection-of-projects"></a>遷移專案集合

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>將 DSL 專案和方案遷移至 Visual Studio 2010

1. 啟動 DSL 遷移工具。

   - 您可以按兩下 Windows Explorer （或檔案瀏覽器）中的工具，或從命令提示字元啟動工具。 此工具位於這個位置：

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. 選擇包含您想要轉換之方案和專案的資料夾。

   - 在工具頂端的方塊中輸入路徑，或按一下 **[流覽]**。

     [遷移] 工具會顯示定義或使用 Dsl 的專案樹狀結構。 樹狀結構包含使用**VisualStudio**或**TextTemplating**元件的每個專案。

3. 檢查項目的樹狀結構，並取消選取您不想要轉換的專案。

   - 選取專案或方案，以查看工具將進行的變更清單。

       > [!NOTE]
       > 出現在 [資料夾名稱] 旁的核取方塊不會有任何作用。 您必須展開資料夾以檢查項目和方案。

4. 轉換專案。

   1. 按一下 [**轉換**]。

        轉換每個專案檔之前，會將_專案_**.csproj**的複本_儲存為_**vs2008 .csproj**

        每個方案的_solution_**複本都會儲存為** _ _ **vs2008 .sln**

   2. 調查回報的任何失敗轉換。

        失敗會在文字視窗中回報。 此外，樹狀檢視會在每個無法轉換的節點上顯示紅色旗標。 您可以按一下節點以取得該失敗的詳細資訊。

5. 轉換方案中包含已成功轉換專案的**所有範本**。

   1. 開啟解決方案。

   2. 按一下方案總管標頭中的 [**轉換所有範本**] 按鈕。

       > [!NOTE]
       > 您可以不需要進行此步驟。 如需詳細資訊，請參閱[如何自動化轉換所有範本](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\))。

6. 在轉換的專案中更新您的自訂程式碼。

   - 嘗試建立專案，並調查是否有任何失敗。

   - 測試您的設計工具。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>另請參閱

- [相關部落格文章](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)