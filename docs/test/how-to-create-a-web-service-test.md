---
title: 建立 Web 服務測試
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a6e42d6d92a74a0fc8be96c966b9146b7888b9e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589093"
---
# <a name="how-to-create-a-web-service-test"></a>如何：建立 Web 服務測試

您可以使用 Web 效能測試以測試 Web 服務。 藉由使用 [插入要求]**** 和 [插入 Web 服務要求]**** 選項，您可以在 [Web 效能測試編輯器]**** 中自訂個別要求，以便找到 Web 服務頁面。 一般而言，這些頁面不會顯示在 Web 應用程式中。 因此，您必須自訂要求，以取得這些頁面的存取權。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

下列程序使用 Commerce Starter Kit 內所包含的 Web 服務。 你可以從[ASP.NET商務入門工具組](https://sourceforge.net/projects/ppcsk/)下載它。

**需求**

Visual Studio Enterprise

## <a name="to-test-a-web-service"></a>測試 Web 服務

1. 建立新的 Web 效能測試。 在瀏覽器開啟後，選擇 [停止]****。

2. 在 [Web 效能測試編輯器]**** 中，以滑鼠右鍵按一下 Web 效能測試，然後選取 [新增 Web 服務要求]****。

3. 在新要求的 [Url]**** 屬性中，鍵入 Web 服務的名稱，例如 **http://localhost/storecsvs/InstantOrder.asmx**。

4. 打開瀏覽器的單獨會話，並在 **"位址"** 工具列中鍵入 *.asmx*頁的 URL。 請選取要測試的方法，並檢查 SOAP 訊息， 其中包含 `SOAPAction`。

5. 在 [Web 效能測試編輯器]**** 中，以滑鼠右鍵按一下要求，然後選取 [新增標頭]**** 新增新的標頭。 在 [名稱]**** 屬性中，鍵入 `SOAPAction`。 在 [值]**** 屬性中，鍵入您在 `SOAPAction` 中所看到的值，例如 `"http://tempuri.org/CheckStatus"`。

6. 在編輯器中展開 URL 節點，選擇 [字串內容]**** 節點，然後在 [內容類型]**** 屬性中輸入值 `text/xml`。

7. 返回步驟 4 中的瀏覽器，從 Web 服務描述頁面選取 SOAP 要求的 XML 部分，並將它複製到剪貼簿。

8. XML 內容類似於下列範例：

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
     <soap:Body>
       <CheckStatus xmlns="http://tempuri.org/">
         <userName>string</userName>
         <password>string</password>
         <orderID>int</orderID>
       </CheckStatus>
     </soap:Body>
     </soap:Envelope>
     ```

9. 返回到**Web 效能測試編輯器**，然後在**字串正文**屬性中選擇省略號 **（...）。** 將剪貼簿的內容貼到屬性中。

10. 為了讓測試通過，您必須以有效的值取代 XML 中任何的預留位置值。 在先前的範例中，您可能取代 `string` 的兩個執行個體 (Instance) 和一個 `int`。 這個 Web 服務作業只有在存有編排順序的已註冊使用者時才會完成。

11. 以滑鼠右鍵按一下 Web 服務要求，然後選取 [新增 URL QueryString 參數]****。

12. 為查詢字串參數指派一個名稱和值。 在先前的範例中，名稱為 `op`，而值為 `CheckStatus`。 這會識別要執行的 Web 服務作業。

    > [!NOTE]
    > 您可以在 SOAP 主體中使用資料繫結，以便使用 `{{DataSourceName.TableName.ColumnName}}` 語法以資料繫結值取代任何預留位置值。

13. 執行測試。 在 [Web 效能測試結果檢視器]**** 的上方窗格中，選取 Web 服務要求。 在底部窗格中，選擇 Web 瀏覽器選項卡。將顯示 Web 服務返回的 XML 以及任何操作的結果。

## <a name="see-also"></a>另請參閱

- [為負載測試建立自訂程式碼和外掛程式](../test/create-custom-code-and-plug-ins-for-load-tests.md)
