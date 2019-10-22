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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf6016b2c12fd5ebe7cfb76c14c776508d99d2db
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651470"
---
# <a name="ltlocgt-javascript"></a>&lt;loc&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定提供當地語系化 IntelliSense 資訊之側車檔的位置和類型。

## <a name="syntax"></a>語法

```
<loc filename="filename"
    format="vsdoc|messagebundle" />
```

#### <a name="parameters"></a>參數
 `filename` 選擇項。 側車檔案的根名稱，其中包含中性文化特性的當地語系化資訊。 當 Visual Studio 搜尋當地語系化資訊時，它會嘗試尋找此檔案的特定文化特性版本。 例如，如果 `filename` 是 jquery，Visual Studio 會在與包含 `<loc>` 元素的 .js 檔案相同的位置中搜尋正確的文化特性特定資料夾（例如 JA-JP）。 如果找到特定文化特性的資料夾，它會檢查 jquery .xml 檔案是否存在於其中。 如果找不到正確的檔案，它會改為使用受控資源位置規則。 @No__t_0 的預設值是目前檔案的名稱，但副檔名為 .xml，而不是 .js。

 `format` 選擇項。 用於當地語系化的側車檔類型。 使用 `messagebundle` 來指定使用 Open Ajax 中繼資料所定義的訊息組合。 `messagebundle` 是建議的格式。 不過，Microsoft Ajax 或 winmd 檔案中不支援此格式。 使用 `vsdoc` 來指定 Microsoft Ajax 和 Windows 執行階段所使用的標準 .NET Framework 當地語系化格式。 這是一個選擇性的屬性。 `vsdoc` 是預設格式。

## <a name="remarks"></a>備註
 @No__t_0 元素必須出現在檔案頂端，與 `<reference>` 元素相同的區段中。 @No__t_0 元素的使用規則與 `<reference>` 元素相同。 如需詳細資訊，請參閱[JavaScript IntelliSense](../ide/javascript-intellisense.md)中的「參考指示詞」一節。

 Visual Studio 會處理每個 .js 檔案的單一 `<loc>` 元素。 如果有多個 `<loc>` 元素，則只會使用單一 `<loc>` 元素。 判斷要使用哪一個 `<loc>` 元素的行為未定義。

 使用訊息組合格式時，請使用 XML 檔批註中的 `locid` 屬性來指定 `name` 屬性值。

## <a name="example"></a>範例
 下列範例示範如何使用 messagebundle 格式的 `<loc>` 元素。 將下列 XML 新增至名為 messageFilename 的檔案，並將檔案放在正確的文化特性特定資料夾中，如 `filename` 參數的描述中所指定。

```
<?xml version="1.0" encoding="utf-8" ?>
<messagebundle>
  <msg name="1">A class that represents a rectangle</msg>
  <msg name="2">The height of a rectangle</msg>
  <msg name="3">The width of a rectangle</msg>
</messagebundle>

```

 針對 messagebundle 範例，請將下列程式碼新增至專案中的 JavaScript 檔案。 @No__t_0 元素必須顯示為 JavaScript 檔案中的第一行。 這段程式碼中的描述會由當地語系化的描述取代（如果有的話）。

```javascript
/// <loc filename="messageFilename.xml" format="messagebundle"/>

function doSomething(a,b)
{
    /// <summary locid='1'>description</summary>
    /// <param name='a' locid='2'>parameter a description</param>
    /// <param name='b' locid='3'>parameter b description</param>
}

```

 下列範例會使用 VSDoc 格式。 將下列 XML 新增至名為 scriptFilename 的檔案，並將檔案放在正確的特定文化特性資料夾中。

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

 針對 VSDoc 範例，請將下列程式碼新增至專案中的 JavaScript 檔案。 這段程式碼中的描述會由當地語系化的描述取代（如果有的話）。

```javascript
/// <loc filename="scriptFilename.xml" format="vsdoc" />

function illuminate(a)
{
    /// <summary locid='M:illuminate'>description</summary>
    /// <param name='a' type='Number'>parameter a description</param>
}

```

## <a name="see-also"></a>另請參閱
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)
