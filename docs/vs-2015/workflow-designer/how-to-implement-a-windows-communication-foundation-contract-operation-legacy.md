---
title: 如何：執行 Windows Communication Foundation 合約作業（舊版） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f6f54e781dfae15b4b1c1159d73ac3495b35c21
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603870"
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>HOW TO：實作 Windows Communication Foundation 合約作業 (舊版)
本主題描述當使用以 [!INCLUDE[indigo1](../includes/indigo1-md.md)] 或 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 為目標的舊版 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 時，如何實作 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] 合約作業。

 從 [工具箱] 將 [ **ReceiveActivity** ] 活動拖曳至工作流程設計介面之後，您將建立新的 [!INCLUDE[indigo2](../includes/indigo2-md.md)] 合約，或匯入現有的合約並執行作業。 您可以透過 [[選擇作業] 對話方塊（舊版）](../workflow-designer/choose-operation-dialog-box-legacy.md)選取及/或建立您的合約及其作業。

### <a name="to-implement-a-wcf-contract-operation"></a>若要實作 WCF 合約作業

1. 按兩下設計工具中的 [ **ReceiveActivity** ] 活動，或按一下 [**屬性**] 窗格中 [ **ServiceOperationInfo** ] 屬性旁邊的省略號。

2. 執行下列任一步驟：

   - 按一下對話方塊右上角的 [**新增合約**]。 這將為您建立新的 [!INCLUDE[indigo2](../includes/indigo2-md.md)] 合約與作業。

      -或-

   - 按一下對話方塊右上角的 [匯**入**]。 [[流覽並選取 .Net 類型] 對話方塊（舊版）](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)隨即開啟。 搜尋含有您所要之合約的組件或專案。 選取合約，然後按一下 **[確定]** 。

     建立或匯入合約之後，您可以將新作業加入至該建立或匯入的合約。 若要加入新作業，請選取合約，然後按一下對話方塊右上角的 [**新增**作業]。 完成新增作業時，請繼續進行步驟 3。

3. 選取您想要與**ReceiveActivity**活動產生關聯的作業。 您可以變更作業的名稱、參數、屬性和權限設定，藉此操作作業的定義。

    若要變更名稱，請在 [作業**名稱**] 文字方塊中輸入新的名稱。

    按一下 [**參數**] 索引標籤，以存取作業的參數。 您可以變更參數的名稱、型別或方向，以及從作業新增或刪除參數。

    按一下 [**屬性**] 索引標籤，以存取作業的作業保護層級和支援的訊息交換功能。

    按一下 [**許可權**] 索引標籤，指定允許哪些群組執行此作業。

4. 按一下 **[確定]** ，[ **ReceiveActivity** ] 活動就會顯示其正在執行的作業名稱。

5. 將您要用於執行該作業的工作流程活動放在**ReceiveActivity**活動中。

## <a name="see-also"></a>請參閱
 [選擇作業對話方塊（舊版）](../workflow-designer/choose-operation-dialog-box-legacy.md) [如何：叫用 WCF 合約作業（舊版）](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)