---
title: 特殊字元 (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- line terminator character
- white space character
- Unicode character
- escape sequence
- backslash (\)
ms.assetid: 3b38b1bd-1f0f-4748-b13e-55cab36fd126
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0eaae8dfc84d9a3be6db54c50558d4cf675a53a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569628"
---
# <a name="special-characters-javascript"></a>特殊字元 (JavaScript)
您可以在字串中放入 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 提供的逸出序列 (Escape Sequence)，用來建立無法直接輸入的字元。  
  
## <a name="remarks"></a>備註  
 字串值是一串零或多個 Unicode 字元 (字母、數字和其他字元)。 字串常值是以成對的單引號或雙引號括住。 雙引號可以包含在以單引號括住的字串中。 單引號可以包含在以雙引號括住的字串中。  
  
 字串常值中的每個字元都可以透過逸出序列來代表。 逸出序列的開頭為反斜線 (\\)，通知 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 解譯器下一個字元是特殊字元。  
  
 您可以使用 \u*hhhh* 逸出序列來指定 Unicode 字元，其中 *hhhh* 是四位數的十六進位數字。 Unicode 逸出序列可以代表任何 16 位元字元。 如需詳細資訊，請參閱 [Unicode 字碼指標逸出序列](#CodePoint)。  
  
 您可以使用單一字元逸出序列代表某些字元。 例如，\t 指定定位字元。  
  
## <a name="escape-sequences"></a>逸出序列  
 下表列出常用字元之逸出序列的一些範例。  
  
|Unicode 字元值|逸出序列|意義|分類|  
|-----------------------------|---------------------|-------------|--------------|  
|\u0008|\b|退格鍵||  
|\u0009|\t|索引標籤|空白字元|  
|\u000A|\n|換行字元 (新行)|行結束字元|  
|\u000B|\v<br /><br /> (請參閱這個表格後面的附註。)|垂直 Tab|空白字元|  
|\u000C|\f|換頁字元|空白字元|  
|\u000D|\r|歸位字元|行結束字元|  
|\u0020||空格|空白字元|  
|\u0022|\\"|雙引號 (")||  
|\u0027|\\'|單引號 (')||  
|\u005C|\\\|反斜線 (\\)||  
|\u00A0||不中斷空格|空白字元|  
|\u2028||行分隔符號|行結束字元|  
|\u2029||段落分隔符號|行結束字元|  
|\uFEFF||位元組順序符號|空白字元|  
  
 [類別] 資料行指定字元是空白字元還是行結束字元。 [trim 方法 (字串)](../../javascript/reference/trim-method-string-javascript.md) 移除字串前後的空白字元以及行結束字元。  
  
 反斜線本身做為逸出字元。 因此，您無法在指令碼中直接輸入該符號。 如果您想要撰寫一個反斜線，則必須同時鍵入兩個 (\\\\)。  
  
> [!NOTE]
>  從 [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] 開始，測試垂直 Tab (\v) 與 "v" 是否相等，無法將瀏覽器識別為 Internet Explorer。 在舊版本中，運算式 `"\v" === "v"` 會傳回 `true`。 在 [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] 中，運算式會傳回 `false`。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>說明  
 下列範例示範 \\\ 和 \\' 逸出序列。  
  
### <a name="code"></a>程式碼  
  
```JavaScript  
document.write('The image path is C:\\webstuff\\mypage\\gifs\\garden.gif.');  
document.write ("<br />");  
document.write('The caption reads, "After the snow of \'97. Grandma\'s house is covered."');  
```  
  
<a name="CodePoint"></a>   
## <a name="unicode-code-point-escape-sequences"></a>Unicode 字碼指標逸出序列  
 在 [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] 中，完全支援 Unicode。 最常見的 Unicode 字碼指標是由四個十六進位數字代表 (例如 /u0009 代表 Tab 字元)。 Astral 字碼指標包含所有需要四個以上十六進位數字的符號，現在也支援簡化格式。 使用格式 "\u{*codepoint*}"，完整 Unicode 字元集可以使用常值格式表示。 例如，若要呈現符號 "𠮷"，您可以使用下列格式："\u{20BB7}"。  
  
 在下列程式碼範例中，字串都是相等的。 (\uD842\uDFB7 是在舊版中指定這個符號的因應措施)。  
  
```JavaScript  
"\u{20BB7}"=="𠮷"=="\uD842\uDFB7"  
```  
  
 RegExp 現在包含 /u 旗標來啟用 astral 字碼指標的完整支援。 例如，在下列程式碼範例中，規則運算式中的 /u 旗標會啟用相符的 astral 字碼指標 (句號符合所提供字串中的任何字元)。  
  
```JavaScript  
"𠮷".match(/./u)[0].length == 2  
```  
  
 /u 旗標會將新的格式 \u{codepoint}) 剖析為 Unicode 逸出序列。 這是必要作業，因為沒有 /u 旗標的 \u{xxxxx} 在規則運算式中有不同的意義。  
  
> [!NOTE]
>  在 astral 字碼指標中，長度一律為 2。 這符合舊版的行為。  
  
 String 物件現在包含兩個新方法 (String.codePointAt 和 String.fromCodePoint) 以支援 astral 字碼指標。 例如，您可以使用 codePointAt 傳回 "𠮷" 符號的對等字碼指標。  
  
```JavaScript  
"𠮷".codePointAt(0) == 0x20BB7  
  
```  
  
 您也可以使用 `for...of` 陳述式反覆執行字碼指標。  
  
```JavaScript  
for(var c of "𠮷") {  
    console.log(c);  
}  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [String.fromCharCode 函式](../../javascript/reference/string-fromcharcode-function-javascript.md)