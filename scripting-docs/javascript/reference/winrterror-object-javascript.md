---
title: "WinRTError 物件 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- WinRTError object [JavaScript]
- JavaScript, WinRTError object
ms.assetid: d75ab8e5-e729-4d86-90fd-ea228c30dd66
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11b339b4fc3c4bd4f34416ffd98b8f9c3f288f98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="winrterror-object-javascript"></a>WinRTError 物件 (JavaScript)
Windows 執行階段呼叫傳回指出失敗的 HRESULT 時，JavaScript 會將它轉換為特殊 Windows 執行階段錯誤。 這僅適用於 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式 (Windows 執行階段可用時)，做為全域 JavaScript 命名空間的一部分。  
  
## <a name="syntax"></a>語法  
  
```  
  
errorObj = new WinRTError();  
  
```  
  
## <a name="remarks"></a>備註  
 WinRTError 錯誤類型僅用於源自 Windows 執行階段 API 的錯誤。.  
  
## <a name="example"></a>範例  
 下列範例顯示如何擲回和攔截 WinRTError。  
  
```JavaScript  
try {  
            Windows.Storage.ApplicationData.localFolder.createFileAsync("sample.txt");  
        } catch (err) {  
            var n = err;  
        }  
  
```  
  
## <a name="methods"></a>方法  
 WinRTError 物件沒有方法。  
  
## <a name="properties"></a>屬性  
 WinRTError 物件具有相同的內容[物件時發生錯誤](../../javascript/reference/error-object-javascript.md)物件。  
  
## <a name="requirements"></a>需求  
 僅 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式才支援 WinRTError 物件，Internet Explorer 並不予支援。  
  
## <a name="see-also"></a>另請參閱  
 [Error 物件](../../javascript/reference/error-object-javascript.md)