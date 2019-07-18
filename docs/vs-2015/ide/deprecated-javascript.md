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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68177810"
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
 選擇性。 關於函式或方法的當地語系化資訊識別項。 該識別項會是成員識別碼，或對應由 OpenAjax 中繼資料所定義訊息包中的 `name` 屬性值。 識別項類型會依據在 [\<loc>](../ide/loc-javascript.md) 元素中指定的格式而有所不同。  
  
 `description`  
 選擇性。 函式或已被取代的方法的描述。  
  
## <a name="remarks"></a>備註  
 用來標註函式，其中包含的項目`<deprecated>`，必須放在任何陳述式之前的函式主體。 當您將函數標示為已被取代時，我們建議您取代其[\<摘要 >](../ide/summary-javascript.md)項目`<deprecated>`項目。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用 `<deprecated>` 元素。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)
