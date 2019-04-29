---
title: 工作流程設計工具-CorrelatesOn 定義對話方塊
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7b7336a3f3b0c2725f4e52116d0add8bf13b90e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949812"
---
# <a name="correlateson-definition-dialog-box"></a>CorrelatesOn 定義對話方塊

**CorrelatesOn**  對話方塊中編輯時，會在工作流程設計工具<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>屬性<xref:System.ServiceModel.Activities.Receive>活動。 如需詳細資訊，請參閱 <<c0> [ 接收活動設計工具](../workflow-designer/receive-activity-designer.md)。

<xref:System.ServiceModel.Activities.Receive> 活動之間的相互關聯，會指定某個工作流程中不同服務作業彼此之間的關係。

下表描述的使用者介面 (UI) 項目**CorrelatesOn**  對話方塊。

|UI 項目|描述|
|-|-----------------|
|**CorrelatesWith**|用來路由訊息到適當工作流程執行個體的 <xref:System.ServiceModel.Activities.CorrelationHandle>。|
|**XPath 查詢**|配對的索引鍵/值，其中包含用來從傳入訊息擷取相互關聯資料的查詢。 這個值會對應到<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>屬性。 XPath 查詢會包含在 <xref:System.ServiceModel.MessageQuerySet> 物件中。|

## <a name="to-launch-the-correlateson-dialog-box"></a>若要啟動 CorrelatesOn 對話方塊

**接收**活動設計工具可以從拖曳**工具箱**，只要通常用來放置活動的工作流程設計工具介面中，卸除。 卸除活動設計工具會建立<xref:System.ServiceModel.Activities.Receive>預設值的活動<xref:System.Activities.Activity.DisplayName%2A>的接收。 若要開啟  **CorrelatesOn 定義**對話方塊中，選取**接收**活動設計工具，然後在屬性方格中，選取的集合文字旁邊的省略符號按鈕**CorrelatesOn**屬性。

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activities.Receive>
- [新增相互關聯初始設定式對話方塊](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [初始化相互關聯對話方塊](../workflow-designer/initialize-correlation-dialog-box.md)