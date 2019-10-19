---
title: SCRIPTLANGUAGEVERSION 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 802a9f31cc7e3497c5e5fc54395d988552f75e84
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574369"
---
# <a name="scriptlanguageversion-enumeration"></a>SCRIPTLANGUAGEVERSION 列舉
指定可能的腳本版本。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>列舉值  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|預設版本。 整數值為0。|  
|SCRIPTLANGUAGEVERSION_5_7|Windows 腳本版本5.7。 整數值是1。|  
|SCRIPTLANGUAGEVERSION_5_8|Windows 腳本版本5.8。 整數值為2。|  
|SCRIPTLANGUAGEVERSION_MAX|最大版本。 整數值為255。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼的常數、列舉和錯誤碼](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)