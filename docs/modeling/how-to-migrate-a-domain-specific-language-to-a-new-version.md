---
title: 如何：遷移 Domain-Specific 語言專案
description: 提供有關如何將特定領域語言專案遷移至較新版本的 Visual Studio 的資訊。
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: bbefb1cd5ae546c5454660b6782f9c76f35a63f4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922700"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>如何：將網域指定的語言移轉至新的版本
您可以 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] 從與一起散發的版本，將定義和使用特定領域語言的專案遷移至 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] 。

 提供遷移工具作為的一部分 [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] 。 此工具會轉換使用或定義 DSL 工具 Visual Studio 專案和解決方案。

 您必須明確地執行遷移工具：當您在 Visual Studio 中開啟方案時，它不會自動啟動。 您可以在下列路徑找到工具和詳細的指引檔：

 **% Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>遷移 DSL 專案之前
 遷移工具會修改 Visual Studio 的專案檔 (**.csproj**) 以及 (**.sln**) 的方案檔。

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

        轉換每 **個專案檔之前，會將** 一個 _專案_ 的複本 _儲存為_**vs2008 .csproj**

        每個方案的 **複本都會儲存為** __ **vs2008 .sln**

   2. 調查任何報告的失敗轉換。

        失敗會在文字視窗中報告。 此外，樹狀檢視會在每個無法轉換的節點上顯示紅色旗標。 您可以按一下節點以取得該失敗的詳細資訊。

5. 轉換包含已成功轉換專案之方案中的 **所有範本**。

   1. 開啟解決方案。

   2. 在方案總管的標頭中，按一下 [ **轉換所有範本** ] 按鈕。

       > [!NOTE]
       > 您可以不需要進行此步驟。 如需詳細資訊，請參閱 [如何自動轉換所有範本](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\))。

6. 更新已轉換之專案中的自訂程式碼。

   - 嘗試建立專案，並調查任何失敗。

   - 測試您的設計工具。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>另請參閱

- [相關部落格文章](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)