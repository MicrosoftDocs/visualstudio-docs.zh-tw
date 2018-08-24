---
title: 在 Visual Studio 中儲存負載測試記錄
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 9ac88d8a-4777-462c-aa0e-244dadb2cfd1
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 3464ffc1db1a757ac20e3f77d0d901ec731a7cab
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2018
ms.locfileid: "39381930"
---
# <a name="how-to-specify-how-frequently-test-logs-are-saved-using-the-load-test-editor"></a>如何：使用負載測試編輯器指定儲存測試記錄的頻率

使用 [新增負載測試精靈] 建立負載測試之後，您就可以使用 [負載測試編輯器]，將負載測試屬性變更為符合您的測試需求和目標。 如需詳細資訊，請參閱[逐步解說：建立和執行負載測試](../test/walkthrough-create-and-run-a-load-test.md)。

> [!NOTE]
> 如需回合設定屬性及其描述的完整清單，請參閱[負載測試回合設定屬性](../test/load-test-run-settings-properties.md)。

您可以使用 [負載測試編輯器] 變更 [屬性] 視窗中的 [已完成之測試的儲存記錄檔頻率] 屬性，以指定在負載測試中儲存測試記錄的頻率。

## <a name="to-specify-the-frequency-for-saving-the-test-log-in-a-load-test"></a>若要指定負載測試中儲存測試記錄檔的頻率

1.  開啟負載測試。

     [負載測試編輯器] 隨即出現。 其中會顯示負載測試樹狀目錄。

2.  在負載測試樹狀目錄的 [回合設定] 資料夾中，選擇您要對其指定測試記錄儲存頻率的回合設定節點。

3.  在 [檢視] 功能表上，選取 [屬性視窗]。

     情節的分類和屬性會顯示在 [屬性] 視窗中。

4.  在 [已完成之測試的儲存記錄檔頻率] 屬性的文字方塊中輸入數字，表示寫入至測試記錄檔的頻率。 此數字表示次數，即測試每執行到輸入的次數，就會儲存至測試記錄檔。 例如，如果輸入值 10，即等於指定將第 10、20、30 次 (依此類推) 的測試寫入至測試記錄檔。

    > [!NOTE]
    > [已完成之測試的儲存記錄檔頻率] 屬性的值若使用 0，即等於指定不儲存任何測試記錄檔。

5.  屬性變更完成之後，選擇 [檔案] 功能表上的 [儲存]。

     您可以使用 [負載測試分析器] 的 [資料表] 檢視來檢視儲存在記錄檔中的資料。 如需詳細資訊，請參閱[在資料表檢視中分析負載測試結果和錯誤](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)。

## <a name="see-also"></a>另請參閱

- [編輯負載測試情節](../test/edit-load-test-scenarios.md)
- [逐步解說：建立和執行負載測試](../test/walkthrough-create-and-run-a-load-test.md)
- [如何：指定測試失敗是否會儲存至測試記錄](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)
- [如何：設定收集完整詳細資料以便啟用虛擬使用者活動圖](../test/how-to-configure-load-tests-to-collect-full-details.md)