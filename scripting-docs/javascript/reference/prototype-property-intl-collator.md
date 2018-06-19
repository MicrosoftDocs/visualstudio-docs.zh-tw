---
title: prototype 屬性 (Intl.Collator) |Microsoft 文件
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
ms.assetid: c1bbb523-fb55-4395-b357-34d91cf5bba0
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 696535afde8c497bc98fc2c81a03854d66add6f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639118"
---
# <a name="prototype-property-intlcollator"></a>prototype 屬性 (Intl.Collator)
自動分頁器傳回的原型參考。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
collator.prototype  
```  
  
## <a name="remarks"></a>備註  
 `collator`引數是自動分頁器名稱。  
  
 `prototype` 屬性可用來提供某類別物件的一組基本功能。 物件的新執行個體會「繼承」指派給該物件之原型的行為。  
  
 例如，若要將方法加入可傳回集合中最大項目值的 `Intl.Collator` 物件，請宣告函式，並將它加入 `Intl.Collator.prototype`，然後使用它。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]