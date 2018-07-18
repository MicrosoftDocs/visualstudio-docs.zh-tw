---
title: IActiveScriptParseProcedureOld 介面 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 99cff9cd4d04c5d25489b6cc4c9b9af93792dc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724418"
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld 介面
可讓來源的程式碼文字加入指令碼的程序。 解譯的指令碼語言沒有獨立撰寫環境，例如 VBScript，這會提供替代機制 (以外`IActiveScriptParse`或`IPersist*`) 將指令碼程序新增至命名空間。  
  
> [!NOTE]
>  此介面已被取代之喜好`IActiveScriptParseProcedure`介面。  
  
## <a name="methods"></a>方法  
 除了繼承自`IUnknown`、`IActiveScriptParseProcedureOld`介面會公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|剖析指定的程式碼的程序，並將程式新增到命名空間。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)