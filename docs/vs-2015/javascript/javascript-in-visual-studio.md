---
title: Visual Studio 中的 JavaScript | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1ad7efda94ea3914caafa39d39870a77b08056d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49278235"
---
# <a name="javascript-in-visual-studio"></a>Visual Studio 中的 JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript 是在 Visual Studio 中的第一級語言。 當您在 Visual Studio IDE 中撰寫 JavaScript 程式碼時，可以使用大部分或所有標準編輯輔助，包括程式碼片段、IntelliSense 等等。 您可以為許多應用程式類型和服務撰寫 JavaScript 程式碼。  
  
 如需 JavaScript 語言參考文件，請參閱 [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx)。  
  
 可能需要特定版本的 Visual Studio 或特定的 Visual Studio 擴充功能，才能開發特定應用程式類型和使用 HTML 和 JavaScript 的服務。 下列清單中有詳細資訊的連結。  
  
-   若要使用 Apache Cordova 來建立跨平台應用程式，請[取得 Visual Studio Tools for Apache Cordova](http://go.microsoft.com/fwlink/p/?LinkId=397606)。  
  
-   若要建立 [Windows 市集](http://dev.windows.com/develop)、[Windows Phone](http://dev.windows.com/develop) 及通用應用程式 (支援這兩種平台)，請[取得工具](http://dev.windows.com/en-us/develop/downloads)。  
  
-   若要建立雲端式服務，請參閱 [Microsoft Azure 網站](http://azure.microsoft.com/documentation/)。  
  
-   若要建立網站和 Web 應用程式，請參閱 [ASP.NET 網站](http://www.asp.net/get-started/websites)。  
  
    > [!NOTE]
    >  您可以建立空白 ASP.Net 網站，並用來進行 HTML、CSS 和 JavaScript 程式設計。 ASP.NET 所提供的 Webconfig 檔案可讓您在 Visual Studio 中偵錯 (或當您執行應用程式時，可以使用 F12 工具)。  
  
 Visual Studio 中的 JavaScript 編輯器會提供 IntelliSense 支援。 如需詳細資訊，請參閱 [JavaScript IntelliSense](../ide/javascript-intellisense.md)。  
  
## <a name="whats-new-in-javascript"></a>JavaScript 的新功能  
 下表中列出 JavaScript 的新功能。  
  
|功能|描述|  
|-------------|-----------------|  
|類別|新的語法支援[類別](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/class-statement-javascript.md)宣告。|  
|Promise|[Promise](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/promise-object-javascript.md) 使非同步撰寫程式碼更方便、更俐落。 同時支援 Promise 建構函式及 `all` 和 `race` 公用程式方法。|  
|Iterator|現在您可以反覆查看遞迴的物件 (包括陣列、類似陣列的物件和迭代器) ，叫用自訂的反覆項目攔截程序，來執行每個相異的屬性值陳述式。 如需詳細資訊，請參閱[迭代器和產生器](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/advanced/iterators-and-generators-javascript.md)。 **注意：** 目前還不支援產生器。|  
|Arrow 函式|Arrow 函式 (=>) 提供簡寫語法，用於 `function` 關鍵字，以語彙 `this` 繫結為特色。|  
|內建物件的新方法|[Array 物件](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/array-object-javascript.md)、[Math 物件](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/math-object-javascript.md)、[Number 物件](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/number-object-javascript.md)、[Object 物件](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/object-object-javascript.md)及 [String 物件](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/string-object-javascript.md)等內建物件包含許多新的公用程式函式和屬性，可用來操作和檢查資料。|  
|物件常值的增強功能|物件現在支援計算的屬性、簡潔的方法定義，以及簡寫語法，用於其值已初始化為相同名稱變數的屬性。 如需詳細資訊，請參閱[建立物件](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/creating-objects-javascript.md)。|  
|Proxy|[Proxy](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/proxy-object-javascript.md) 可為物件啟用自訂行為。|  
|剩餘參數|剩餘參數可讓您將函式呼叫中連續的引數轉為陣列。 如需詳細資訊，請參閱[函式](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/functions-javascript.md)。|  
|Spread 運算子|[spread 運算子](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md) (`…`) 會把可逐一查看的運算式擴充成個別的引數。 例如，`a.b(…array)` 和 `a.b.apply(a, array)` 大致上相同。|  
|Symbol|[Symbol](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/symbol-object-javascript.md) 物件可允許由其他程式碼將屬性新增到現有的物件，而不會干擾現有的物件屬性，也不會有非預期的可視性和其他未經協調的新增。|  
|範本字串|[範本字串](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/advanced/template-strings-javascript.md)是一種字串常值，可讓運算式被評估並與字串常值串連。|  
|Unicode 增強功能|已改善 Unicode 支援。 例如，新的逸出序列格式支援 astral 字碼指標 (超過 4 個十六進位數字的字碼指標)。 如需詳細資訊，請參閱[特殊字元](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/advanced/special-characters-javascript.md)。|  
|WeakSet|[WeakSet](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/weakset-object-javascript.md) 是一種物件集合，如果沒有任何其他地方參考它，就會由記憶體回收。|

