---
title: fill 方法 （陣列） (JavaScript) |Microsoft 文件
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
ms.assetid: 11526627-c0bb-4157-a8c4-0a039079b4a1
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4546bafb3fa3a8c242b8b7ef4ef2863ea86bf179
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636468"
---
# <a name="fill-method-array-javascript"></a>fill 方法 (陣列) (JavaScript)
以指定的值填入陣列。  
  
## <a name="syntax"></a>語法  
  
```  
arrayObj.fill(value [ , start [ , end ] ]);  
```  
  
#### <a name="parameters"></a>參數  
 `arrayObj`  
 必要項。 陣列物件。  
  
 `value`  
 必要項。 用來填入陣列的值。  
  
 `start`  
 選擇項。 用來填入陣列值的起始索引。 預設值為 0。  
  
 `end`  
 選擇項。 用來填入陣列值的結束索引。 預設值是 `this` 物件的長度屬性。  
  
## <a name="remarks"></a>備註  
 如果`start`是負數，`start`會被視為`length` + `start`，其中`length`是陣列的長度。 如果`end`是負數，`end`會被視為`length` + `end`。  
  
## <a name="example"></a>範例  
 下列程式碼範例填入有值的陣列。  
  
```JavaScript  
[0, 0, 0].fill(7, 1);  
// Array contains [0,7,7]  
  
[0, 0, 0].fill(7);  
// Array contains [7,7,7]  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]