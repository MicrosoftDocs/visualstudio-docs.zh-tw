---
title: 工作流程設計工具-CorrelatesOn 定義] 對話方塊
description: 瞭解如何使用工作流程設計工具中的 [CorrelatesOn] 對話方塊來編輯 Receive 活動的 CorrelatesOn 屬性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b4f371da2570d5573ce84c7e29393889202ae940
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955537"
---
# <a name="correlateson-definition-dialog-box"></a>CorrelatesOn 定義對話方塊

工作流程設計工具中使用 [ **CorrelatesOn** ] 對話方塊來編輯活動的 <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> 屬性 <xref:System.ServiceModel.Activities.Receive> 。 如需詳細資訊，請參閱 [Receive 活動設計](../workflow-designer/receive-activity-designer.md)工具。

<xref:System.ServiceModel.Activities.Receive> 活動之間的相互關聯，會指定某個工作流程中不同服務作業彼此之間的關係。

下表說明 [ **CorrelatesOn** ] 對話方塊的使用者介面 (UI) 元素。

|UI 元素|描述|
|-|-----------------|
|**CorrelatesWith**|用來路由訊息到適當工作流程執行個體的 <xref:System.ServiceModel.Activities.CorrelationHandle>。|
|**XPath 查詢**|配對的索引鍵/值，其中包含用來從傳入訊息擷取相互關聯資料的查詢。 這個值會對應至 <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> 屬性。 XPath 查詢會包含在 <xref:System.ServiceModel.MessageQuerySet> 物件中。|

## <a name="to-launch-the-correlateson-dialog-box"></a>若要啟動 CorrelatesOn 對話方塊

[ **Receive** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到工作流程設計工具介面上，通常放置活動的地方。 卸載活動設計工具會建立 <xref:System.ServiceModel.Activities.Receive> 活動，預設值是 <xref:System.Activities.Activity.DisplayName%2A> Receive。 若要開啟 [ **CorrelatesOn 定義** ] 對話方塊，請選取 [ **Receive** ] 活動設計工具，然後在屬性方格中，選取 [ **CorrelatesOn** ] 屬性的集合文字旁的省略號按鈕。

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activities.Receive>
- [加入相互關聯初始設定式對話方塊](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [初始化相互關聯對話方塊](../workflow-designer/initialize-correlation-dialog-box.md)