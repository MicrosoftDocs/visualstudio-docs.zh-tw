---
title: Web 效能測試 API
description: 瞭解 web 效能測試 API，該 API 支援程式碼 web 效能測試、測試外掛程式、要求外掛程式、要求和解壓縮/驗證規則。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: f2afc1ab325fab8da6bdaba5650ae06d9cfcce14
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969226"
---
# <a name="how-to-use-the-web-performance-test-api"></a>如何：使用 Web 效能測試 API

您可以為 Web 效能測試撰寫程式碼。 Web 效能測試 API 可以用來建立 Web 效能測試程式碼、Web 效能測試外掛程式、要求外掛程式、要求、擷取規則和驗證規則。 構成這些型別的類別，就是這個 API 中的核心類別。 這個 API 中的其他類型可用來支援 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest>、<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>、<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>、<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest>、<xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> 和 <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> 等物件的建立。 您可以使用 <xref:Microsoft.VisualStudio.TestTools.WebTesting> 命名空間來建立自訂 Web 效能測試。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

您也可以使用 Web 效能測試 API，以程式設計方式建立及儲存宣告式 Web 效能測試。 若要這樣做，請使用 <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> 和 <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer> 類別。

> [!TIP]
> 使用物件瀏覽器檢查 <xref:Microsoft.VisualStudio.TestTools.WebTesting> 命名空間。 Visual C# 和 Visual Basic 編輯器都提供 IntelliSense 支援，以便使用命名空間中的類別來撰寫程式碼。

您也可以為負載測試建立外掛程式。 如需詳細資訊，請參閱 [如何：使用負載測試 API](../test/how-to-use-the-load-test-api.md) 和 how [to：建立負載測試外掛程式](../test/how-to-create-a-load-test-plug-in.md)。

## <a name="to-use-the-webtesting-namespace"></a>若要使用 WebTesting 命名空間

1. 開啟包含 Web 效能測試的 Web 效能和負載測試專案。

2. 將 Visual C# 或 Visual Basic 類別庫專案加入至測試方案。

3. 將 Web 效能和負載測試專案的參考加入至類別庫專案。

4. 將參考加入至類別庫專案中的 Microsoft.VisualStudio.QualityTools.WebTestFramework DLL。

5. 在類別庫專案的類別檔中，為 `using` 命名空間加入 <xref:Microsoft.VisualStudio.TestTools.WebTesting> 陳述式。

6. 建立實作 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> 介面的類別。

7. 建置專案。

8. 使用 [Web 效能測試編輯器] 加入新的 Web 效能測試外掛程式：

    1. 選擇工具列上的 [新增 Web 測試外掛程式]。

         [新增 Web 測試外掛程式] 對話方塊隨即出現。

    2. 在 **[選取外掛程式]** 底下，選取您的 web 效能測試外掛程式類別。

    3. 在 [所選外掛程式的屬性] 窗格中，設定外掛程式要在執行階段中使用的初始值。

        > [!NOTE]
        > 您可以從外掛程式公開任意數目的屬性，只要讓這些屬性成為公用、可設定且屬於基底型別 (例如整數、布林或字串) 的屬性即可。 您之後也可以使用 [屬性] 視窗來編輯 Web 效能測試外掛程式屬性。

    4. 選擇 [確定]。

9. 執行您的 Web 效能測試。

     如需的範例執行 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> ，請參閱 [如何：建立 web 效能測試外掛程式](../test/how-to-create-a-web-performance-test-plug-in.md)。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [為負載測試建立自訂程式碼和外掛程式](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [如何：使用負載測試 API](../test/how-to-use-the-load-test-api.md)
- [如何：建立 web 效能測試外掛程式](../test/how-to-create-a-web-performance-test-plug-in.md)
