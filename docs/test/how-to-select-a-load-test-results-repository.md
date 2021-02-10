---
title: 如何：選取負載測試結果儲存機制
description: 瞭解如何識別本機或遠端 SQL server 來儲存您的測試結果。 伺服器必須有負載測試結果存放區。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.dialog.connectstringmissing
- vs.test.load.dialog.databaseconnectstring
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
- SQL, Load Test Results Store
ms.assetid: fa0c4dd9-612f-4a57-b8eb-458f129d9cda
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 832b4f9257c328989b2d4d0f7db3bb5f49ec4f08
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971852"
---
# <a name="how-to-select-a-load-test-results-repository"></a>如何：選取負載測試結果存放庫

您不必侷限於本機結果存放區。 負載測試通常會在遠端代理程式電腦集合上執行。 代理程式加上控制器能夠產生比任何單一電腦更接近的模擬負載。 如需詳細資訊，請參閱 [測試控制器和測試代理](configure-test-agents-and-controllers-for-load-tests.md)程式。

從代理程式或本機電腦產生的測試結果，可以儲存在任何已經存有您所建立之負載測試結果存放區的 SQL Server 上。 在任何情況下，您都必須使用 [管理測試控制器] 視窗來識別要儲存負載測試結果的位置。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="identify-a-results-store-for-load-test-data"></a>識別負載測試資料的結果存放區

1. 在 [方案總管] 中開啟您的負載測試檔案。

2. 從 [負載測試] 工具列選擇 [管理測試控制器]。 [管理測試控制器] 對話方塊隨即顯示。 如果您正在遠端使用代理程式，則必須選取控制器。

     ![負載測試結果存放區連接屬性](../test/media/loadtestconnectionproperties.png) 負載測試結果存放區連接屬性

3. 在 [ **負載測試結果存放區**] 中，按一下 [ (]， **)** 顯示 [ **連接屬性** ] 對話方塊。

4. 在 [伺服器名稱] 中，鍵入先前執行 `LoadTest` 指令碼所在之伺服器的名稱。

    > [!TIP]
    > 如果您在本機電腦上使用 SQL Express 做為負載測試存放區，請輸入 \<computername> \sqlexpress (例如 **MyComputer\sqlexpress**) 。

5. 在 [登入伺服器] 底下，您可以選擇 [使用 Windows 驗證]。 您可以指定使用者名稱和密碼，但若指定，則必須選取 [儲存我的密碼] 選項。

6. 在 [連接至資料庫] 底下，選擇 [選取或輸入資料庫名稱]。 請從下拉式清單方塊中選取 [LoadTest]。

7. 選擇 [確定]。 您可以選擇 [測試連接] 測試連接。

8. 選擇 [管理測試控制器] 對話方塊中的 [關閉]。

## <a name="see-also"></a>另請參閱

- [管理負載測試結果存放庫中的負載測試結果](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [測試控制器和測試代理程式](configure-test-agents-and-controllers-for-load-tests.md)
