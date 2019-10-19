---
title: IActiveScriptParseProcedureOld 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4558a0cab2aea9b56db2759bb80b1287cd33ce87
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571434"
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld 介面
允許將程式碼文字加入至腳本。 對於沒有獨立撰寫環境的已解讀指令碼語言（例如 VBScript），這會提供替代機制（除了 `IActiveScriptParse` 或 `IPersist*` 以外），以將腳本程式新增至命名空間。  
  
> [!NOTE]
> 這個介面已被取代，而改用 `IActiveScriptParseProcedure` 介面。  
  
## <a name="methods"></a>方法  
 除了繼承自 `IUnknown` 的方法之外，`IActiveScriptParseProcedureOld` 介面也會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|剖析指定的程式碼程式，並將程式新增至命名空間。|  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)