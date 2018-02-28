---
title: "GetObject 函式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GetObject
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetObject function
ms.assetid: 62efcdbc-8b86-491d-9000-ef38aa9942a9
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d8bad127a0f260395a1ec19f44ff2d495006024
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="getobject-function-javascript"></a>GetObject 函式 (JavaScript)
傳回對 Automation 物件的參考，從檔案。  
  
> [!NOTE]
>  在 Internet Explorer 9 （標準模式） 或更新版本不支援此函式。  
  
## <a name="syntax"></a>語法  
  
```  
GetObject([pathname] [, class])  
```  
  
## <a name="parameters"></a>參數  
 `pathname`  
 選擇項。 完整路徑和名稱，包含要擷取之物件的檔案。 如果`pathname`省略，則`class`需要。  
  
 `class`  
 選擇項。 物件的類別。  
  
 `class`引數會使用語法`appname.objectype`並包含下列部分：  
  
 `appname`  
 必要項。 提供物件的應用程式的名稱。  
  
 `objectype`  
 必要項。 型別或物件的類別來建立。  
  
## <a name="remarks"></a>備註  
 `GetObject`函式不支援在[!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)]或更新版本。  
  
 使用`GetObject`函式可從檔案存取對 Automation 物件。 指定所傳回的物件`GetObject`給物件變數。 例如：  
  
```JavaScript  
var CADObject;  
CADObject = GetObject("C:\\CAD\\SCHEMA.CAD");  
```  
  
 此程式碼執行時，指定相關聯的應用程式`pathname`已啟動，且會啟動指定的檔案物件。 如果`pathname`為零長度字串 ("")，`GetObject`傳回指定之型別的新物件執行個體。 如果`pathname`省略引數，則`GetObject`傳回目前使用中的指定之型別的物件。 如果指定之類型的物件不存在，就會發生錯誤。  
  
 某些應用程式可讓您啟用檔案的組件。 若要這樣做，驚嘆號 （！） 的檔案名稱結尾加上遵循的字串來識別您想要啟用的檔案的一部分。 如需如何建立這個字串的資訊，請參閱 < 建立物件的應用程式的文件。  
  
 例如，在 繪圖應用程式中您可能至繪圖，儲存在檔案中的多個圖層。 您可以使用下列程式碼來啟動圖層內呼叫繪圖`SCHEMA.CAD`:  
  
```JavaScript  
var LayerObject = GetObject("C:\\CAD\\SCHEMA.CAD!Layer3");  
```  
  
 如果您未指定物件的類別，Automation 會決定要啟動的應用程式以及哪一個物件，若要啟用，根據您所提供的檔名。 不過，某些檔案，可能會支援多個物件類別。 例如，繪圖可能支援三種不同類型的物件： 應用程式物件、 繪圖物件和工具列物件，都是相同的檔案部分。 若要指定您要啟動的檔案中的物件，使用選擇性`class`引數。 例如：  
  
```JavaScript  
var MyObject;  
MyObject = GetObject("C:\\DRAWINGS\\SAMPLE.DRW", "FIGMENT.DRAWING");  
```  
  
 在上述範例中，`FIGMENT`繪圖應用程式的名稱和`DRAWING`是其中一個支援的物件類型。 啟動物件後，您在使用您所定義的物件變數的程式碼中參考它。 在上述範例中，存取新的物件使用的物件變數的屬性和方法`MyObject`。 例如：  
  
```JavaScript  
MyObject.Line(9, 90);  
MyObject.InsertText(9, 100, "Hello, world.");  
MyObject.SaveAs("C:\\DRAWINGS\\SAMPLE.DRW");  
```  
  
> [!NOTE]
>  使用`GetObject`函式物件的目前執行個體，或如果您想要建立的物件已經載入檔案時。 如果沒有目前的執行個體，而且您不想要開始使用該物件載入的檔案，請使用`ActiveXObject`物件。  
  
 如果物件已本身註冊為單一執行個體物件，只有一個執行個體物件的建立，不論如何多次`ActiveXObject`執行。 使用單一執行個體物件，`GetObject`一律會傳回相同的執行個體時呼叫零長度字串 ("") 的語法，而且如果會造成錯誤`pathname`省略引數。  
  
## <a name="requirements"></a>需求  
 支援文件模式如下： Quirks、 Internet Explorer 6 標準、 Internet Explorer 7 標準和 Internet Explorer 8 標準。 請參閱＜ [版本資訊](../../javascript/reference/javascript-version-information.md)＞。  
  
## <a name="see-also"></a>另請參閱  
 [ActiveXObject 物件](../../javascript/reference/activexobject-object-javascript.md)