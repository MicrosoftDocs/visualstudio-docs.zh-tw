---
title: HTML 標記方法 (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- link method [JavaScript]
- blink method [JavaScript]
- fontsize method [JavaScript]
- italics method [JavaScript]
- sup method [JavaScript]
- anchor method [JavaScript]
- fixed method [JavaScript]
- fontcolor method [JavaScript]
- bold method [JavaScript]
- small method [JavaScript]
- HTML Tag methods [JavaScript]
- sub method [JavaScript]
- big method [JavaScript]
ms.assetid: 50376223-be95-4aa4-9147-9e738a5d3cfa
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7639bc609d8e9b7e4b212fe67ae40f81487d708e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638648"
---
# <a name="html-tag-methods-javascript"></a>HTML 標記方法 (JavaScript)
您可以使用 HTML 標記方法將放在文字周圍的 HTML 項目`String`物件。  
  
## <a name="syntax"></a>語法  
 下表列出的語法以及每個 HTML 標記方法的描述。  
  
 中的語法，`string1`是`String`物件或常值。  
  
 標準的資料行會指出[World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/?LinkId=199553) HTML 4 的建議。 「 建議 」 表示 HTML 項目建議改用樣式表。  
  
|語法|方法描述|參數描述|標準|  
|------------|------------------------|---------------------------|--------------|  
|`string1`.anchor (`name`)|將放在文字周圍的名稱屬性的 HTML 錨點。|`name`參數是要放在名稱屬性的 HTML 錨定文字。||  
|`string1`.big()|將 HTML \<b i g > 標籤文字周圍。||建議您不要使用|  
|`string1`.blink()|將 HTML\<閃爍 > 標籤文字周圍。 \<閃爍 > 標記不支援在 Internet Explorer 中。||不在標準|  
|`string1`.bold()|將 HTML \<B > 標籤文字周圍。||建議您不要使用|  
|`string1`.fixed()|將 HTML \<TT > 標籤文字周圍。||建議您不要使用|  
|`string1`.fontcolor (`color`)|將 HTML\<字型 > 標記具有 COLOR 屬性文字周圍。|`color`參數是包含預先定義的名稱為色彩的十六進位值的字串值。 有效的預先定義的色彩的名稱取決於[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]裝載瀏覽器和它的版本。|已被取代|  
|`string1`.fontsize (`size`)|將 HTML\<字型 > 標記具有 SIZE 屬性文字周圍。|`size`參數是整數值，指定文字的大小。 有效的整數值取決於[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]裝載瀏覽器和它的版本。|已被取代|  
|`string1`.italics()|將 HTML\<我 > 標籤文字周圍。||建議您不要使用|  
|`string1`.link (`href`)|將具有 HREF 屬性，該文字周圍的 HTML 錨點。|`href`參數是要放入 HREF 屬性的 HTML 錨定文字。||  
|`string1`.small()|將 HTML\<小 > 標籤文字周圍。||建議您不要使用|  
|`string1`.strike()|將 HTML \<STRIKE > 標籤文字周圍。||已被取代|  
|`string1`.sub()|將 HTML \<SUB > 標籤文字周圍。|||  
|`string1`.sup()|將 HTML \<SUP > 標籤文字周圍。|||  
  
## <a name="remarks"></a>備註  
 不會執行檢查來判斷 HTML 標記是否已套用至字串。  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用 HTML 標記方法。  
  
```JavaScript  
// anchor method.  
var strVariable = "This is an anchor.";  
document.write(strVariable.anchor("Anchor1"));  
// Output: <A NAME="Anchor1">This is an anchor.</A>  
  
// big method.  
var strVariable = "This is a string.";  
document.write(strVariable.big());  
// Output: <BIG>This is a string.</BIG>  
  
//  blink method.  
var strVariable = "This is a string.";  
document.write(strVariable.blink());  
// Output: <BLINK>This is a string.</BLINK>  
  
//  bold method.  
var strVariable = "This is a string.";  
document.write(strVariable.bold());  
// Output: <B>This is a string.</B>  
  
//  fixed method.  
var strVariable = "This is a string.";  
document.write(strVariable.fixed());  
// Output: <TT>This is a string.</TT>  
  
//  fontcolor method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontcolor("red"));  
// Output: <FONT COLOR="red">This is a string.</FONT>  
  
//  fontsize method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontsize(-1));  
// Output: <FONT SIZE="-1">This is a string.</FONT>  
  
//  italics method  
var strVariable = "This is a string.";  
document.write(strVariable.italics());  
// Output: <I>This is a string.</I>  
  
//  link method.  
var strVariable = "This is a hyperlink.";  
document.write(strVariable.link("http://www.microsoft.com"));  
// Output: <A HREF="http://www.microsoft.com">This is a hyperlink.</A>  
  
//  small method.  
var strVariable = "This is a string.";  
document.write(strVariable.small());  
// Output: <SMALL>This is a string.</SMALL>  
  
//  strike method.  
var strVariable = "This is a string.";  
document.write(strVariable.strike());  
// Output: <STRIKE>This is a string.</STRIKE>  
  
//  sub method.  
var strVariable = "This is a string.";  
document.write(strVariable.sub());  
// Output: <SUB>This is a string.</SUB>  
  
//  sup method.  
var strVariable = "This is a string.";  
document.write(strVariable.sup());  
// Output: <SUP>This is a string.</SUP>  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**:[字串物件](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [String 物件](../../javascript/reference/string-object-javascript.md)