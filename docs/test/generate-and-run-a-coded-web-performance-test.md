---
title: 自動程式化 Web 效能測試
description: 瞭解如何將 web 效能測試轉換成以程式碼為基礎的腳本，讓您可以編輯和自訂。
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, creating
- code, Web performance tests
- Web performance tests, coded
ms.assetid: 169e48f9-52fd-4d0b-83d9-54913bde506b
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 74269872992935568362a061d47f7335dbaedec8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936414"
---
# <a name="generate-and-run-a-coded-web-performance-test"></a>產生和執行 Web 效能測試程式碼

Web 效能測試是透過瀏覽您的 Web 應用程式來錄製。 測試包含在負載測試中，測量您的 Web 應用程式在多個使用者壓力下的執行效能。 可將 Web 效能測試轉換成程式碼指令碼，您可以像編輯和自訂其他原始程式碼一樣編輯這個指令碼。 例如，您可以加入迴圈和分支建構。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="generate-a-coded-web-performance-test"></a>產生 Web 效能測試程式碼

1. 如果您尚未建立 Web 效能測試，請參閱[錄製 Web 效能測試](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-web-performance-and-load-test-project)。

2. 產生程式碼測試。

     ![產生 Web 效能測試程式碼](../test/media/web_test_coded_generate.png)

3. 為測試命名。

     ![輸入 Web 效能測試程式碼的名稱](../test/media/web_test_coded_generate_nametest.png)

     新的程式碼測試會在程式碼編輯器中開啟。

     根據您加入方案的 Web 效能和負載測試專案範本，將會決定採用 Visual Basic 或 Visual C# 產生程式碼。

     ![新的測試程式碼隨即在 [程式碼編輯器] 中開啟](../test/media/web_test_coded_generate_opencodeeditor.png)

     您在程式碼中可以看到 GetRequestEnumerator() 方法 (C#) 或 Run() 方法 (Visual Basic) 包含已錄製之測試的每個驗證規則與 Web 要求。

4. 為了示範加入一些簡單程式碼，請向下捲動到方法的結尾，並在最後一個 Web 要求的程式碼之後加入下列程式碼：

    ```c#
    if (DateTime.Today.DayOfWeek == DayOfWeek.Wednesday)
    {
        WebTestRequest customRequest = new WebTestRequest("http://weather.msn.com/");
        yield return customRequest;
    }
    else
    {
        WebTestRequest customRequest = new WebTestRequest("https://msdn.microsoft.com/");
        yield return customRequest;
    }
    ```

    ```vb
    If DateTime.Today.DayOfWeek = DayOfWeek.Wednesday Then
        Dim customRequest As WebTestRequest = New WebTestRequest("http://weather.msn.com/")
        MyBase.Send(customRequest)
    Else
        Dim customRequest As WebTestRequest = New WebTestRequest("https://msdn.microsoft.com/")
        MyBase.Send(customRequest)
    End If
    ```

5. 建置方案來驗證您的自訂程式碼編譯。

6. 執行測試。

     ![執行自動程式化 Web 效能測試](../test/media/web_test_coded_generate_run.png)

     而且，因為執行當天剛好是星期三…

     ![Web 效能測試程式碼結果](../test/media/web_test_coded_generate_results.png)

## <a name="qa"></a>問答集

### <a name="q-can-i-run-more-than-one-test-at-a-time"></a>問：我可以同時執行多個測試嗎？
**答：** 是，請在 **方案總管** 中使用滑鼠右鍵 (內容) ] 功能表。

### <a name="q-should-i-add-a-data-source-before-or-after-i-generate-a-coded-test"></a>問：我應該在產生程式碼測試之前或之後加入資料來源？
**答：** 在您產生自動程式化測試之前，新增 [資料來源](../test/add-a-data-source-to-a-web-performance-test.md)比較容易，因為會自動產生程式碼。

當您執行具有資料來源的程式碼測試時，可能會看到下列錯誤訊息：

**無法 \<Test Name> 在代理程式上執行測試 \<Computer Name> ：物件參考未設定為物件的實例。**

發生此錯誤的原因是測試類別擁有已定義的 DataSourceAttribute，而沒有相對應的 DataBindingAttribute。 若要解決這個錯誤，請加入適當的 DataBindingAttribute、刪除它，或在程式碼註解它。

### <a name="q-should-i-add-validation-and-extraction-rules-before-or-after-i-generate-a-coded-test"></a>問：我應該在產生程式碼測試之前或之後加入驗證和擷取規則？
**答：** 在產生自動程式化測試之前新增驗證規則和擷取規則比較容易；不過建議您使用 [自動程式化 UI 測試](../test/use-ui-automation-to-test-your-code.md)進行驗證。
