---
title: "IDebugDocumentProvider 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 262794718e238068cfd9a8e3fae5161b9fe8cc54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentprovider-interface"></a>IDebugDocumentProvider 介面
提供方法來具現化視文件。  
  
## <a name="remarks"></a>備註  
 文件具現化這個間接方式：  
  
-   允許在需要時載入文件。  
  
-   可讓偵錯工具 IDE 內包含的文件物件。  
  
-   可讓多個方式來存取相同的文件物件。  
  
 這實際上分隔從供應商的文件，並允許提供者執行其他執行階段內容資訊。  
  
 除了繼承自`IDebugDocumentInfo`、`IDebugDocumentProvider`介面會公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|會導致要具現化，如果不存在的文件。|