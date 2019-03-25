---
title: IRemoteDebugApplicationEx:RevokeBreak | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:RevokeBreak
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:RevokeBreak
ms.assetid: 1f077860-0a39-4ec9-b676-ae0712819c7b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0992eb5637434ccdf0dbf4fa6e436c87ae3fdd6c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148174"
---
# <a name="iremotedebugapplicationexrevokebreak"></a>IRemoteDebugApplicationEx:RevokeBreak

撤銷 break 命令。

## <a name="syntax"></a>語法

```cpp
HRESULT RevokeBreak( );
```

### <a name="parameters"></a>參數

無。

## <a name="return-value"></a>傳回值

方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。

|值|描述|
|-----------|-----------------|
|`S_OK`|方法成功。|

## <a name="see-also"></a>另請參閱

- [IRemoteDebugApplicationEx 介面](iremotedebugapplicationex-interface.md)