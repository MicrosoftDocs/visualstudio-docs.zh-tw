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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657334"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>如何：將網域指定的語言移轉至新的版本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 從與一起散發的版本，將定義和使用特定領域語言的專案遷移至 [!INCLUDE[dsl](../includes/dsl-md.md)] [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] 。

 提供遷移工具作為的一部分 [!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)] 。 此工具 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會轉換使用或定義 DSL 工具的專案和方案。

 您必須明確地執行遷移工具：當您在中開啟方案時，它不會自動啟動 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 您可以在下列路徑找到工具和詳細的指引檔：

 **% Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>遷移 DSL 專案之前
 遷移工具會修改 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案檔 (**.Csproj**) 和方案檔， (**.sln**) 。

#### <a name="to-prepare-projects-for-migration"></a>準備專案以進行遷移。

- 請確定可以撰寫 **.csproj** 和 **.sln** 檔案。 如果它們是在原始檔控制之下，請確定已簽出它們。

- 製作您想要遷移的資料夾複本。

## <a name="migrating-a-collection-of-projects"></a>遷移專案集合

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>將 DSL 專案和解決方案遷移至 Visual Studio 2010

1. 啟動 DSL 遷移工具。

   - 您可以按兩下 Windows 檔案總管 (或檔案總管) 中的工具，或是從命令提示字元啟動工具。 此工具位於下列位置：

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. 選擇包含您要轉換之方案和專案的資料夾。

   - 在工具頂端的方塊中輸入路徑，或按一下 **[流覽]**。

     「遷移工具」會顯示定義或使用 Dsl 的專案樹狀結構。 樹狀結構包含使用 **VisualStudio** 或 **TextTemplating** 元件的每個專案。

3. 檢查項目的樹狀結構，並取消選取您不想要轉換的專案。

   - 選取專案或方案，以查看工具將會進行的變更清單。

       > [!NOTE]
       > 在 [資料夾名稱] 旁出現的核取方塊不會有任何作用。 您必須展開資料夾以檢查項目和方案。

4. 轉換專案。

   1. 按一下 [ **轉換**]。

        轉換每**個專案檔之前，會將**一個_專案_的複本_儲存為_**vs2008 .csproj**

        每個方案的_solution_**複本都會儲存為** _ _ **vs2008 .sln**

   2. 調查任何報告的失敗轉換。

        失敗會在文字視窗中報告。 此外，樹狀檢視會在每個無法轉換的節點上顯示紅色旗標。 您可以按一下節點以取得該失敗的詳細資訊。

5. 轉換包含已成功轉換專案之方案中的**所有範本**。

   1. 開啟解決方案。

   2. 在方案總管的標頭中，按一下 [ **轉換所有範本** ] 按鈕。

       > [!NOTE]
       > 您可以不需要進行此步驟。 如需詳細資訊，請參閱 [如何自動轉換所有範本](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a)。

6. 更新已轉換之專案中的自訂程式碼。

   - 嘗試建立專案，並調查任何失敗。

   - 測試您的設計工具。

## <a name="see-also"></a>另請參閱
 [Visualization and Modeling SDK 的新功能](../misc/what-s-new-in-visualization-and-modeling-sdk.md)
