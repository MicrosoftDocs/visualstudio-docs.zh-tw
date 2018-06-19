---
title: VBArray 物件 (JavaScript) |Microsoft 文件
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
- VBArray
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- VBArray object constant
ms.assetid: f0b767f1-ea8a-4726-962b-2708d4742518
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b86e261a0cef445f1e0e0ecd651d5eb283cffce1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641618"
---
# <a name="vbarray-object-javascript"></a>VBArray 物件 (JavaScript)
提供 Visual Basic 安全陣列的存取。  
  
> [!WARNING]
>  僅 Internet Explorer 才支援此物件， [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式並不予支援。  
  
## <a name="syntax"></a>語法  
  
```  
  
varName = new VBArray(safeArray)   
```  
  
## <a name="parameters"></a>參數  
 `varName`  
 必要項。 要對其指派 VBArray 的變數名稱。  
  
 *safeArray*  
 必要項。 VBArray 值。  
  
## <a name="remarks"></a>備註  
 VBArray 是唯讀的，而且無法直接建立。 *safeArray* 引數必須取得 VBArray 值，才能傳遞至 VBArray 建構函式。 您只能從現有的 ActiveX 或其他物件中擷取此值，來達到這個目的。  
  
 VBArray 可以有多個維度。 每個維度的索引可能會不同。 **dimensions** 方法會擷取陣列中的維度數目； `lbound` 和 `ubound` 方法會擷取每個維度所使用的索引範圍。  
  
## <a name="example"></a>範例  
 下列範例由三個部分組成。 第一個部分是 VBScript 程式碼，用以建立 Visual Basic 安全陣列。 第二個部分是 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 程式碼，用以將 Visual Basic 安全陣列轉換成 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 陣列。 這兩個部分都會放\<h e a d > 一節的 HTML 網頁。 第三個部分是[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]程式碼是放在\<主體 > 區段以執行其他兩個部分。  
  
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
         document.writeln(k)  
         k = k + 1  
      Next  
      document.writeln("<br />")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vbarray){  
   var a = new VBArray(vbarray);  
   var b = a.toArray();  
   var i;  
   for (i = 0; i < 9; i++)   
   {  
      document.writeln(b[i]);  
   }  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
<!--  
   VBArrayTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## <a name="properties"></a>屬性  
 `VBArray` 物件沒有屬性。  
  
## <a name="methods"></a>方法  
 [dimensions 方法](../../javascript/reference/dimensions-method-vbarray-javascript.md)&#124;[getItem 方法](../../javascript/reference/getitem-method-vbarray-javascript.md)&#124;[lbound 方法](../../javascript/reference/lbound-method-vbarray-javascript.md)&#124;[toArray 方法](../../javascript/reference/toarray-method-vbarray-javascript.md)&#124;[ubound 方法](../../javascript/reference/ubound-method-vbarray-javascript.md)  
  
## <a name="requirements"></a>需求  
 受下列文件模式支援：Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準和 Internet Explorer 10 標準。 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式不支援。 請參閱＜ [版本資訊](../../javascript/reference/javascript-version-information.md)＞。  
  
## <a name="see-also"></a>另請參閱  
 [Array 物件](../../javascript/reference/array-object-javascript.md)