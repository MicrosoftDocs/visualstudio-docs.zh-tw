---
title: "資料屬性與存取子屬性 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7e132831-375d-4728-9a57-5c6f91075b1c
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b800131ba76aa432492c0caefdbb9e8d5291924
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="data-properties-and-accessor-properties"></a>資料屬性與存取子屬性
本節包含您可能需要的資料屬性與存取子屬性的所有資訊。  
  
### <a name="data-properties"></a>資料屬性  
 「資料屬性」是可取得和設定值的屬性。 資料屬性會在其描述項中包含 `value` 和 `writable` 屬性。  
  
 下表列出資料屬性描述項的屬性。  
  
|資料描述項屬性|描述|預設|  
|-------------------------------|-----------------|-------------|  
|`value`|屬性的目前值。|`undefined`|  
|`writable`|`true` 或 `false`。 如果 `writable` 設定為 `true`，則可以修改屬性值。|`false`|  
|`enumerable`|`true` 或 `false`。 如果 `enumerable` 設定為 `true`，則可以透過 `for...in` 陳述式列舉屬性。|`false`|  
|`configurable`|`true` 或 `false`。 如果 `configurable` 設定為 `true`，則可以變更屬性的屬性 (property attribute)，以及刪除屬性。|`false`|  
  
 如果描述項沒有 `value`、`writable`、`get` 或 `set` 屬性，而且指定的屬性名稱不存在，則會新增資料屬性。  
  
 `configurable` 屬性為 `false` 且 `writable` 為 `true` 時，可以變更 `value` 和 `writable` 屬性。  
  
#### <a name="data-properties-added-without-using-defineproperty"></a>在未使用 defineProperty 的情況下新增資料屬性  
 如果您在未使用 `Object.defineProperty`、`Object.defineProperties` 或 `Object.create` 函式的情況下新增資料屬性，則 `writable`、`enumerable` 和 `configurable` 屬性都會設定為 `true`。 新增屬性之後，即可使用 `Object.defineProperty` 函式進行修改。  
  
 您可以使用下列方式來新增資料屬性：  
  
-   指派運算子 (=)，如 `obj.color = "white";`  
  
-   物件常值，如 `obj = { color: "white", height: 5 };`  
  
-   建構函式，如[使用建構函式定義類型](../../javascript/advanced/using-constructors-to-define-types.md)中所述  
  
### <a name="accessor-properties"></a>存取子屬性  
 每次設定或擷取屬性值時，「存取子屬性」都會呼叫使用者提供的函式。 存取子屬性的描述項包含 `get` 屬性和 (或) `set` 屬性。  
  
 下表列出存取子屬性描述項的屬性。  
  
|存取子描述項屬性|描述|預設|  
|-----------------------------------|-----------------|-------------|  
|`get`|傳回屬性值的函式。 函式沒有任何參數。|`undefined`|  
|`set`|設定屬性值的函式。 它的一個參數包含要指派的值。|`undefined`|  
|`enumerable`|`true` 或 `false`。 如果 `enumerable` 設定為 `true`，則可以透過 `for...in` 陳述式列舉屬性。|`false`|  
|`configurable`|`true` 或 `false`。 如果 `configurable` 設定為 `true`，則可以變更屬性的屬性 (property attribute)，以及刪除屬性。|`false`|  
  
 如果未定義 `get` 存取子，並嘗試存取屬性值，則會傳回值 `undefined`。 如果未定義 `set` 存取子，並嘗試將值指派給存取子屬性，則不會發生任何狀況。  
  
### <a name="property-modifications"></a>屬性修改  
 如果物件已有所指定名稱的屬性，則會修改屬性的屬性 (property attribute)。 當您修改屬性 (property) 時，描述項中未指定的屬性 (attribute) 會保持不變。  
  
 如果現有屬性 (property) 的 `configurable` 屬性 (attribute) 是 `false`，則唯一允許的修改是將 `writable` 屬性 (attribute) 從 `true` 變更為 `false`。  
  
 您可以將資料屬性變更為存取子屬性，反之亦然。 如果您這麼做，會在屬性 (property) 中保留描述項中未指定的 `configurable` 和 `enumerable` 屬性 (attribute)。 描述項中未指定的其他屬性會設定為其預設值。  
  
 您可以使用多個 `Object.defineProperty` 函式呼叫，以累加方式定義可設定的存取子屬性。 例如，一個 `Object.defineProperty` 呼叫可能只會定義一個 `get` 存取子。 對相同屬性名稱的稍後呼叫可能會定義 `set` 存取子。 屬性接著會有 `get` 存取子和 `set` 存取子。  
  
 若要取得套用至現有屬性的描述項物件，您可以使用 [Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
 您可以使用 [Object.seal 函式](../../javascript/reference/object-seal-function-javascript.md)和 [Object.freeze 函式](../../javascript/reference/object-freeze-function-javascript.md)，保留對屬性之屬性 (property attribute) 的修改。