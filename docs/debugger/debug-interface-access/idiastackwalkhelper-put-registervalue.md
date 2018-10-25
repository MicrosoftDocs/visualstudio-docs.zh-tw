---
title: IDiaStackWalkHelper::put_registerValue |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81ac9c2366f97497fca4f7faa49facf2a3f819b9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49838929"
---
# <a name="idiastackwalkhelperputregistervalue"></a>IDiaStackWalkHelper::put_registerValue
設定暫存器值。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `index`  
 [in]值，以從[CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)指定將寫入暫存器的列舉類型。  
  
 `NewVal`  
 [in]新的暫存器值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 值的大小，儘管實作應該儲存只哪些暫存器通常會保留。 例如，8 位元暫存器會保存只有最低 8 位元的指定值。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)