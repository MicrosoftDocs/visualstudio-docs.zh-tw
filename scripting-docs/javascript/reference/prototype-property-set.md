---
title: prototype 屬性 (Set) |Microsoft 文件
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
ms.assetid: a075d5a6-e502-4636-85fc-1af001b8ac35
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8265d182562aee55f870fff4c3d5cbadf21402ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638858"
---
# <a name="prototype-property-set"></a>prototype 屬性 (Set)
傳回集合的原型參考。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
set.prototype  
```  
  
## <a name="remarks"></a>備註  
 `set` 引數是集合的名稱。  
  
 `prototype` 屬性可用來提供某類別物件的一組基本功能。 物件的新執行個體會「繼承」指派給該物件之原型的行為。  
  
 例如，若要將方法加入可傳回集合中最大項目值的 `Set` 物件，請宣告函式，並將它加入 `Set.prototype`，然後使用它。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]