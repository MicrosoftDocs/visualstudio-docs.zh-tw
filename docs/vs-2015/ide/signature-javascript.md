---
title: '&lt;&gt; (JavaScript) 的簽章 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <signature> JavaScript XML tag
- signature JavaScript XML tag
ms.assetid: 319138e7-cfbe-4b37-9643-2ddb7f9c63d4
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4c640c28ada16a8a03943fcd1362d4fd521772c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671121"
---
# <a name="ltsignaturegt-javascript"></a>&lt;&gt; (JavaScript) 的簽章
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

針對函式或方法的一組相關元素進行分組，以提供多載函式的檔。

## <a name="syntax"></a>語法

```
<signature externalid="id" externalFile="filename"
    helpKeyword="keyword" locid="descriptionID">
</signature>
```

#### <a name="parameters"></a>參數
 `externalid` 選擇項。 如果 `format` 元素的屬性 [\<loc>](../ide/loc-javascript.md) 為，則 `vsdoc` 這個屬性會指定用來尋找與簽章相關聯之 XML 程式碼的成員識別碼。 與屬性不同的是 `locid` ，這個屬性會指定成員中必須載入具有此識別碼的所有元素。 存在於 XML 程式碼中的任何相關描述資訊，也會與簽章中指定的元素合併。 這可讓您在側車檔中指定其他元素（例如 `<capability>` ），而不在原始程式檔中指定它們。 `externalid` 是選擇性屬性。

 `externalFile` 選擇項。 指定要在其中尋找的檔案名 `externalid` 。 如果不存在，則會忽略這個屬性 `externalid` 。 這是選擇性屬性。 預設值是目前檔案的名稱，但副檔名為 .xml，而不是 .js。 根據預設，當地語系化的 managed 資源查閱規則會用來尋找檔案。

 `helpKeyword` 選擇項。 F1 說明的關鍵字。

 `locid` 選擇項。 有關欄位之當地語系化資訊的識別碼。 該識別項會是成員識別碼，或對應由 OpenAjax 中繼資料所定義訊息包中的 `name` 屬性值。 識別碼類型取決於在標記中指定的格式 [\<loc>](../ide/loc-javascript.md) 。

## <a name="remarks"></a>備註
 針對 .js 檔案中的每個多載函式描述使用一個專案 `<signature>` ，或 `<signature>` 針對指定的每個外部成員識別碼使用一個元素。

 專案 `<signature>` 必須放在函數主體中的任何語句之前。 使用、或專案搭配專案時 [\<summary>](../ide/summary-javascript.md) [\<param>](../ide/param-javascript.md) ，請 [\<returns>](../ide/returns-javascript.md) `<signature>` 將其他元素放在區塊內 `<signature>` 。

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
 [XML 檔批註](../ide/xml-documentation-comments-javascript.md)
