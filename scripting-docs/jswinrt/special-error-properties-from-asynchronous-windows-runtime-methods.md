---
title: 來自非同步 Windows 執行階段方法的特殊錯誤屬性 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45155584-06d8-4e7f-93a6-8564a93f643d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 120d8f699c8bedd0fe5762300203c5d5ec18e73e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24571408"
---
# <a name="special-error-properties-from-asynchronous-windows-runtime-methods"></a>來自非同步 Windows 執行階段方法的特殊錯誤屬性
可能很難針對 JavaScript 中的非同步 Windows 執行階段方法進行偵錯，因為可能會從呼叫堆疊深層擲回錯誤。 應用程式以偵錯模式執行時，JavaScript `Error` 物件有些額外屬性只會出現在從非同步 Windows 執行階段方法擲回錯誤時。  
  
## <a name="special-error-properties"></a>特殊錯誤屬性  
 在偵錯模式中，因失敗 Windows 執行階段非同步作業而導致的錯誤物件具有下列特殊屬性：  
  
-   `asyncOpSource` (物件) 取得進行已產生錯誤之呼叫的原始位置資訊。 屬性 `asyncOpSource.originatingCall` (字串) 顯示使用者程式碼中產生非同步作業的位置。  
  
-   asyncOpType (字串) 取得引發錯誤之非同步作業類型的名稱。  
  
 如需非同步作業錯誤的詳細資訊，請參閱：  
  
-   [如何使用 Promise 處理錯誤 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/hh700337.aspx)  
  
-   [為 Windows 執行階段錯誤進行疑難排解](http://msdn.microsoft.com/en-us/1ef7d7df-82ac-441d-8ad0-54ab1318de64)