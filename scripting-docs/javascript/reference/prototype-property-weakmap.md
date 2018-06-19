---
title: prototype 屬性 (WeakMap) |Microsoft 文件
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
ms.assetid: d28b8a9b-38c9-443d-9586-7cc74784bd99
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cc1bff0d62f2aeb8d6fb78a0857f287fb34078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639248"
---
# <a name="prototype-property-weakmap"></a>prototype 屬性 (WeakMap)
傳回的原型參考`WeakMap`物件。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
weakmap.prototype  
```  
  
## <a name="remarks"></a>備註  
 `weakmap`引數是名稱`WeakMap`物件。  
  
 `prototype` 屬性可用來提供某類別物件的一組基本功能。 物件的新執行個體會「繼承」指派給該物件之原型的行為。  
  
 例如，若要將方法加入`WeakMap`傳回的最大項目值的物件`WeakMap`、 宣告函式、 將它加入至`WeakMap.prototype`，然後使用它。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]