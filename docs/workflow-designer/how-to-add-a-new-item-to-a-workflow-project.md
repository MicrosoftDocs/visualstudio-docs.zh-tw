---
title: 工作流程設計工具：將新的專案加入至工作流程專案
description: 瞭解如何在建立工作流程專案之後，將工作流程活動、設計工具和其他熟悉的 Visual Studio 專案加入至您的專案。
ms.custom: SEO-VS-2020
ms.date: 06/25/2018
ms.topic: how-to
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e0cc4b24462583a5f704f47c16e6e8d30456512b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938456"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>如何：將新的專案加入至工作流程專案

建立工作流程專案之後，您可以將工作流程活動、設計工具和其他熟悉的 Visual Studio 專案加入至您的專案。

下表列出您可以新增至工作流程專案的 Windows Workflow Foundation (WF) 專案：

| 名稱 | 描述 |
|-| - |
| 活動 | 要由其他活動組成的活動。 選取這個專案會將相同的 XAML 檔案加入至專案，就像您在選取新專案的 **活動程式庫** 範本時所取得的一樣。 如需有關此程式的詳細資訊，請參閱 [建立工作流程專案](creating-a-workflow-project.md)。 |
| 活動設計工具 | 可自訂活動之設計階段經驗的設計工具。 選取這個專案會將相同的檔案加入至專案，就像您在選取新專案的 [ **活動設計** 工具程式庫] 範本時所取得的一樣。 |
| 程式碼活動 | 包含寫入至程式碼之執行邏輯的活動。 已為您產生包含 <xref:System.Activities.CodeActivity.Execute%2A> 方法之覆寫的原始程式碼檔。 |
| WCF 工作流程服務 | 使用工作流程活動建置的 [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] 服務。 選取這個專案會將相同的檔案加入至專案，就像您在選取新專案的 **WCF Workflow Service 應用程式** 範本時所取得的一樣。 如需此程式的詳細資訊，請參閱 [如何：建立 WCF 工作流程服務應用程式](creating-a-workflow-project.md)。 |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>若要將新的項目加入至工作流程專案

1. 在 [專案] 功能表上，選取 [新增項目]。

   [ **加入新專案** ] 對話方塊隨即開啟。

1. 在左窗格中，選取 [ **工作流程** ] 類別，然後選取工作流程專案範本。

   > [!NOTE]
   > 如果您沒有看到 **工作流程** 類別目錄，請先安裝 Visual Studio 的 **Windows Workflow Foundation** 元件。 如需詳細指示，請參閱 [安裝 Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)。

1. 在對話方塊底部的 [ **名稱** ] 方塊中輸入專案的名稱。

1. 選取 [ **新增** ]，將專案加入至專案。

## <a name="see-also"></a>另請參閱

- [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)
