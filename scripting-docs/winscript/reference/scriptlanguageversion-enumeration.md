---
title: SCRIPTLANGUAGEVERSION 列舉 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4cee2966b326ca7b4c258ffdb85b6fa71d90992
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734068"
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