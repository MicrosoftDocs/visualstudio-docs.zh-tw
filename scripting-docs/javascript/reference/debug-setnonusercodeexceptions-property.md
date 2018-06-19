---
title: Debug.setNonUserCodeExceptions 屬性 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1dd2abee-a415-41bb-a359-017da62f9485
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f53084d5580bc7b6b6c6356268dc60f519b2bd6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636158"
---
# <a name="debugsetnonusercodeexceptions-property"></a>Debug.setNonUserCodeExceptions 屬性
判斷是否要為使用者未處理偵錯工具來處理此領域中的任何 try catch 區塊。 可以歸類為擲回，使用者未處理或未處理的例外狀況。  
  
 如果這個屬性設定為`true`在給定範圍中，偵錯工具可以然後決定要採取某些動作 （例如，中斷） 如果開發人員想要在使用者未處理的例外狀況中斷，該範圍內擲回的例外狀況。 如果這個屬性設定為`false`會與相同永遠不會設定的屬性。  
  
 如需有關偵錯的詳細資訊，請參閱[動態指令碼偵錯概觀](http://go.microsoft.com/fwlink/p/?LinkId=249469)。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.setNonUserCodeExceptions [= bool];  
```  
  
## <a name="example"></a>範例  
 下列程式碼將示範如何設定這個屬性。  
  
```JavaScript  
(function () {  
    Debug.setNonUserCodeExceptions = true;  
    try{  
        var x = null;  
        x.y();  
    } catch (e) {  
    // Catch the exception.  
    }  
})();  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]