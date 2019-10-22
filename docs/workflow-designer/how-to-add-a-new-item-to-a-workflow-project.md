---
title: 工作流程設計工具：將新專案加入至工作流程專案
ms.date: 06/25/2018
ms.topic: conceptual
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a87efc24ef148600c31dbb07d7517f9235306102
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650419"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>如何：將新專案加入至工作流程專案

建立工作流程專案之後，您可以將工作流程活動、設計工具和其他熟悉的 Visual Studio 專案加入至專案。

下表列出您可以新增至工作流程專案的 Windows Workflow Foundation （WF）專案：

| [屬性] | 描述 |
|-| - |
| 活動 | 要由其他活動組成的活動。 選取這個專案會將相同的 XAML 檔案加入至專案，就像您在選取新專案的**活動程式庫**範本時所取得的一樣。 如需有關此程式的詳細資訊，請參閱[建立工作流程專案](creating-a-workflow-project.md)。 |
| 活動設計工具 | 可自訂活動之設計階段經驗的設計工具。 選取這個專案會將相同的檔案加入至專案，就像您在選取新專案的 [**活動設計**工具程式庫] 範本時所取得的一樣。 |
| 程式碼活動 | 包含寫入至程式碼之執行邏輯的活動。 已為您產生包含 <xref:System.Activities.CodeActivity.Execute%2A> 方法之覆寫的原始程式碼檔。 |
| WCF 工作流程服務 | 使用工作流程活動建置的 [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] 服務。 選取這個專案會將相同的檔案加入至專案，就像您在選取新專案的**WCF 工作流程服務應用程式**範本時所取得的一樣。 如需此程式的詳細資訊，請參閱[如何：建立 WCF 工作流程服務應用程式](/visualstudio/workflow-designer/creating-a-workflow-project)。 |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>若要將新的項目加入至工作流程專案

1. 在 [專案] 功能表中，選取 [新增新項目]。

   [新增項目] 對話方塊隨即開啟。

1. 在左側窗格中，選取 [**工作流程**] 分類，然後選取 [工作流程專案] 範本。

   > [!NOTE]
   > 如果您沒有看到 [**工作流程**] 類別目錄，請先安裝 Visual Studio 的**Windows Workflow Foundation**元件。 如需詳細指示，請參閱[Install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)。

1. 在對話方塊底部的 [**名稱**] 方塊中，輸入專案的名稱。

1. 選取 [**新增**] 以將專案新增至專案。

## <a name="see-also"></a>請參閱

- [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)