---
title: '&lt;summary&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- summary JavaScript XML tag
- <summary> JavaScript XML tag
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 81d41918d61bbe95cfe19d2382535449a47deb8c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62431416"
---
# <a name="ltsummarygt-javascript"></a>&lt;summary&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定函式或方法的描述。  
  
## <a name="syntax"></a>語法  
  
```  
<summary locid="descriptionID">description  
</summary>  
```  
  
#### <a name="parameters"></a>參數  
 `locid`  
 選擇性。 關於函式或方法的當地語系化資訊識別項。 該識別項會是成員識別碼，或對應由 OpenAjax 中繼資料所定義訊息包中的 `name` 屬性值。 識別項類型會依據在 [\<loc>](../ide/loc-javascript.md) 元素中指定的格式而有所不同。  
  
 `description`  
 選擇性。 函式或方法的描述。  
  
## <a name="remarks"></a>備註  
 用於標註函式的元素 (包括 [\<summary>](../ide/summary-javascript.md)、[\<param>](../ide/param-javascript.md) 和 [\<returns>](../ide/returns-javascript.md)) 必須放在函式主體中的任何陳述式之前。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用 `<summary>` 元素。  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## <a name="see-also"></a>請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)
