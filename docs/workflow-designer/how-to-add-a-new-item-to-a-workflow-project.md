---
title: 工作流程設計工具-如何：將新項目新增至工作流程專案
ms.date: 06/25/2018
ms.topic: conceptual
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6f0fb6c013e3df041e750344c09fb19f8c43b254
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649585"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>HOW TO：將新的項目新增至工作流程專案

您已建立工作流程專案後，您可以將工作流程活動、 設計師和其他熟悉的 Visual Studio 項目新增至您的專案。

下表列出您可以新增至工作流程專案的 Windows Workflow Foundation (WF) 項目：

| 名稱 | 描述 |
|-| - |
| 活動 | 要由其他活動組成的活動。 選取這個項目是將相同的 XAML 檔案加入專案，如有選取時，您會取得**活動程式庫**新專案範本。 如需此程序的相關詳細資訊，請參閱 <<c0> [ 建立工作流程專案](creating-a-workflow-project.md)。 |
| 活動設計工具 | 可自訂活動之設計階段經驗的設計工具。 選取這個項目是將相同的檔案加入專案，如有選取時，您會取得**活動設計工具程式庫**新專案範本。 |
| 程式碼活動 | 包含寫入至程式碼之執行邏輯的活動。 已為您產生包含 <xref:System.Activities.CodeActivity.Execute%2A> 方法之覆寫的原始程式碼檔。 |
| WCF 工作流程服務 | 使用工作流程活動建置的 [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] 服務。 選取這個項目是將相同的檔案加入專案，如有選取時，您會取得**WCF 工作流程服務應用程式**新專案範本。 如需有關此程序的詳細資訊，請參閱[How to:建立 WCF 工作流程服務應用程式](/visualstudio/workflow-designer/creating-a-workflow-project)。 |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>若要將新的項目加入至工作流程專案

1. 在 [專案] 功能表中，選取 [新增新項目]。

   [新增項目] 對話方塊隨即開啟。

1. 在左側窗格中，選取**工作流程**類別，然後再選取工作流程項目範本。

   > [!NOTE]
   > 如果您沒有看到**工作流程**類別，第一次安裝**Windows Workflow Foundation** Visual Studio 的元件。 如需詳細指示，請參閱 <<c0> [ 安裝的 Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)。

1. 輸入的名稱中的項目**名稱**底部的對話方塊 方塊中。

1. 選取 **新增**將項目加入至專案。

## <a name="see-also"></a>另請參閱

- [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)