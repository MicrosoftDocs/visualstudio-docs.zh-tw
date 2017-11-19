---
title: "format 屬性 (Intl.NumberFormat) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 68c3223a-023c-4fa0-aa99-d049a7a0e26a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be40f8e94220ad7504dd3b9736e71b3416bb3d2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="format-property-intlnumberformat"></a>format 屬性 (Intl.NumberFormat)
傳回使用指定的數字格式器設定來格式化地區設定特定的數字的函數。  
  
## <a name="syntax"></a>語法  
  
```  
numberFormatObj.format  
```  
  
#### <a name="parameters"></a>參數  
 `numberFormatObj`  
 必要項。 名稱`NumberFormat`做為格式子物件。  
  
## <a name="remarks"></a>備註  
 所傳回的函式`format`屬性會接受單一引數， `value`，並傳回字串，表示當地語系化的數字，使用指定的選項`NumberFormat`物件。 如果`value`未提供，則函數會傳回`NaN`（不是數字）。  
  
## <a name="example"></a>範例  
 下列範例會使用`NumberFormat`物件建立當地語系化的數目。  
  
```JavaScript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
})  
  
if (console && console.log) {  
    console.log(nf.format(100)); // "¥100.00"  
}  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Intl.NumberFormat 物件](../../javascript/reference/intl-numberformat-object-javascript.md)