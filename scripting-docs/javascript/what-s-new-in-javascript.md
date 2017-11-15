---
title: "JavaScript 的新功能 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 342b68ef-df93-48c4-81de-bdf6b6ce58d9
caps.latest.revision: "33"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 540d10958a7f2d406a6d70a633fc09a2cada8f41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="what39s-new-in-javascript"></a>JavaScript 的新功能
本文件列出兩個[邊緣模式](http://blogs.msdn.com/b/ie/archive/2014/11/11/living-on-the-edge-our-next-step-in-interoperability.aspx)、[!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] 和 Windows Phone 市集應用程式都支援的 JavaScript 新功能。  
  
 若要了解在邊緣模式中支援，但 [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] 應用程式中即將淘汰的 JavaScript 項目，請參閱[版本資訊](../javascript/reference/javascript-version-information.md)。  
  
> [!IMPORTANT]
>  如需如何使用 JavaScript 建立 [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] 和 Windows Phone 市集應用程式的詳細資訊 (包括 Visual Studio JavaScript 編輯器和其他功能的資訊)，請參閱[使用 Visual Studio 2013 開發 Windows 市集應用程式](http://go.microsoft.com/fwlink/p/?LinkID=238263)。  
  
## <a name="new-features-in-javascript"></a>JavaScript 中的新功能  
  
|功能|描述|  
|-------------|-----------------|  
|類別|新的語法支援[類別](../javascript/reference/class-statement-javascript.md)宣告。|  
|Promise|[Promise](../javascript/reference/promise-object-javascript.md) 使非同步撰寫程式碼更方便、更俐落。 同時支援 Promise 建構函式及 `all` 和 `race` 公用程式方法。|  
|Iterator|現在您可以反覆查看遞迴的物件 (包括陣列、類似陣列的物件和迭代器) ，叫用自訂的反覆項目攔截程序，來執行每個相異的屬性值陳述式。 如需詳細資訊，請參閱[迭代器和產生器](../javascript/advanced/iterators-and-generators-javascript.md)。 **注意：**目前還不支援產生器。|  
|Arrow 函式|Arrow 函式 (=>) 提供簡寫語法，用於 `function` 關鍵字，以語彙 `this` 繫結為特色。|  
|內建物件的新方法|[Array 物件](../javascript/reference/array-object-javascript.md)、[Math 物件](../javascript/reference/math-object-javascript.md)、[Number 物件](../javascript/reference/number-object-javascript.md)、[Object 物件](../javascript/reference/object-object-javascript.md)及 [String 物件](../javascript/reference/string-object-javascript.md)等內建物件包含許多新的公用程式函式和屬性，可用來操作和檢查資料。|  
|物件常值的增強功能|物件現在支援計算的屬性、簡潔的方法定義，以及簡寫語法，用於其值已初始化為相同名稱變數的屬性。 如需詳細資訊，請參閱[建立物件](../javascript/creating-objects-javascript.md)。|  
|Proxy|[Proxy](../javascript/reference/proxy-object-javascript.md) 可為物件啟用自訂行為。|  
|剩餘參數|剩餘參數可讓您將函式呼叫中連續的引數轉為陣列。 如需詳細資訊，請參閱[函式](../javascript/functions-javascript.md)。|  
|Spread 運算子|[spread 運算子](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md) (`...`) 會把可逐一查看的運算式擴充成個別的引數。 例如，`a.b(...array)` 和 `a.b.apply(a, array)` 大致上相同。|  
|Symbol|[Symbol](../javascript/reference/symbol-object-javascript.md) 物件可允許由其他程式碼將屬性新增到現有的物件，而不會干擾現有的物件屬性，也不會有非預期的可視性和其他未經協調的新增。|  
|範本字串|[範本字串](../javascript/advanced/template-strings-javascript.md)是一種字串常值，可讓運算式被評估並與字串常值串連。|  
|Unicode 增強功能|已改善 Unicode 支援。 例如，新的逸出序列格式支援 astral 字碼指標 (超過 4 個十六進位數字的字碼指標)。 如需詳細資訊，請參閱[特殊字元](../javascript/advanced/special-characters-javascript.md)。|  
|WeakSet|[WeakSet](../javascript/reference/weakset-object-javascript.md) 是一種物件集合，如果沒有任何其他地方參考它，就會由記憶體回收。|  
  
## <a name="see-also"></a>另請參閱  
 [JavaScript 語言參考](../javascript/javascript-language-reference.md)