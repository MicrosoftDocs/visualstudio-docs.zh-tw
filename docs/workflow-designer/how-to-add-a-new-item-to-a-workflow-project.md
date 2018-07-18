---
title: 工作流程設計工具-如何： 將新的項目新增至工作流程專案
ms.date: 06/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c3f1202c87986eab6af899a3d4c3b7a5f62e5af6
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757675"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>如何： 將新的項目新增至工作流程專案

您已建立工作流程專案後，您可以將工作流程活動、 設計師和其他熟悉的 Visual Studio 項目新增至您的專案。

下表列出您可以新增至工作流程專案的 Windows Workflow Foundation (WF) 項目：

|名稱|描述|
|----------|-----------------|
|活動|要由其他活動組成的活動。 選取這個項目是將相同的 XAML 檔案加入專案，如有選取時，您會取得**活動程式庫**新專案範本。 如需此程序的相關詳細資訊，請參閱 <<c0> [ 如何： 建立活動程式庫](../workflow-designer/how-to-create-an-activity-library.md)。|
|活動設計工具|可自訂活動之設計階段經驗的設計工具。 選取這個項目是將相同的檔案加入專案，如有選取時，您會取得**活動設計工具程式庫**新專案範本。 如需此程序的相關詳細資訊，請參閱 <<c0> [ 如何： 建立活動設計工具程式庫](../workflow-designer/how-to-create-an-activity-designer-library.md)。|
|程式碼活動|包含寫入至程式碼之執行邏輯的活動。 已為您產生包含 <xref:System.Activities.CodeActivity.Execute%2A> 方法之覆寫的原始程式碼檔。|
|WCF 工作流程服務|使用工作流程活動建置的 [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] 服務。 選取這個項目是將相同的檔案加入專案，如有選取時，您會取得**WCF 工作流程服務應用程式**新專案範本。 如需有關此程序的詳細資訊，請參閱 <<c0> [ 如何： 建立 WCF 工作流程服務應用程式](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md)。|

## <a name="to-add-a-new-item-to-a-workflow-project"></a>若要將新的項目加入至工作流程專案

1. 在 **專案**功能表上，選取**加入新項目**。

   [新增項目] 對話方塊隨即開啟。

1. 在左側窗格中，選取**工作流程**類別，然後再選取工作流程項目範本。

   > [!NOTE]
   > 如果您沒有看到**工作流程**類別，第一次安裝**Windows Workflow Foundation**元件的 Visual Studio 2017。 如需詳細指示，請參閱 <<c0> [ 安裝的 Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)。

1. 輸入的名稱中的項目**名稱**底部的對話方塊 方塊中。

1. 選取 **新增**將項目加入至專案。

## <a name="see-also"></a>另請參閱

- [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)