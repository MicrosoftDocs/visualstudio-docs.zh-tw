---
title: catch 方法 （承諾） |Microsoft 文件
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
ms.assetid: 55266f6a-db4d-4de8-857a-8bc7d35ed4b8
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 307e5b2a501b038542a602df4538523a3fc6eccd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633988"
---
# <a name="catch-method-promise"></a>catch 方法 (承諾)
可讓您指定要對拒絕承諾進行的工作。  
  
## <a name="syntax"></a>語法  
  
```  
  
promise.catch(onRejected)  
```  
  
#### <a name="parameters"></a>參數  
 `promise`  
 必要項。 Promise 物件  
  
 `onRejected`  
 必要項。 要在拒絕承諾時執行的錯誤處理常式函式。  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 在下列程式碼範例中，會在 5000 毫秒之後傳回逾時的第一個呼叫。 在這個程式碼中，會拒絕承諾，並執行錯誤處理常式函式。  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(reject, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    console.log("done!");  
}).catch(err => {  
    console.log("error!");  
})  
  
// Output (after five seconds):  
// error!  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]