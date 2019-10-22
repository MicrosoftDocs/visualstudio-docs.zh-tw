---
title: 識別碼的語句完成 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript], statement completion
- statement completion, JavaScript IntelliSense
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f5e52bf174e5a41d79fa23bfca39121db668e40e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643864"
---
# <a name="statement-completion-for-identifiers"></a>識別項的陳述式完成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript 不允許針對變數宣告進行明確類型的輸入。 因此，IntelliSense 不一定可以提供物件的完成清單。 在各種情況下可能會發生這種情況。 以下是幾個常見的範本。

- 已宣告參數，但尚未在使用中檔的其他位置呼叫它，如下列範例所示。

  ```javascript
  function illuminate(light) {
           light.  // Accurate statement completion is not available
                   // unless illuminate is called elsewhere with a
                   // parameter that has a value. If it is called only
                   // in a function that is a sibling to
                   // illuminate(light) in the call hierarchy, the
                   // IntelliSense engine also cannot determine the
                   // parameter type.
       }

  // Sibling function. No statement completion for light
  // object in preceding code.
  function lightLamp() {
      var x = illuminate(1);
  }

  // Uncomment the next line to obtain statement completion for
  // light object in preceding code.
  // var x = illuminate(1);
  ```

- 物件是在回應事件時呼叫的函式中。 在設計階段，IntelliSense 引擎無法判斷在此情況下使用的物件類型。

   如果 IntelliSense 引擎可以判斷應該呼叫事件，通常會透過使用作用中檔中的事件 `addEventListener`，提供更精確的 IntelliSense 資訊。

  當 IntelliSense 無法識別物件時，IntelliSense 引擎會在使用中檔中顯示的已命名實體（或識別碼）中填入完成清單。 當完成清單包含這些識別碼時，就會在其旁邊顯示資訊圖示。 此外，每個識別碼的工具提示會指出運算式是未知的。 下圖顯示類型為 `light` 的物件的語句完成選項，因為物件及其屬性未定義，所以無法識別。 不過，`intensity` 屬性可在 [識別碼] 清單中使用，因為它已在 `illuminate` 函式中使用。

  **無法識別之物件的完成選項**

  ![適用於識別碼的 JavaScript IntelliSense](../ide/media/js-intellisense-identifiers.png "|::ref1::|")

  您可以使用 XML 檔批註或 JavaScript IntelliSense 擴充性功能，覆寫物件的完成清單。 使用這些功能時，您可以在可能無法使用時，提供類型資訊和更具描述性的 IntelliSense 資訊。 如需詳細資訊，請參閱[擴充 JavaScript IntelliSense](../ide/extending-javascript-intellisense.md)和[建立 XML 檔批註](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)。

## <a name="see-also"></a>另請參閱
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)
