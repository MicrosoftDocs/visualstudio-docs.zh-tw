---
title: "IDebugDocumentText 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugDocumentText interface
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9522d1075cd796fb69f6abbc42adc2706a817fed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttext-interface"></a>IDebugDocumentText 介面
提供存取純文字版的偵錯文件。 這個介面會使用下列慣例：  
  
-   字元位置和行號是以零為起始。  
  
-   字元位置代表字元位移。它們請勿代表位元組或文字的位移。 Win32，字元位置會是 Unicode 位移。  
  
 除了繼承自`IDebugDocument`、`IDebugDocumentText`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|傳回文件的屬性。|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|傳回文件中的行數和字元數。|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|傳回對應的一行之第一個字元的字元位置。|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|傳回指定的字元位置的行號，並選擇性地對應的行內的字元位移。|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|擷取字元和/或字元屬性，與字元位置範圍相關聯。|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|傳回對應至文件內容的字元位置範圍。|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|建立對應至提供的字元位置範圍的文件內容物件。|