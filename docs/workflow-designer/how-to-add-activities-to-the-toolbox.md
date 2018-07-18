---
title: 工作流程設計工具-如何： 將活動新增至工具箱
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4edb752ca64afd899ac9b3e463b9d29e4b3b68a1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973766"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>HOW TO：將活動新增至工具箱

將活動加入至**工具箱**方案中數個不同的方式。 您可以從目前的專案內部加入活動、從不同的專案參考活動，或是從不同的組件參考活動。

## <a name="to-add-an-activity-from-within-your-current-project"></a>若要從目前的專案內部加入活動

1.  將新的自訂活動加入到目前的工作流程專案。 如需專案中加入新的自訂活動的詳細資訊，請參閱[How to： 將新的項目加入至工作流程專案](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md)。

2.  加入自訂邏輯至活動。

3.  建置專案。 如果建置成功，新的類別目錄中**工具箱**名為"\<*專案名稱*> 」 會顯示與該類別目錄中包含的自訂活動。

    > [!NOTE]
    > 如果重設工具箱，自訂活動會移除，即使重新建置方案也一樣。 若要重新填入自訂活動的 [工具箱]，已重設之後，重新啟動 Visual Studio 2010。

    > [!NOTE]
    > 在工具箱中，針對一個活動名稱只能顯示一個活動。 如果有兩個活動來自不同的組件但類別名稱相同，就只能顯示其中一個。

    > [!NOTE]
    > 應用程式定義域在編輯器執行個體間共用，如果使用靜態變數，則它們也會在編輯器執行個體間共用。 如果這不是想要的行為，應該使用服務來追蹤變數執行個體。 請參閱[使用 ModelItem 編輯內容](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context)如需使用設計工具內的服務。

## <a name="to-add-an-activity-from-within-a-different-project"></a>若要從不同的專案內部加入活動

1.  開啟一個方案，該方案應包含至少一個工作流程專案，以及一個自訂活動程式庫專案，或另一個定義自訂活動的工作流程專案。

2.  建置這兩個專案。 如果建置成功，新的類別目錄中**工具箱**名為"\<*專案名稱*> 」 會顯示與該類別目錄中包含的自訂活動。

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>若要從組件將活動加入至工具箱

1.  開啟一個工作流程方案。

2.  從**工具**功能表上，選取**選擇工具箱項目...**.

3.  在**選擇工具箱項目**對話方塊中，選取**System.Activities 元件**索引標籤，然後按一下 **瀏覽...** 想要新增到瀏覽至包含自訂活動組件。

4.  選取組件，然後按一下**確定**。 自訂活動元件會加到元件清單中，而且會自動選取。

    1.  按一下**確定**以關閉對話方塊。

5.  若要顯示工具箱 中，選取**工具箱**從**檢視**功能表。

6.  自訂活動會出現在**工具箱**之前已新增項目為焦點 類別底下。 例如，如果**一般**類別目錄中選取**工具箱**之前加入工具箱項目，該活動會出現在**一般**類別。

## <a name="see-also"></a>另請參閱

- [使用工作流程設計工具](../workflow-designer/using-the-workflow-designer.md)