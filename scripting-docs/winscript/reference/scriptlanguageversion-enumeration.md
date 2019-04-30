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
ms.openlocfilehash: 6aab63989d1ae02f7c75fc9c20a14d59e8a05078
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840204"
---
# <a name="scriptlanguageversion-enumeration"></a>SCRIPTLANGUAGEVERSION 列舉
指定可能的指令碼版本。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>列舉值  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|預設的版本。 整數值為 0。|  
|SCRIPTLANGUAGEVERSION_5_7|Windows 指令碼 5.7 版。 整數值為 1。|  
|SCRIPTLANGUAGEVERSION_5_8|Windows 指令碼版本 5.8。 整數值為 2。|  
|SCRIPTLANGUAGEVERSION_MAX|最高的版本。 整數值為 255。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼的常數、列舉和錯誤碼](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)