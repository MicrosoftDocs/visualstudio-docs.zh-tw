---
title: IDebugDocumentProvider 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d775deb153205d0e9a452775272285c67e74a210
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949860"
---
# <a name="idebugdocumentprovider-interface"></a>IDebugDocumentProvider 介面
提供方法，視需要來具現化文件。  
  
## <a name="remarks"></a>備註  
 此具現化文件的間接方式：  
  
- 允許將文件載入時需要它。  
  
- 可讓被包含在偵錯工具 IDE 的文件物件。  
  
- 可讓多個方式來存取相同的文件物件。  
  
  這實際上分隔從供應商的文件，並允許提供者執行其他執行階段內容資訊。  
  
  除了繼承自方法`IDebugDocumentInfo`，則`IDebugDocumentProvider`介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|會導致要具現化，如果不存在的文件。|