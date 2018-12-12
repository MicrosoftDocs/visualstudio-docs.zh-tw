---
title: 用於負載測試的步驟負載模式逐步遞增時間
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
ms.assetid: 4a69e857-f93b-4907-9a01-fd1b66291205
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 81373e30498ad02f4007e096cfbc6a7cff953402
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895715"
---
# <a name="how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern"></a>如何：指定步驟負載模式的逐步遞增時間屬性

使用 [新增負載測試精靈] 建立負載測試之後，您就可以使用 [負載測試編輯器] 來變更情節屬性，以便符合您的測試需求和目標。 如需詳細資訊，請參閱[逐步解說：建立和執行負載測試](../test/walkthrough-create-and-run-a-load-test.md)。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> 如需負載測試情節屬性及其描述的完整清單，請參閱[負載測試情節屬性](../test/load-test-scenario-properties.md)。

[逐步遞增時間] 屬性是在 [屬性] 視窗中設定的。 您可以在 [負載測試編輯器] 中編輯負載測試情節屬性。

[逐步遞增時間] 屬性只能搭配步驟負載模式使用。 如需詳細資訊，請參閱[編輯負載模式以模型化虛擬使用者活動](../test/edit-load-patterns-to-model-virtual-user-activities.md)。

步驟負載模式用來在負載測試執行時增加一部或多部伺服器的負載，讓您能夠查看效能在使用者負載增加時如何變化。 例如，若要在使用者負載增加至 2,000 位使用者時查看伺服器的效能，您可能會使用具有下列屬性的步驟負載模式來執行 10 小時的負載測試：

-   初始使用者計數：100

-   最大使用者計數：2000

-   逐步執行持續期間 (秒)：1800

-   逐步遞增時間 (秒)：20

-   逐步執行使用者計數：100

這些設定會讓負載測試以使用者負載 100、200、300 (最多到 2,000 位使用者) 執行 30 分鐘 (1800 秒)。

> [!NOTE]
> [逐步遞增時間] 屬性是唯一無法在 [新增負載測試精靈] 中選擇的屬性。

[逐步遞增時間] 屬性允許步驟之間的增加作業 (例如，從 100 位增加至 200 位使用者) 逐漸進行，而非立即進行。 在此範例中，使用者負載會在 20 秒的期間內從 100 位增加至 200 位使用者 (每秒增加 5 位使用者)。

## <a name="to-edit-the-step-ramp-time-property-for-a-step-load-pattern"></a>編輯步驟負載模式的逐步遞增時間屬性

1.  開啟負載測試。

     [負載測試編輯器] 隨即出現。 負載測試樹狀隨即顯示。

2.  在負載測試樹狀目錄的 [情節] 資料夾中，開啟您要為其指定逐步遞增時間的情節節點。

3.  選取 [步驟負載模式] 節點。

    > [!NOTE]
    > 情節的負載模式必須是步驟負載模式。 如果不是，負載模式會顯示目前與情節關聯的負載模式類型。 如需詳細資訊，請參閱[編輯負載模式以模型化虛擬使用者活動](../test/edit-load-patterns-to-model-virtual-user-activities.md)。

4.  在 [檢視] 功能表上，選取 [屬性視窗]。

     情節的分類和屬性會顯示在 [屬性] 視窗中。

5.  輸入秒數來設定 [逐步遞增時間] 屬性值，表示每個步驟在這段時間會逐漸新增 [逐步執行使用者計數] 屬性指定的使用者人數。

6.  完成變更屬性之後，請選擇 [檔案] 功能表上的 [儲存]。 然後，您就可以使用新的 [逐步遞增時間] 值來執行負載測試。

## <a name="see-also"></a>另請參閱

- [編輯負載測試情節](../test/edit-load-test-scenarios.md)
- [測試控制器和測試代理程式](configure-test-agents-and-controllers-for-load-tests.md)
- [負載測試情節屬性](../test/load-test-scenario-properties.md)
- [編輯負載模式以模型化虛擬使用者活動](../test/edit-load-patterns-to-model-virtual-user-activities.md)