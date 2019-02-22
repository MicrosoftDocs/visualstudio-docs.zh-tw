---
title: IRemoteDebugApplicationEx:ForceStepMode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:ForceStepMode
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:ForceStepMode
ms.assetid: 83e69a3e-e4c9-4ddd-b01b-1820e4177a03
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cb5c94c55709f5ecdbd6bae63ee3366f3dfeb2f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790850"
---
# <a name="iremotedebugapplicationexforcestepmode"></a>IRemoteDebugApplicationEx:ForceStepMode

會強制進入單一步驟模式偵錯工具。

## <a name="syntax"></a>語法

```cpp
HRESULT ForceStepMode(
   IRemoteDebugApplicationThread*  pStepThread
);
```

### <a name="parameters"></a>參數

`pStepThread`

[in]若要逐步處理序偵錯監視的執行緒。 如果是 null，PDM 會清除其逐步執行的執行緒。

## <a name="return-value"></a>傳回值

方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。

|值|描述|
|-----------|-----------------|
|`S_OK`|方法成功。|

## <a name="see-also"></a>另請參閱

- [IRemoteDebugApplicationEx 介面](iremotedebugapplicationex-interface.md)