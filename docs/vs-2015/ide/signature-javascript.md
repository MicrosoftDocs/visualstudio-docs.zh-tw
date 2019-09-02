---
title: '&lt;簽章&gt;(JavaScript) |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <signature> JavaScript XML tag
- signature JavaScript XML tag
ms.assetid: 319138e7-cfbe-4b37-9643-2ddb7f9c63d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 02a4c36f3969ca0f9ef61e817afb82eb8247f041
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203490"
---
# <a name="ltsignaturegt-javascript"></a>&lt;簽章&gt;(JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

一組相關的項目函式或方法，以提供多載函式的文件的等級而定。  
  
## <a name="syntax"></a>語法  
  
```  
<signature externalid="id" externalFile="filename"  
    helpKeyword="keyword" locid="descriptionID">  
</signature>   
```  
  
#### <a name="parameters"></a>參數  
 `externalid`  
 選擇性。 如果`format`屬性[ \<loc >](../ide/loc-javascript.md)項目是`vsdoc`，這個屬性會指定識別碼用來找出與簽章相關聯的 XML 程式碼的成員。 不同於`locid`屬性，這個屬性指定應該載入成員具有此識別碼中的所有項目。 也會與簽章中指定的項目合併的 XML 程式碼中的任何相關聯的描述資訊。 這可讓您指定其他項目，例如`<capability>`，而不在原始程式檔中指定它們側車檔案中。 `externalid` 是選擇性的屬性。  
  
 `externalFile`  
 選擇性。 指定在其中尋找檔案的名稱`externalid`。 如果沒有，則會忽略這個屬性`externalid`存在。 這是選擇性的屬性。 預設值是檔案的副檔名為.xml，而不是檔案的.js 但目前的名稱。 根據預設，當地語系化的受管理的資源查閱規則用來找出檔案。  
  
 `helpKeyword`  
 選擇性。 F1 說明的關鍵字。  
  
 `locid`  
 選擇性。 如需欄位的當地語系化資訊識別項。 該識別項會是成員識別碼，或對應由 OpenAjax 中繼資料所定義訊息包中的 `name` 屬性值。 識別項類型會依據在 [\<loc>](../ide/loc-javascript.md) 標籤中指定的格式而有所不同。  
  
## <a name="remarks"></a>備註  
 使用其中一個`<signature>`項目，每個多載函式描述中的.js 檔案或使用下列其中一個`<signature>`指定每個外部成員識別碼的項目。  
  
 `<signature>`項目必須放在任何陳述式之前的函式主體。 使用時[\<摘要 >](../ide/summary-javascript.md)， [ \<param >](../ide/param-javascript.md)，或[\<傳回 >](../ide/returns-javascript.md)項目`<signature>`項目，將其他項目放`<signature>`區塊。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用 `<signature>` 元素。  
  
```javascript  
// Use of <signature> with externalid.  
// Requires use of the <loc> tag to identify the external functions.  
function illuminate(light) {  
    /// <signature externalid='M:Windows.Devices.Light.Illuminate()' />  
    /// <signature externalid='M:Windows.Devices.Light.Illuminate(System.Int32)'>  
    ///   <param name='light' type='Number' />  
    /// </signature>  
}  
  
// Use of <signature> for overloads implemented in JavaScript.  
function add(a, b) {  
    /// <signature>  
    /// <summary>function summary 1</summary>  
    /// <param name="a" type="Number">The first number</param>  
    /// <param name="b" type="Number">The second number</param>  
    /// <returns type="Number" />  
    /// </signature>  
    /// <signature>  
    /// <summary>function summary 2 – differ by number of params</summary>  
    /// <param name="a" type="Number">Only 1 parameter</param>  
    /// <returns type="Number" />  
    /// </signature>  
    /// <signature>  
    /// <summary>function summary 3 – differ by parameter type</summary>  
    /// <param name="a" type="Number">Number parameter</param>  
    /// <param name="b" type="String">String parameter</param>  
    /// <returns type="Number" />  
    /// </signature>  
    /// <signature>  
    /// <summary>function summary 4 – differ by return type</summary>  
    /// <param name="a" type="Number">The first number</param>  
    /// <param name="b" type="Number">The second number</param>  
    /// <returns type="String" />  
    /// </signature>  
  
    return a + b;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)
