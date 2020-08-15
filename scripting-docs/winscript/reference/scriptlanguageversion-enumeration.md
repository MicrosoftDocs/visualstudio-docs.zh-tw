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
ms.openlocfilehash: 511bc3525480306e0fe3075231c1e55794f01e9e
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238682"
---
# <a name="scriptlanguageversion-enumeration"></a>SCRIPTLANGUAGEVERSION 列舉
指定可能的腳本版本。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>列舉值  
  
|值|腳本版本|  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|預設版本。 整數值為0。|  
|SCRIPTLANGUAGEVERSION_5_7|Windows 腳本版本5.7。 整數值是1。|  
|SCRIPTLANGUAGEVERSION_5_8|Windows 腳本版本5.8。 整數值為2。|  
|SCRIPTLANGUAGEVERSION_MAX|最大版本。 整數值為255。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼的常數、列舉和錯誤碼](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)