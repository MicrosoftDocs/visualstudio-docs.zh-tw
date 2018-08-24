---
title: 在 Visual Studio 中指定使用 Web 快取資料進行負載測試的虛擬使用者百分比
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 406c1c0c853563dc45b76e0bbcfefb3e21df0aff
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379367"
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>如何：指定使用 Web 快取資料之虛擬使用者的百分比

使用 [新增負載測試精靈] 建立負載測試之後，您就可以使用 [負載測試編輯器] 來變更情節屬性，以便符合您的測試需求和目標。 如需負載測試情節屬性及其描述的完整清單，請參閱[負載測試情節屬性](../test/load-test-scenario-properties.md)。

[新使用者的百分比] 屬性是在 [屬性] 視窗中設定的。 您可以在 [負載測試編輯器] 中編輯負載測試情節屬性。

[新使用者的百分比] 屬性會影響負載測試模擬網頁瀏覽器執行快取的方式。 根據預設，[新使用者的百分比] 屬性設定為 0%。 如果 [新使用者的百分比] 屬性的值設定為 100%，表示負載測試中的每一個 Web 效能測試回合都會被視為網站的初次瀏覽者，其瀏覽器快取中完全沒有之前瀏覽所留下的網站內容。 因此，Web 測試中的所有要求 (包括如影像之類的所有相依要求) 都會被下載。

> [!NOTE]
> 如果 Web 測試中同樣的可快取資源被要求一次以上時，這些要求不會被下載。

如果進行負載測試的網站有大量的回訪使用者，他們的本機快取可能已經有影像和其他可快取的內容，那麼將 [新使用者的百分比] 屬性設定為 100%，將會比真實使用狀況產生更多的下載要求。 在此情況下，您應該估計來自網站的初次瀏覽者的瀏覽百分比，然後據以設定 [新使用者的百分比] 屬性。

## <a name="to-specify-the-percentage-of-new-users-for-a-scenario"></a>指定情節的新使用者百分比

1. 開啟負載測試。

     [負載測試編輯器] 隨即出現。 負載測試樹狀隨即顯示。

2. 在負載測試樹狀目錄的 [情節] 資料夾中，選擇您要為其變更新使用者百分比值的情節節點。

3. 在 [檢視] 功能表上，選取 [屬性視窗]。

     情節的分類和屬性會顯示在 [屬性] 視窗中。

4. 為新使用者的百分比輸入一個數字，以設定 [新使用者的百分比] 屬性的值。

5. 屬性變更完成之後，選擇 [檔案] 功能表上的 [儲存]。 接著，您就可以使用新的 [新使用者的百分比] 值來執行負載測試。

## <a name="see-also"></a>另請參閱

- [編輯負載測試情節](../test/edit-load-test-scenarios.md)
- [逐步解說：建立和執行負載測試](../test/walkthrough-create-and-run-a-load-test.md)
- [測試控制器和測試代理程式](configure-test-agents-and-controllers-for-load-tests.md)
- [負載測試情節屬性](../test/load-test-scenario-properties.md)
- [編輯負載模式以模型化虛擬使用者活動](../test/edit-load-patterns-to-model-virtual-user-activities.md)