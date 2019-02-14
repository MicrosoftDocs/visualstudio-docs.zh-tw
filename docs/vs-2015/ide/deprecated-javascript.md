---
title: '&lt;已被取代&gt;(JavaScript) |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b93a2b4dcc541f32c16766da0dd9dd19a4fdfe0d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54759752"
---
# <a name="ltdeprecatedgt-javascript"></a>&lt;deprecated&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定取代函式或方法。  
  
## <a name="syntax"></a>語法  
  
```  
<deprecated  
    type="deprecate|remove"  
    locid="descriptionID">description  
</deprecated>  
```  
  
#### <a name="parameters"></a>參數  
 `type`  
 選擇性。 指定是否函式或方法將會移除在未來的版本中，或是否函式或方法已經移除，以及其使用可能會導致錯誤。 若要設定`deprecate`指定函式或方法，將在未來版本中移除。 若要設定`remove`來指定，函式或方法已經移除。  
  
 `locid`  
 選擇性。 如需函式或方法的當地語系化資訊識別項。 識別項是成員識別碼或其對應至`name`屬性 OpenAjax 中繼資料所定義的訊息組合中的值。 識別項型別取決於所指定的格式[ \<loc >](../ide/loc-javascript.md)項目。  
  
 `description`  
 選擇性。 函式或已被取代的方法的描述。  
  
## <a name="remarks"></a>備註  
 用來標註函式，其中包含的項目`<deprecated>`，必須放在任何陳述式之前的函式主體。 當您將函數標示為已被取代時，我們建議您取代其[\<摘要 >](../ide/summary-javascript.md)項目`<deprecated>`項目。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用`<deprecated>`項目。  
  
```javascript  
function areaFunction(radiusParam) {  
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## <a name="see-also"></a>請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)
