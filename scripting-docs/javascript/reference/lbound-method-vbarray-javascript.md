---
title: lbound 方法 (VBArray) (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- lbound
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lbound method
ms.assetid: 30ff5e8a-8165-494b-bce8-0a562ec2eec3
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b01adf424d42e9d24512d15b03ede6079a3da186
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638198"
---
# <a name="lbound-method-vbarray-javascript"></a>lbound 方法 (VBArray) (JavaScript)
傳回指定維度之 VBArray 中使用的最低索引值。  
  
## <a name="syntax"></a>語法  
  
```  
  
safeArray.lbound(dimension)   
```  
  
## <a name="parameters"></a>參數  
 *safeArray*  
 必要項。 VBArray 物件。  
  
 `dimension`  
 選擇項。 需要下限索引時，則的 VBArray 的維度。 如果省略，`lbound` 的行為就如同傳遞 1 一般。  
  
## <a name="remarks"></a>備註  
 如果 VBArray 是空的，`lbound` 方法會傳回 undefined。 如果 `dimension` 大於 VBArray 中的維度數目或為負值，則此方法會產生「陣列索引超出範圍」的錯誤。  
  
## <a name="example"></a>範例  
 下列範例由三個部分組成。 第一個部分是 VBScript 程式碼，用以建立 Visual Basic 安全陣列。 第二個部分是[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]程式碼，判斷安全陣列中的維度數目和每個維度下限。 VBScript，而不是 Visual Basic 中建立安全的陣列，因為下限一律為零。 這兩個部分都會放\<h e a d > 一節的 HTML 網頁。 第三個部分是[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]程式碼是放在\<主體 > 區段以執行其他兩個部分。  
  
```JavaScript  
<head>  
<script type="text/vbscript">  
<!--  
Function CreateVBArray()  
   Dim i, j, k  
   Dim a(2, 2)  
   k = 1  
   For i = 0 To 2  
      For j = 0 To 2  
         a(j, i) = k  
         k = k + 1  
      Next  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vba){  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The lower bound of dimension ";  
      s += i + " is ";  
      s += a.lbound(i);  
      s += ".<br />";  
   }  
   return (s);  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
   document.write(VBArrayTest(CreateVBArray()));  
</script>  
</body>  
```  
  
## <a name="requirements"></a>需求  
 受下列文件模式支援：Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準和 Internet Explorer 10 標準。 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式不支援。 請參閱＜ [版本資訊](../../javascript/reference/javascript-version-information.md)＞。  
  
 **適用於**： [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [dimensions 方法 (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem 方法 (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [toArray 方法 (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound 方法 (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)