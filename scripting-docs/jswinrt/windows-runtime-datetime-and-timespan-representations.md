---
title: Windows 執行階段 DateTime 和 TimeSpan 的表示 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime dates and times
- TimeSpan [JavaScript]
- DateTime [JavaScript]
ms.assetid: 9743e9ac-9054-463e-8264-427183e4905f
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d7c394b57eb0215e3dff857d935b367e602c2b0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24571418"
---
# <a name="windows-runtime-datetime-and-timespan-representations"></a>Windows 執行階段 DateTime 和 TimeSpan 的表示
日期和時間的 JavaScript 表示與 Windows 執行階段版本不同。 Windows 執行階段的 [DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx) 結構在 JavaScript 中表示為 [Date](../javascript/reference/date-object-javascript.md)，它有符合 `DateTime` 資料的備份存放區 (且具有不同於 JavaScript `Date` 的範圍和精確度)。 如果您修改這個自訂 `Date` 物件，它會變成標準 JavaScript `Date` 並會失去精確度。 JavaScript `Date` 值可以傳遞至 Windows 執行階段 `DateTime`，且會進行範圍檢查，這可能會造成封送處理例外狀況。  
  
 Windows 執行階段 [TimeSpan](http://msdn.microsoft.com/en-us/c5defb66-819c-4796-85b5-07ed249a5d86) 結構會轉換為毫秒並傳回為 JavaScript 數字。  
  
## <a name="see-also"></a>另請參閱  
 [在 JavaScript 中使用 Windows 執行階段](../jswinrt/using-the-windows-runtime-in-javascript.md)