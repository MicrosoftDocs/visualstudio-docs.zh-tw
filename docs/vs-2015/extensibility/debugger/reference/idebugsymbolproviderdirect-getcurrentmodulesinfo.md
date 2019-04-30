---
title: IDebugSymbolProviderDirect::GetCurrentModulesInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetCurrentModulesInfo
- GetCurrentModulesInfo
ms.assetid: b3b45ed2-ea4e-4389-b78a-11fc9796a6c1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ce4473fca76424f3b737d530997f766da7b219d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62421911"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesinfo"></a>IDebugSymbolProviderDirect::GetCurrentModulesInfo
擷取符號群組中的模組的相關資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetCurrentModulesInfo(
   unsigned long * pCount,
   GUID *          ppGuids,
   DWORD *         pADIds,
   DWORD *         pCurrentState,
   IUnknown **     ppCDModItfs
);
```

```csharp
int GetCurrentModulesInfo(
   uint       pCount,
   Guid       ppGuids,
   uint       pADIds,
   uint       pCurrentState,
   out object ppCDModItfs
);
```

#### <a name="parameters"></a>參數
 `pCount`

 [in]中的模組數目`ppGuids`陣列。

 `ppGuids`

 [in]陣列，其中包含模組的唯一識別碼。

 `pADIds`

 [in]針對應用程式定義域的識別項。

 `pCurrentState`

 [in]目前的符號群組的狀態。

 `ppCDModItfs`

 [out]傳回物件，包含符號群組中的模組。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)