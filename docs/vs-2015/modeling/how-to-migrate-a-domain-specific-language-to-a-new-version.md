---
title: 如何：將特定領域語言遷移至新版本 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 45f7b38f7dbb6ea470b2d9e186dc8e6bf4b33b1e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657334"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>如何：將網域指定的語言移轉至新的版本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以遷移定義和使用特定領域語言的專案，以便從隨 [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] 散發的 [!INCLUDE[dsl](../includes/dsl-md.md)] 版本中 [!INCLUDE[vs2010](../includes/vs2010-md.md)]。

 @No__t_0 中提供了遷移工具。 此工具會轉換使用或定義 DSL 工具的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案和解決方案。

 您必須明確地執行遷移工具：當您在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中開啟方案時，它不會自動啟動。 您可以在此路徑找到工具和詳細的指引檔：

 **% Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>遷移 DSL 專案之前
 遷移工具會修改 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案檔（ **.csproj**）和方案檔（ **.sln**）。

#### <a name="to-prepare-projects-for-migration"></a>準備專案以進行遷移。

- 請確定可以寫入 **.csproj**和 **.sln**檔案。 如果它們是在原始檔控制之下，請確定它們已簽出。

- 建立您想要遷移的資料夾複本。

## <a name="migrating-a-collection-of-projects"></a>遷移專案集合

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>將 DSL 專案和方案遷移至 Visual Studio 2010

1. 啟動 DSL 遷移工具。

   - 您可以按兩下 Windows Explorer （或檔案瀏覽器）中的工具，或從命令提示字元啟動工具。 此工具位於這個位置：

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. 選擇包含您想要轉換之方案和專案的資料夾。

   - 在工具頂端的方塊中輸入路徑，或按一下 **[流覽]** 。

     [遷移] 工具會顯示定義或使用 Dsl 的專案樹狀結構。 樹狀結構包含使用**VisualStudio**或**TextTemplating**元件的每個專案。

3. 檢查項目的樹狀結構，並取消選取您不想要轉換的專案。

   - 選取專案或方案，以查看工具將進行的變更清單。

       > [!NOTE]
       > 出現在 [資料夾名稱] 旁的核取方塊不會有任何作用。 您必須展開資料夾以檢查項目和方案。

4. 轉換專案。

   1. 按一下 [**轉換**]。

        轉換每個專案檔之前，會將_專案_ **.csproj**的複本_儲存為_**vs2008 .csproj**

        每個方案的**複本都會儲存為** **vs2008 .sln**

   2. 調查回報的任何失敗轉換。

        失敗會在文字視窗中回報。 此外，樹狀檢視會在每個無法轉換的節點上顯示紅色旗標。 您可以按一下節點以取得該失敗的詳細資訊。

5. 轉換方案中包含已成功轉換專案的**所有範本**。

   1. 開啟方案。

   2. 按一下方案總管標頭中的 [**轉換所有範本**] 按鈕。

       > [!NOTE]
       > 您可以不需要進行此步驟。 如需詳細資訊，請參閱[如何自動化轉換所有範本](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a)。

6. 在轉換的專案中更新您的自訂程式碼。

   - 嘗試建立專案，並調查是否有任何失敗。

   - 測試您的設計工具。

## <a name="see-also"></a>請參閱
 [Visualization and Modeling SDK 的新功能](../misc/what-s-new-in-visualization-and-modeling-sdk.md)
