---
title: 為 RequireJS 自訂 IntelliSense |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 2be07ef8-9c08-444b-a21a-22a4fe6386a3
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5bcf5f27653782d0280082713306e142702559c8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770311"
---
# <a name="customizing-intellisense-for-requirejs"></a>為 RequireJS 自訂 IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

從 Visual Studio 2013 Update 4 開始，提供對熱門 RequireJS JavaScript 檔案和模組化載入器的支援。 RequireJS 可讓您更輕鬆地定義程式碼模組之間的相依性，並只在需要時才以動態方式載入模組。 撰寫使用 RequireJS 的 JavaScript 程式碼時，會提供 IntelliSense 的模組建議，您可以從模組定義參考這些建議，或從程式碼內使用 `require()` 呼叫參考這些建議。  
  
 根據預設，Visual Studio 支援非常基本的組態，以支援 RequireJS，但常見的作法是設定您自己的自訂組態設定 (亦即定義程式庫的別名)。 本主題說明您可以自訂 Visual Studio 的不同方式，以使用專案的唯一設定。  
  
 本主題說明如何：  
  
-   在 ASP.NET 專案中自訂 RequireJS  
  
-   在 JSProj 專案中自訂 RequireJS，這些專案可用來建置 Apache Cordova 應用程式、Windows 市集應用程式和 LightSwitch HTML 應用程式  
  
## <a name="customize-requirejs-in-aspnet-projects"></a>在 ASP.NET 專案中自訂 RequireJS  
 當目前的 JavaScript 檔案參考名為 require.js 的檔案時，會自動啟用對 RequireJS 的支援 (如需詳細資訊，請參閱 [JavaScript IntelliSense](../ide/javascript-intellisense.md) 中的＜判斷 IntelliSense 的內容＞一節)。 在 ASP.NET 專案中，通常是在 _references.js 檔案中使用 /// \<reference/> 指示詞來參考 require.js。  
  
### <a name="configure-the-data-main-attribute-in-an-aspnet-project"></a>在 ASP.NET 專案中設定 data-main 屬性  
 為了精確地模擬應用程式在執行時的運作方式，JavaScript 編輯器必須知道設定 require.js 時所要先載入的檔案。 這通常會使用參考 require.js 之指令碼項目上的 `data-main` 屬性，在您的應用程式 HTML 檔案中進行設定，如下所示。  
  
```html  
<script src="js/require.js" data-main="js/app.js"></script>  
```  
  
 在這個範例中，系統會在 require.js 之後立即載入 data-main (js/app.js) 所參考的指令碼。 立即載入的檔案是最先設定 RequireJS 使用量 (使用 `require.config()`) 的最佳位置。若要通知 JavaScript 編輯器哪個檔案要用於應用程式中的 `data-main`，請新增 `data-main` 屬性，然後修改應用程式中參考 require.js 的 /// \<reference/> 指示詞。 例如，您可以使用這個指示詞：  
  
```javascript  
/// <reference path="js/require.js" data-main="js/app.js" />  
```  
  
### <a name="configure-the-application-start-page-in-an-aspnet-project"></a>在 ASP.NET 專案中設定應用程式起始頁  
 當應用程式執行時，RequireJS 假設相對檔案路徑 (例如，"...\\"路徑） 是相對於載入 require.js 程式庫的 HTML 檔案。 當您在 Visual Studio 編輯器中為 ASP.NET 專案撰寫程式碼時，這個起始頁不明，您必須告知編輯器使用相對檔案路徑時所要使用的起始頁。 為了達成這個目的，請將 `start-page` 屬性新增至您的 /// \<reference/> 指示詞。  
  
```javascript  
/// <reference path="js/require.js" data-main="js/app.js" start-page="/app/index.html" />  
```  
  
 `start-page` 屬性會指定您執行應用程式時，會在瀏覽器中看到之頁面的 URL。  
  
## <a name="customize-requirejs-in-jsproj-projects"></a>在 JSProj 專案中自訂 RequireJS  
 建置 Apache Cordova 應用程式、以 HTML 為基礎的 Windows 市集應用程式或 LightSwitch HTML 應用程式時，會使用 JSProj 專案 (專案檔的副檔名為 .jsproj)。 不同於 ASP.NET 專案，這些專案會從專案中現有的 HTML 檔讀取 .js 檔的參考。 因此，在 JSProj 專案中編輯 JavaScript 時，如果另一個也參考 require.js 的 HTML 檔參考目前正在編輯的 JavaScript 檔，您會看到 RequireJS 支援已啟用。  
  
 在 JSProj 專案檔中不需要 ASP.NET 專案所需的自訂步驟。 換言之，系統會自動載入參考 require.js 的指令碼標記上的 `data-main` 屬性所使用的指令碼檔，以便設定 require.js。 參考 require.js 的 HTML 檔也會做為應用程式的起始頁。  
  
## <a name="see-also"></a>請參閱  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)
