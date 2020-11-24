---
title: 建立 Web 服務測試
description: 瞭解如何使用 web 服務的效能測試，並在 Web 效能測試編輯器中自訂要求以找出 web 服務頁面。
ms.custom: SEO-VS-2020
ms.date: 06/30/2020
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 32b5a6a91221e8942faeefcb89cfc52dd0cc5895
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95439923"
---
# <a name="how-to-create-a-web-service-test"></a>如何：建立 Web 服務測試

您可以使用 Web 效能測試以測試 Web 服務。 藉由使用 [插入要求] 和 [插入 Web 服務要求] 選項，您可以在 [Web 效能測試編輯器] 中自訂個別要求，以便找到 Web 服務頁面。 一般而言，這些頁面不會顯示在 Web 應用程式中。 因此，您必須自訂要求，以取得這些頁面的存取權。

>[!NOTE]
> Web 效能和負載測試功能在 Visual Studio 2019 中已淘汰。 針對 Application Insights，多步驟 web 測試取決於 Visual Studio 的 webtest 檔。 已[宣佈](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/) Visual Studio 2019 會是具有 Webtest 功能的最後一個版本。 請務必瞭解，雖然不會新增任何新功能，但目前仍支援 Visual Studio 2019 中的 Webtest 功能，並且會在產品的支援生命週期中繼續受到支援。 Azure 監視器產品小組已解決多步驟可用性測試的相關問題，如[這裡](https://github.com/MicrosoftDocs/azure-docs/issues/26050#issuecomment-468814101)所示。

**Requirements**

Visual Studio Enterprise

## <a name="to-create-a-simple-web-service"></a>建立簡單的 web 服務

若要進行測試，您可以使用自己的 web 服務，或使用 Visual Studio 中包含的基本 Web 服務 (.ASMX) 範本。 若要使用此範本建立簡單的 web 服務：

1. 在 Visual Studio 中，使用 ASP.NET Web 應用程式 ( .NET Framework) 範本來建立新專案，然後在出現提示時選取 **空白** 的範本。 輸入名稱，並建立專案。

1. 在方案總管中，以滑鼠右鍵按一下專案節點，選擇 [**加入**  >  **新專案**]，然後選擇 [ **Web 服務 (.asmx])**。 新增 web 服務。

1. 開啟 *WebService1* ，並以下列程式碼取代預設的 `HelloWorld` web 方法。

   ```csharp
   public string HelloWorld(string str)
   {
      return "Hello, " + str;
   }
   ```

## <a name="install-the-load-testing-component"></a>安裝負載測試元件

如果您尚未安裝 Web 效能與負載測試工具元件，您需要透過 Visual Studio 安裝程式來安裝它。

1. 從 Windows 的 [**開始**] 功能表開啟 **Visual Studio 安裝程式**。 您也可以從 [新增專案] 對話方塊，或從功能表列選擇 [**工具**  >  **取得工具和功能**]，在 Visual Studio 中存取它。

1. 在 [Visual Studio 安裝程式] 中，選擇 [個別元件] 索引標籤，然後向下捲動至 [偵錯和測試] 區段。 選取 [Web 效能與負載測試工具]。

   ![Web 效能與負載測試工具元件](media/web-perf-load-testing-tools-component.png)

1. 選擇 [修改] 按鈕。

   Web 效能與負載測試工具元件隨即安裝。

## <a name="create-a-web-test-project"></a>建立 web 測試專案

Web 測試需要 Web 效能和負載測試專案專案範本。 在本節中，我們將建立 C# 負載測試專案。 如果您想要的話，您也可以建立 Visual Basic 負載測試專案。

::: moniker range="vs-2017"

1. 開啟 Visual Studio。

   如果您使用 (.ASMX) 範本的範例 Web 服務，您可以將 web 測試專案加入至相同的方案。

2. 從功能表列中選擇 [檔案]**[新增]** > **[專案]** > 。

   此時會開啟 [新增專案] 對話方塊。

3. 在 [新增專案] 對話方塊中，依序展開 [已安裝的] 和 [Visual C#]，然後選取 [測試] 分類。 選擇 [Web 效能和負載測試專案] 範本。

   ![Web 效能和負載測試專案範本](media/web-perf-load-test-project-template.png)

4. 如果您不想要使用預設名稱，請輸入專案的名稱，然後選擇 [確定]。

::: moniker-end

::: moniker range=">=vs-2019"

1. 開啟 Visual Studio。

   如果您使用 (.ASMX) 範本的範例 Web 服務，您可以將 web 測試專案加入至相同的方案。

2. 在 [開始] 視窗中，選擇 [ **建立新專案**]。

3. 在 [建立新專案] 頁面，於搜尋方塊內鍵入 **web test**，然後選取 C# 的 [Web 效能和負載測試專案] \[已淘汰] 範本。 選擇 [下一步]  。

4. 如果您不想要使用預設名稱，請輸入專案的名稱，然後選擇 [建立]。

::: moniker-end

   Visual Studio 會建立專案，並在 **方案總管** 中顯示檔案。 專案一開始會包含一個名為 *webtest1.webtest webtest* 的 web 測試檔案。

## <a name="to-test-a-web-service"></a>測試 Web 服務

1. 啟動您的 web 服務，如有必要，請選擇 [ **停止** ] 以暫停服務。

1. 在 web 測試專案中，開啟 *webtest1.webtest webtest*，這會開啟 Web 效能測試編輯器。 在 [測試編輯器] 中，以滑鼠右鍵按一下 web 效能測試，然後選取 [ **新增 Web 服務要求**]。

1. 在新要求的 [Url] 屬性中，鍵入 Web 服務的名稱，例如 **https://localhost:44318/WebService1.asmx**。

1. 針對 web 服務，開啟瀏覽器的另一個會話，並在 [**位址**] 工具列中輸入 *.ASMX* 頁面的 URL。 在網頁頂端，選取您要測試的方法，然後檢查 SOAP 訊息。  (在 web 服務範例中，方法是 HelloWorld ) 。當您開啟方法時，您會看到它包含 `SOAPAction` 。

1. 在 [Web 效能測試編輯器] 中，以滑鼠右鍵按一下要求，然後選取 [新增標頭] 新增新的標頭。 在 [名稱] 屬性中，鍵入 `SOAPAction`。 在 [ **值** ] 屬性中，輸入您在中看到的值 `SOAPAction` ，例如 *http://tempuri.org/HelloWorld* 。

1. 展開 [測試編輯器] 中的 [URL] 節點，選擇 [ **字串** 內容] 節點，然後在 [ **內容類型** ] 屬性中輸入的值 `text/xml` 。

1. 返回步驟 4 中的瀏覽器，從 Web 服務描述頁面選取 SOAP 要求的 XML 部分，並將它複製到剪貼簿。

   XML 內容類似於下列範例：

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
       <soap:Body>
         <HelloWorld xmlns="http://tempuri.org/">
           <str>string</str>
         </HelloWorld>
       </soap:Body>
     </soap:Envelope>
     ```

1. 返回 Web 效能測試編輯器，然後選擇 [**字串主體**] 屬性中的省略號 **( ... )** 。 將剪貼簿的內容貼到屬性中。

1. 將 XML 中的任何預留位置值取代為有效的值，以便測試可通過。 在上述範例中，您會將的實例取代為 `string` 名稱。

1. 以滑鼠右鍵按一下 Web 服務要求，然後選取 [新增 URL QueryString 參數]。

1. 為查詢字串參數指派一個名稱和值。 在先前的範例中，名稱為 `op`，而值為 `HelloWorld`。 這會識別要執行的 Web 服務作業。

    > [!NOTE]
    > 您可以使用語法，在 SOAP 主體中使用資料系結，以資料系結值取代任何預留位置值 `{{DataSourceName.TableName.ColumnName}}` 。

1. 執行測試。 在 [Web 效能測試結果檢視器] 的上方窗格中，選取 Web 服務要求。 在下方窗格中，選取 [ **網頁瀏覽器** ] 索引標籤。Web 服務所傳回的 XML，以及任何作業的結果都會顯示。

   尋找您的 web 服務要求結果。

## <a name="see-also"></a>另請參閱

- [為負載測試建立自訂程式碼和外掛程式](../test/create-custom-code-and-plug-ins-for-load-tests.md)
