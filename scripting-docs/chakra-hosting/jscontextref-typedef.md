---
title: JsContextRef Typedef | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 8586bfcc-bb24-430d-a6f2-1a3b3e34ec2e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec1300717b59c3b901665b39ca0102988e83e853
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567728"
---
# <a name="jscontextref-typedef"></a>JsContextRef Typedef
指令碼內容的參考。  
  
## <a name="syntax"></a>語法  
  
```  
typedef JsRef JsContextRef;  
```  
  
## <a name="remarks"></a>備註  
 每個指令碼內容都含有自己的全域物件，該物件與其他指令碼內容中的全域物件不同。  
  
 許多 Chakra 裝載應用程式開發介面需要「使用中」指令碼內容，您可以使用 `JsSetCurrentContext` 來設定此內容。 需要設定目前內容的 Chakra 裝載應用程式開發介面，會在其文件中明確註明。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)