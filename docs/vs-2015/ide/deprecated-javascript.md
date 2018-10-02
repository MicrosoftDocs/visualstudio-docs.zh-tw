---
title: '&lt;已被取代&gt;(JavaScript) |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9d62067b8bd888c40a8cbc0f67d209760d487cf5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497508"
---
# <a name="ltdeprecatedgt-javascript"></a>&lt;已被取代&gt;(JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[Visual Studio 2017 文件](https://docs.microsoft.com/en-us/visualstudio/)。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)



