---
title: 工作流程設計工具-如何：將活動新增至工具箱
description: 將活動加入至方案中的 [工具箱]，方法是從您目前的專案，或從不同的專案中參考它們。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2330392ace27a913870e7c7448976d1cae46958
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437940"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>HOW TO：將活動新增至工具箱

您可以透過數種不同的方式，將活動新增至方案中的 [ **工具箱** ]。 您可以從目前的專案內部加入活動、從不同的專案參考活動，或是從不同的組件參考活動。

## <a name="to-add-an-activity-from-within-your-current-project"></a>若要從目前的專案內部加入活動

1. 將新的自訂活動加入到目前的工作流程專案。 如需將新的自訂活動加入至專案的詳細資訊，請參閱 [如何：將新的專案加入至工作流程專案](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md)。

2. 加入自訂邏輯至活動。

3. 建置專案。 如果組建成功，[ **工具箱** ] 中會顯示名為 "" 的新類別， \<*project name*> 並顯示包含在該類別中的自訂活動。

    > [!NOTE]
    > 如果重設工具箱，自訂活動會移除，即使重新建置方案也一樣。 若要在重設自訂活動之後重新填入工具箱，請重新開機 Visual Studio。

    > [!NOTE]
    > 在工具箱中，針對一個活動名稱只能顯示一個活動。 如果有兩個活動來自不同的組件但類別名稱相同，就只能顯示其中一個。

    > [!NOTE]
    > 應用程式定義域在編輯器執行個體間共用，如果使用靜態變數，則它們也會在編輯器執行個體間共用。 如果這不是想要的行為，應該使用服務來追蹤變數執行個體。 如需在設計工具內使用服務的詳細資訊，請參閱 [使用 ModelItem 編輯內容](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) 。

## <a name="to-add-an-activity-from-within-a-different-project"></a>若要從不同的專案內部加入活動

1. 開啟一個方案，該方案應包含至少一個工作流程專案，以及一個自訂活動程式庫專案，或另一個定義自訂活動的工作流程專案。

2. 建置這兩個專案。 如果組建成功，[ **工具箱** ] 中會顯示名為 "" 的新類別， \<*project name*> 並顯示包含在該類別中的自訂活動。

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>若要從組件將活動加入至工具箱

1. 開啟一個工作流程方案。

2. 從 [ **工具** ] 功能表選取 **[選擇工具箱專案** ]。

3. 在 [ **選擇工具箱專案** ] 對話方塊中，選取 [system.string **元件** ] 索引標籤，然後按一下 **[流覽]** ，流覽至包含您要加入之自訂活動的元件。

4. 選取元件，然後按一下 **[確定]** 。 自訂活動元件會加到元件清單中，而且會自動選取。

    1. 按一下 **[確定]** 關閉對話方塊。

5. 若要顯示 [工具箱]，請從 [ **View** ] 功能表選取 [ **工具箱** ]。

6. 自訂活動會出現在 [工具箱] 中的 [ **工具箱** ] 下，加入專案之前的焦點類別。 例如，如果在新增 [工具箱] 專案之前，在 [ **工具箱** ] 中選取 [ **一般** ] 分類，則活動會出現在 [ **一般** ] 類別之下。

## <a name="see-also"></a>請參閱

- [使用工作流程設計工具](developing-applications-with-the-workflow-designer.md)
