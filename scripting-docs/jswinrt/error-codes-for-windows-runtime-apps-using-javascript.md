---
title: 使用 JavaScript 的 Windows 執行階段應用程式錯誤碼 | Microsoft Docs
ms.custom: ''
ms.date: 05/10/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- JavaScript, Windows Runtime error codes
- VS.WebClient.Help.APPHOST9601
- VS.WebClient.Help.APPHOST9602
- VS.WebClient.Help.APPHOST9603
- VS.WebClient.Help.APPHOST9604
- VS.WebClient.Help.APPHOST9605
- VS.WebClient.Help.APPHOST9606
- VS.WebClient.Help.APPHOST9607
- VS.WebClient.Help.APPHOST9608
- VS.WebClient.Help.APPHOST9610
- VS.WebClient.Help.APPHOST9611
- VS.WebClient.Help.APPHOST9613
- VS.WebClient.Help.APPHOST9614
- VS.WebClient.Help.APPHOST9615
- VS.WebClient.Help.APPHOST9616
- VS.WebClient.Help.APPHOST9617
- VS.WebClient.Help.APPHOST9618
- VS.WebClient.Help.APPHOST9619
- VS.WebClient.Help.APPHOST9620
- VS.WebClient.Help.APPHOST9623
- VS.WebClient.Help.APPHOST9624
- VS.WebClient.Help.APPHOST9626
ms.assetid: 4c6d4e90-602a-4b56-ae74-3458929da442
caps.latest.revision: 1
author: erikadoyle
ms.author: edoyle
manager: jken
ms.openlocfilehash: 89b91a3246d0a6e2980459c2c35c7361168bccd4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24571508"
---
# <a name="error-codes-for-windows-runtime-apps-using-javascript"></a>使用 JavaScript 的 Windows 執行階段應用程式錯誤碼
以下是使用 JavaScript 開發 Windows 執行階段應用程式時，由 Microsoft Visual Studio 主控台所顯示的錯誤碼。
  
