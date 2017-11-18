---
title: "getVarDate 方法 （日期） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getVarDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- getVarDate method
- dates, VT_DATE format
ms.assetid: 561238de-5c91-45a3-b839-a16910d3a1cf
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d21394a5381653997a6b406537a6bde4f5266b97
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="getvardate-method-date-javascript"></a>getVarDate 方法 (日期) (JavaScript)
傳回 `Date` 物件中的 VT_DATE 值。  
  
> [!WARNING]
>  僅 Internet Explorer 支援此方法。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.getVarDate()   
```  
  
#### <a name="parameters"></a>參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## <a name="return-value"></a>傳回值  
 傳回 VT_DATE 值。  
  
## <a name="remarks"></a>備註  
 如果 JavaScript 程式碼與 COM 物件、ActiveX 物件或是接受和傳回 VT_DATE 格式之日期值的其他物件進行互動，則會使用 `getVarDate` 方法。 其中包括 Visual Basic 和 Visual Basic Scripting Edition (VBScript) 中的物件。 傳回值的實際格式取決於地區設定。  
  
## <a name="requirements"></a>需求  
 受下列文件模式支援：Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準和 Internet Explorer 10 標準。 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式不支援。 請參閱＜ [版本資訊](../../javascript/reference/javascript-version-information.md)＞。  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getDate 方法 （日期）](../../javascript/reference/getdate-method-date-javascript.md)   
 [Date.parse 函式](../../javascript/reference/date-parse-function-javascript.md)