---
title: 負載測試的考慮時間
description: 瞭解如何編輯考慮時間，以模擬會讓人們在與網站互動之間等待的人類行為。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, think times
- load tests, adding delays
- load tests, changing think times
ms.assetid: 8e03bee5-ab7b-4b40-9497-9dbe91ccb90e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 0c6dc458fed9f03a4b9176817e243dca3a048b4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887844"
---
# <a name="edit-think-times-to-simulate-website-human-interaction-delays-in-load-tests-scenarios"></a>在負載測試情節中編輯考慮時間以模擬網站人類互動延遲

考慮時間可用來模擬造成人們在與網站互動時必須等待的人類行為。 考慮時間會發生在 Web 效能測試的各個要求之間，以及負載情節中各個測試反覆項目之間。 在負載測試中使用考慮時間，有助於建立更精確的負載模擬。 您可以決定負載測試中要使用或忽略考慮時間。 您會在 [負載測試編輯器] 中變更負載測試中是否要使用考慮時間。

「考慮特性」是套用到負載測試中之情節的設定。 此設定會決定在負載測試期間，是否要使用儲存在個別 Web 效能測試中的考慮時間。 如果想在某些 Web 效能測試中使用考慮時間，其他則不使用，則必須在不同的情節中使用不同的考慮時間設定。 如需情節的詳細資訊，請參閱[編輯負載測試情節](../test/edit-load-test-scenarios.md)。

一開始，您會在使用 [新增負載測試精靈] 建立負載測試時，設定負載測試中是否要使用考慮時間。 如需詳細資訊，請參閱[編輯負載測試情節](../test/edit-load-test-scenarios.md)。

[考慮特性] 選項的描述如下列清單：

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**關閉**

忽略考慮時間。 當您想產生最大負載以加重 Web 伺服器承受力，請使用這個設定。 若想與 Web 伺服器建立更符合現實的互動，請勿使用此選項。

**開啟**

考慮時間的使用正如它們在 Web 效能測試中所錄製的一樣。 以和錄製時情況完全相同的方式，模擬數個使用者執行 Web 效能測試。 由於負載測試會模擬多個使用者，若都使用相同的考慮時間，所建立之同步 (Synchronized) 虛擬使用者負載模式會比較不自然。

**常態分佈**

使用考慮時間，但在一般曲線上變化。 由於每個要求之間的考慮時間有些許不同，因此這項設定能讓虛擬使用者的模擬更貼近現實。

> [!NOTE]
> 如需負載測試情節屬性及其描述的完整清單，請參閱 [負載測試情節屬性](../test/load-test-scenario-properties.md)。

## <a name="change-the-think-profile"></a>變更考慮特性

### <a name="to-change-a-think-profile-in-a-load-test-scenario"></a>若要變更負載測試情節中的考慮特性

1. 從 Web 效能和負載測試專案中，開啟負載測試。

2. 在 [負載測試編輯器] 中，選擇您要變更 [考慮特性] 的情節節點。 [考慮特性] 隨即顯示在 [屬性] 視窗中。 按 **F4** 顯示 [屬性] 視窗。

3. 變更 [屬性] 視窗中的 [考慮特性] 屬性。

4. 完成變更屬性之後，請選擇 [檔案] 功能表上的 [儲存]。 然後，您就可以使用新的考慮特性執行負載測試。

## <a name="see-also"></a>另請參閱

- [編輯負載測試情節](../test/edit-load-test-scenarios.md)