錯誤 | 備註
----- | -------
APPHOST9601：「無法載入 remoteURI。 應用程式無法在本機內容中載入遠端網路內容。」 | 如需 Web 內容中所允許作業的詳細資訊，請參閱[受內容影響的功能和限制 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx)。
APPHOST9602：「'javascript:' 是無效的屬性值，因此將予以忽略。 請勿在本機內容中使用 'javascript:' URI。」 | 基於安全性理由，您無法在本機內容中使用 'javascript:' URI。 如需本機內容中所允許作業的詳細資訊，請參閱[受內容影響的功能和限制 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx)。
APPHOST9603：「無法載入類別識別碼為 classID 的 ActiveX 外掛程式。  應用程式無法載入 ActiveX 控制項。」 | 使用 JavaScript 的 Windows 執行階段應用程式不支援自訂 Microsoft ActiveX 控制項。 如果您需要 UI 控制項，請使用標準 Web 控制項、控制項程式庫，或建立您自己的自訂控制項。 如果您需要執行自訂邏輯，請改為建立自訂 Windows 執行階段物件。 如需其他 HTML、CSS 和 JavaScript 差異的資訊，請參閱 [HTML、CSS 以及 JavaScript 功能和差異 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465380.aspx)。
APPHOST9604：「無法巡覽至 *uri*，因為它使用無效的字元編碼。  應用程式只能巡覽使用 UTF8 編碼的檔案。」 | Windows 執行階段所存取的所有 HTML、JavaScript 和 CSS 都必須編碼為 8 位元 Unicode 轉換格式 (UTF-8)。 如需其他 HTML、CSS 和 JavaScript 差異的資訊，請參閱 [HTML、CSS 以及 JavaScript 功能和差異 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465380.aspx)。
APPHOST9605：「無法從 *sourceURI* 巡覽至 targetURI，因為目的地 URI 是位於較高的安全性區域。 您無法從安全性較低的區域瀏覽安全性較高的區域，除非您是從網路內容 URI 巡覽本機內容 URI 且您已使用 MSApp.addPublicLocalApplicationUri 方法登錄該本機內容 URI。」 | 如需詳細資訊，請參閱 [MSApp.addPublicLocalApplicationUri](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465759.aspx)。
APPHOST9606：「無法載入 *uri*，因為它使用 HTTP 連線，且 ms-https-connections-only meta 項目已存在。 當您使用 ms-https-connections-only meta 項目時，只允許 HTTPS 連線。 請使用 HTTPS 連線，或者，若不需要安全連線，請移除該中繼項目。」 | 如需詳細資訊，請參閱[如何要求 HTTPS 連線](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh452771.aspx)。
APPHOST9607：「應用程式無法啟動 *uri* 的 URI，因為發生下列錯誤: failureCode。」 | 遺漏資源或無效檔案是這個錯誤的常見原因。
APPHOST9608：「應用程式無法巡覽至 about:blank 頁面，因為發生下列錯誤: errorCode。」 | 
APPHOST9610：「應用程式準備巡覽至自訂的錯誤頁面時發生錯誤: *errorCode*。」 |
APPHOST9611：「應用程式無法巡覽至自訂錯誤頁面，因為發生下列錯誤: errorCode。」 |
APPHOST9613：「應用程式無法巡覽至 * uri*，因為發生下列錯誤: errorCode。」 | 
APPHOST9614：「iframe 中的文件要求 *requestedDocMode* 文件模式，但系統強制使用 *currentDocMode* 文件模式。 iframe 將使用 *currentDocMode* 文件模式。」 | 如需顯示遠端 Web 內容的詳細資訊，請參閱[如何連結至外部網頁 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh780594.aspx)。
APPHOST9615：「應用程式無法下載位於 *uri* 的檔案，因為它是使用程式設計方式從本機內容以外叫用。」 | 發生於 Web 內容中的內容嘗試以程式設計方式下載檔案時。
APPHOST9616：「此 URI 無法使用地理位置 API。  只能從屬於套件之一部分的 URI 或包含在資訊清單之 ApplicationContentUris 項目的 URI 叫用地理位置 API。」 | 如需 Web 內容中所允許作業的詳細資訊，請參閱[受內容影響的功能和限制 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx)。
APPHOST9617：「此 URI 無法使用剪貼簿 API。  只能從屬於套件之一部分的 URI 或包含在資訊清單之 ApplicationContentUris 項目的 URI 叫用剪貼簿 API。」 | 如需 Web 內容中所允許作業的詳細資訊，請參閱[受內容影響的功能和限制 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx)。
APPHOST9618：「此 URI 無法使用 window.close。  只能從使用 ms-appx URI 配置載入的已封裝內容叫用 window.close 方法。」 | 如需 Web 內容中所允許作業的詳細資訊，請參閱[受內容影響的功能和限制 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx)。
APPHOST9619：「應用程式無法巡覽至 *uri*，因為網路內容中的頁面不能是應用程式的最上層文件。 請改為在 iframe 中載入該頁面。」 | 您無法從最上層頁面巡覽至遠端網頁，但應用程式可以在 [iframe](https://msdn.microsoft.com/en-us/library/ms535258(v=vs.85).aspx) 中顯示網頁。 如需顯示遠端 Web 內容的詳細資訊，請參閱[如何連結至外部網頁 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh780594.aspx)。
APPHOST9620：「已關閉此應用程式，因為它使用 HTTP 連線，且 ms-https-connections-only 中繼項目已存在。 當您使用 ms-https-connections-only meta 項目時，只允許 HTTPS 連線。 請使用 HTTPS 連線，或者，若不需要安全連線，請移除該中繼項目。」 | 如需詳細資訊，請參閱[如何要求 HTTPS 連線](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh452771.aspx)。
APPHOST9623：「應用程式無法解析 *url*，因為發生下列錯誤: errorCode。」 | 此錯誤的常見原因是遺漏檔案。  
APPHOST9624：「應用程式無法使用指令碼來載入 *url* URL，因為該 URL 會啟動另一個應用程式。 只有直接使用者互動可以載入另一個應用程式。」 | 應用程式無法直接啟動其他應用程式。 應用程式實作特定協定時，使用者可以啟動其他應用程式。 如需詳細資訊，請參閱[應用程式協定與延伸模組](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh464906.aspx)。
APPHOST9626：「偵測到對資源檔 `ms-appx://1d33240b-0b00-40e4-a416-a4750c48787f/ja-jp\images\logo.scale-140.png` 的直接參照。 在偵錯環境之外使用時，此參照導致失敗。」 | 因為 `logo.scale-140.png` 的檔案路徑，所以會將此 PNG 檔案視為當地語系化資源，因而導致無法直接參考該當地語系化資源的錯誤。 如果您想要使用此檔案作為語言資源，請參閱[全球化您的應用程式 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465006.aspx)。 否則，請嘗試重新命名有問題的目錄。
  
## <a name="see-also"></a>另請參閱  
 [在 JavaScript 中使用 Windows 執行階段](../jswinrt/using-the-windows-runtime-in-javascript.md)