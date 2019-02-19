---
title: 識別項的陳述式完成 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript], statement completion
- statement completion, JavaScript IntelliSense
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 89f507c2f4d01cf5e3e1e983cfcb5bafd9d9a7dd
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54787648"
---
# <a name="statement-completion-for-identifiers"></a>識別項的陳述式完成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript 不允許明確輸入的變數宣告。 如此一來，IntelliSense 一律無法提供的完成清單的物件。 在各種情況下，這可能會發生。 以下是一些常見的。  
  
- 已宣告參數，但它尚未呼叫其他地方使用中文件，如下列範例所示。  
  
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
  
- 物件是在呼叫以回應事件的函式。 在設計階段 IntelliSense 引擎無法判斷在此情況下使用之物件的型別。  
  
   如果 IntelliSense 引擎可以判斷此事件應該呼叫，通常透過使用`addEventListener`主動式文件中的事件，提供更精確的 IntelliSense 資訊。  
  
  當 IntelliSense 無法識別的物件時，IntelliSense 引擎就會填入與具名的實體或識別項，在於使用中文件的完成清單。 當完成清單包含這些識別項時，旁邊會出現資訊圖示。 此外，每個識別項的工具提示會指出運算式是未知。 下圖顯示陳述式的型別物件的 [完成] 選項`light`，不能因為是未定義的物件和其屬性識別。 不過，`intensity`屬性是識別項清單中，因為它已用於`illuminate`函式。  
  
  **無法識別的物件的 [完成] 選項**  
  
  ![識別項的 JavaScript IntelliSense](../ide/media/js-intellisense-identifiers.png "js_intellisense_identifiers")  
  
  您可以使用 XML 文件註解或 JavaScript IntelliSense 擴充性功能，以覆寫物件的完成清單。 使用這些功能，您可以提供類型資訊和更具描述性的 IntelliSense 資訊時，它可能否則無法使用。 如需詳細資訊，請參閱 <<c0> [ 擴充 JavaScript IntelliSense](../ide/extending-javascript-intellisense.md)並[建立的 XML 文件註解](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)。  
  
## <a name="see-also"></a>請參閱  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)
