---
title: dimensions 方法 (VBArray) (JavaScript) |Microsoft 文件
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
- dimensions
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dimensions method
- VBArray object constant
ms.assetid: ac83589e-85d9-48cb-b28d-c579e65fd604
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9896a5beced00614a825b1921b6046b0ac8a396a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636918"
---
# <a name="dimensions-method-vbarray-javascript"></a>dimensions 方法 (VBArray) (JavaScript)
傳回 VBArray 的維度數目。  
  
## <a name="syntax"></a>語法  
  
```  
  
array.dimensions( )   
```  
  
## <a name="remarks"></a>備註  
 必要的 *array* 是 VBArray 物件。  
  
## <a name="example"></a>範例  
 **dimensions** 方法能夠擷取指定之 VBArray 的維度數目。  
  
 下列範例由三個部分組成。 第一個部分是 VBScript 程式碼，用以建立 Visual Basic 安全陣列。 第二個部分的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 程式碼是用來決定安全陣列中的維度數目以及每個維度的上限。 這兩個部分都會放\<h e a d > 一節的 HTML 網頁。 第三個部分是[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]程式碼是放在\<主體 > 區段以執行其他兩個部分。  
  
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
function VBArrayTest(vba)  
{  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The upper bound of dimension ";  
      s += i + " is ";  
      s += a.ubound(i);  
      s += ".<br />";  
   }  
   return(s);  
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
 [getItem 方法 (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [lbound 方法 (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [toArray 方法 (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound 方法 (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)