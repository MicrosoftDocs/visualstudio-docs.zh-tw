---
title: '&lt;loc&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <loc> JavaScript XML tag
- loc JavaScript XML tag
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8029dc6282e7b5a4ff9075257bcb1b6213a4a6b4
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54758521"
---
# <a name="ltlocgt-javascript"></a>&lt;loc&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定的位置和側車檔案提供 IntelliSense 的當地語系化的資訊類型。  
  
## <a name="syntax"></a>語法  
  
```  
<loc filename="filename"  
    format="vsdoc|messagebundle" />  
```  
  
#### <a name="parameters"></a>參數  
 `filename`  
 選擇性。 側車檔案，其中包含中性文化特性的當地語系化資訊的根名稱。 當 Visual Studio 搜尋當地語系化資訊時，它會嘗試尋找此檔案的特定文化特性的版本。 例如，如果`filename`是 jquery.xml，Visual Studio 中的.js 檔案，其中包含與相同的位置 （例如 JA) 正確特定文化特性資料夾搜尋`<loc>`項目。 如果它找到的特定文化特性資料夾時，它會檢查 jquery.xml 檔案是否存在中。 如果找不到正確的檔案，而是會使用受管理的資源位置的規則。 預設值為`filename`是目前的檔案，但其而不是.js 副檔名為.xml 的名稱。  
  
 `format`  
 選擇性。 用於當地語系化的側車檔案類型。 使用`messagebundle`指定開啟的 Ajax 中繼資料所定義的訊息組合使用。 `messagebundle` 是建議的格式。 不過，此格式不支援在 Microsoft Ajax 或.winmd 檔案中。 使用`vsdoc`以指定標準的.NET Framework 當地語系化格式，可由 Microsoft Ajax 和 Windows 執行階段。 這是一個選擇性的屬性。 `vsdoc` 是預設格式。  
  
## <a name="remarks"></a>備註  
 `<loc>`項目必須出現在相同的區段中的檔案頂端`<reference>`項目。 使用方式規則`<loc>`項目會與相同`<reference>`項目。 如需詳細資訊，請參閱中的 「 參考指示詞 」 一節[JavaScript IntelliSense](../ide/javascript-intellisense.md)。  
  
 Visual Studio 會處理單一`<loc>`的每個.js 檔案的項目。 如果有多個`<loc>`項目都存在，只會有一個`<loc>`使用項目。 用以判斷哪些行為`<loc>`未定義要使用的項目。  
  
 套件組合的訊息格式時，使用`locid`屬性中指定的 XML 文件註解`name`屬性值。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`<loc>`messagebundle 格式的項目。 名為 messageFilename.xml 檔案中加入下列 XML 程式碼，並將檔案放在正確的文化特性特定資料夾中的描述中所指定`filename`參數。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<messagebundle>  
  <msg name="1">A class that represents a rectangle</msg>  
  <msg name="2">The height of a rectangle</msg>  
  <msg name="3">The width of a rectangle</msg>  
</messagebundle>  
  
```  
  
 Messagebundle 範例中，請將下列程式碼加入您的專案中的 JavaScript 檔案。 `<loc>`項目必須顯示為 JavaScript 檔案中的第一行。 當地語系化的描述，會取代此程式碼中的說明，如果有的話。  
  
```javascript  
/// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
function doSomething(a,b)   
{  
    /// <summary locid='1'>description</summary>  
    /// <param name='a' locid='2'>parameter a description</param>  
    /// <param name='b' locid='3'>parameter b description</param>  
}  
  
```  
  
 下列範例會使用 VSDoc 格式。 名為 scriptFilename.xml 檔案中加入下列 XML 程式碼，並將檔案放在正確的文化特性特定資料夾中。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<doc>  
  <assembly>  
    <name>Lights</name>  
  </assembly>  
  <members>  
    <member name="M:illuminate">  
      <summary>Activates a light. </summary>  
      <param name='a'>The light to activate. </param>  
    </member>  
  </members>  
</doc>  
  
```  
  
 VSDoc 範例中，請將下列程式碼加入您的專案中的 JavaScript 檔案。 當地語系化的描述，會取代此程式碼中的說明，如果有的話。  
  
```javascript  
/// <loc filename="scriptFilename.xml" format="vsdoc" />  
  
function illuminate(a)   
{  
    /// <summary locid='M:illuminate'>description</summary>  
    /// <param name='a' type='Number'>parameter a description</param>  
}  
  
```  
  
## <a name="see-also"></a>請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)
