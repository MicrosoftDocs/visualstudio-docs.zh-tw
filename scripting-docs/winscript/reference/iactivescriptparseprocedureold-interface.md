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
ms.openlocfilehash: 99fa06086bfad56b266b043716e82181aa4c97d5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160624"
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld 介面
可讓來源的程式碼文字，可以加入至指令碼的程序。 解譯的指令碼語言沒有獨立撰寫環境，例如 VBScript，這會提供替代機制 (而非`IActiveScriptParse`或`IPersist*`) 將命名空間中的指令碼程序。  
  
> [!NOTE]
>  此介面已被取代的益處`IActiveScriptParseProcedure`介面。  
  
## <a name="methods"></a>方法  
 除了繼承自方法`IUnknown`，則`IActiveScriptParseProcedureOld`介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|剖析指定的程式碼程序，並將命名空間中的程序。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)