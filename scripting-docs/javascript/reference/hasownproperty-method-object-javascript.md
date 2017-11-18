---
title: "hasOwnProperty 方法 (Object) (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: hasOwnProperty
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: hasOwnProperty method
ms.assetid: 3eb69d69-486f-4792-9518-4452aef369ca
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 397b68fc87bf730886c928e099037ff0183a7f63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="hasownproperty-method-object-javascript"></a>hasOwnProperty 方法 (Object) (JavaScript)
判斷物件是否具有指定名稱的屬性。  
  
## <a name="syntax"></a>語法  
  
```  
  
object.hasOwnProperty(proName)  
```  
  
## <a name="parameters"></a>參數  
 `object`  
 必要項。 物件的執行個體。  
  
 `proName`  
 必要項。 屬性名稱的字串值。  
  
## <a name="remarks"></a>備註  
 `hasOwnProperty`方法會傳回`true`如果`object`具有指定之名稱的屬性`false`如果不存在。 這個方法不會檢查物件的原型鏈結; 中的屬性屬性必須是物件本身的成員。  
  
 Internet Explorer 8 和其下主機物件不被支援這個屬性。  
  
## <a name="example"></a>範例  
 在下列範例中，所有`String`物件共用一般分割方法。 下列程式碼會顯示**false**和**true**。  
  
```JavaScript  
var s = new String("Sample");  
document.write(s.hasOwnProperty("split"));  
document.write("<br/>");  
document.write(String.prototype.hasOwnProperty("split"));  
  
// Output:  
// false  
// true  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [in 運算子](../../javascript/reference/in-operator-decrementjavascript.md)