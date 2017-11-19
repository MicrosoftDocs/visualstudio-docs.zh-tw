---
title: "getItem 方法 (VBArray) (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getItem
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getItem method
- Item property
ms.assetid: f62964ad-8b2f-4596-95d0-b20e587ecea5
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6457435d047f2780a19fa8ce26fc2bb86f7ae0e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="getitem-method-vbarray-javascript"></a>getItem 方法 (VBArray) (JavaScript)
傳回位於指定位置的項目。  
  
## <a name="syntax"></a>語法  
  
```  
  
safeArray.getItem(dimension1[, dimension2, ...], dimensionN)   
```  
  
## <a name="parameters"></a>參數  
 *safeArray*  
 必要項。 VBArray 物件。  
  
 *dimension1, ..., dimensionN*  
 指定 VBArray 中所需項目的正確位置。 *n* 等於 VBArray 中的維度數目。  
  
## <a name="example"></a>範例  
 下列範例由三個部分組成。 第一個部分的 VBScript 程式碼是用來建立 Visual Basic 安全陣列。 第二個部分的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 程式碼是用來逐一查看 Visual Basic 安全陣列，並列印出每個項目的內容。 這兩個部分都會放\<h e a d > 一節的 HTML 網頁。 第三個部分是[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]程式碼是放在\<主體 > 區段以執行其他兩個部分。  
  
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
         a(i, j) = k  
         document.writeln(k)  
         k = k + 1  
      Next  
      document.writeln("<BR>")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
<script type="text/javascript">  
<!--  
function GetItemTest(vbarray)  
{  
   var i, j;  
   var a = new VBArray(vbarray);  
   for (i = 0; i <= 2; i++)  
   {  
      for (j =0; j <= 2; j++)  
      {  
         document.writeln(a.getItem(i, j));  
      }  
   }  
}  
-->  
</script>  
</head>  
<body>  
<script type="text/javascript">  
<!--  
   GetItemTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## <a name="requirements"></a>需求  
 受下列文件模式支援：Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準和 Internet Explorer 10 標準。 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式不支援。 請參閱＜ [版本資訊](../../javascript/reference/javascript-version-information.md)＞。  
  
 **適用於**： [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [dimensions 方法 (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [lbound 方法 (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [toArray 方法 (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound 方法 (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)