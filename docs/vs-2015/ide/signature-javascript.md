---
title: '&lt;signature &gt; （JavaScript） |Microsoft Docs'
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671121"
---
# <a name="ltsignaturegt-javascript"></a>&lt;signature &gt; （JavaScript）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

為函式或方法的一組相關元素，以提供多載函式的檔。

## <a name="syntax"></a>語法

```
<signature externalid="id" externalFile="filename"
    helpKeyword="keyword" locid="descriptionID">
</signature>
```

#### <a name="parameters"></a>參數
 `externalid` 選擇項。 如果 `vsdoc` [\<loc >](../ide/loc-javascript.md)元素的 `format` 屬性，這個屬性會指定用來尋找與簽章相關聯之 XML 程式碼的成員識別碼。 與 `locid` 屬性不同的是，這個屬性會指定應該載入成員中具有此識別碼的所有元素。 XML 程式碼中的任何相關聯描述資訊也會與簽章中指定的元素合併。 這可讓您在側車檔案中指定其他元素（例如 `<capability>`），而不需在原始程式檔中指定這些專案。 `externalid` 是選擇性屬性。

 `externalFile` 選擇項。 指定要在其中尋找 `externalid` 的檔案名。 如果沒有 `externalid` 存在，則會忽略這個屬性。 這是選擇性屬性。 預設值是目前檔案的名稱，但副檔名為 .xml，而不是 .js。 根據預設，當地語系化的受控資源查閱規則會用來尋找檔案。

 `helpKeyword` 選擇項。 F1 說明的關鍵字。

 `locid` 選擇項。 有關欄位的當地語系化資訊識別碼。 該識別項會是成員識別碼，或對應由 OpenAjax 中繼資料所定義訊息包中的 `name` 屬性值。 識別項類型會依據在 [\<loc>](../ide/loc-javascript.md) 標籤中指定的格式而有所不同。

## <a name="remarks"></a>備註
 針對 .js 檔案中的每個多載函式描述使用一個 `<signature>` 元素，或針對指定的每個外部成員識別碼使用一個 `<signature>` 元素。

 在任何語句之前，必須將 `<signature>` 元素放在函式主體中。 當您使用[\<summary >](../ide/summary-javascript.md)、 [\<param >](../ide/param-javascript.md)或[\<returns > 元素](../ide/returns-javascript.md)的元素時，請將其他元素放在 `<signature>` 區塊內。

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
