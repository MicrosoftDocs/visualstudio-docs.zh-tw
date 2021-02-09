---
title: 負載測試 API
description: 瞭解如何使用支援測試外掛程式的負載測試 API （可控制或增強負載測試）。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- APIs, load tests
ms.assetid: e15567bc-1f21-4feb-b81d-f17ba35cfde5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 281e64f83766b6b42dd9f076726c429c9432245b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879549"
---
# <a name="how-to-use-the-load-test-api"></a>如何：使用負載測試 API

Visual Studio 支援能夠控制或增強負載測試的負載測試外掛程式。 負載測試外掛程式是使用者定義的類別，能夠實作 <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> 命名空間中的 <xref:Microsoft.VisualStudio.TestTools.LoadTesting> 介面， 讓您可以使用自訂的負載測試控制項，例如，在計數器或錯誤臨界值到達所設定的值時，中止負載測試。 請使用 <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> 類別上的屬性，以取得或設定使用者定義程式碼中的負載測試參數， 也可以使用 <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> 類別上的事件，在負載測試執行時，附加告知的委派 (Delegate)。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> 使用物件瀏覽器檢查 <xref:Microsoft.VisualStudio.TestTools.LoadTesting> 命名空間。 Visual C# 和 Visual Basic 編輯器都提供 IntelliSense 支援，以便使用命名空間中的類別來撰寫程式碼。

您也可以建立 Web 效能測試的外掛程式。 如需詳細資訊，請參閱 [如何：建立 web 效能測試外掛程式](../test/how-to-create-a-web-performance-test-plug-in.md) 和 [如何：建立要求層級外掛程式](../test/how-to-create-a-request-level-plug-in.md)。

## <a name="to-use-the-loadtesting-namespace"></a>若要使用 LoadTesting 命名空間

1. 開啟包含負載測試的 Web 效能和負載測試專案。

2. 將 Visual C# 或 Visual Basic 類別庫專案加入至測試方案。

3. 將 Web 效能和負載測試專案的參考加入至類別庫專案。

4. 將參考加入至「類別庫」專案中的 Microsoft.VisualStudio.QualityTools.LoadTestFramework DLL。

5. 在類別庫專案的類別檔中，為 `using` 命名空間加入 <xref:Microsoft.VisualStudio.TestTools.LoadTesting> 陳述式。

6. 建立實作 <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> 介面的公用類別。

7. 建置專案。

8. 使用 [負載測試編輯器] 加入新的負載測試外掛程式。

    1. 以滑鼠右鍵按一下負載測試的根節點，然後選擇 [新增負載測試外掛程式]。

    2. [新增負載測試外掛程式] 對話方塊隨即顯示。

    3. 在 [所選外掛程式的屬性] 窗格中，設定外掛程式要在執行階段中使用的初始值。

        > [!NOTE]
        > 您可以從外掛程式公開任意數量的屬性。只要讓它們成為公用、可設定的，以及基底類型，例如整數、布林值或字串。 您之後也可以使用 [屬性] 視窗來編輯負載測試外掛程式屬性。

9. 執行負載測試。

     如需的執行 <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> ，請參閱 [如何：建立負載測試外掛程式](../test/how-to-create-a-load-test-plug-in.md)。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- [為負載測試建立自訂程式碼和外掛程式](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [如何：使用 web 效能測試 API](../test/how-to-use-the-web-performance-test-api.md)
- [如何：建立負載測試外掛程式](../test/how-to-create-a-load-test-plug-in.md)
