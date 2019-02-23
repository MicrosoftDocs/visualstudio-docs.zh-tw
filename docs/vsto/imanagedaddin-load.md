---
title: IManagedAddin::Load
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 87fb34e90d36383f49b6369fb1dea4b9854c7300
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56604003"
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  載入 Managed VSTO 增益集時呼叫。

## <a name="syntax"></a>語法

```csharp
HRESULT Load([in] BSTR bstrManifestURL,
             [in] IDispatch *pdispApplication);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*bstrManifestURL*|VSTO 增益集之資訊清單的完整路徑。|
|*pdispApplication*|代表載入 VSTO 增益集主應用程式的 IDispatch 指標。|

## <a name="return-value"></a>傳回值
 HRESULT 值，表示此方法是否已順利完成。

## <a name="remarks"></a>備註
 資訊清單是一種檔案 (通常是 XML 檔案)，可提供協助載入 VSTO 增益集的資訊。 例如，資訊清單可以指定 VSTO 增益集組件的位置，以及載入 VSTO 增益集時要具現化的進入點類別。

 *BstrManifestURL*參數中包含的值`Manifest`底下的項目**HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<應用程式名稱>_ \Addins\\_\<增益集識別碼 >_**  VSTO 增益集的登錄機碼。 如需詳細資訊，請參閱 < [IManagedAddin 介面](../vsto/imanagedaddin-interface.md)。

 實作 [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) 方法可針對所要載入之 VSTO 增益集執行工作，例如設定增益集的應用程式定義域和安全性原則。

## <a name="see-also"></a>另請參閱
- [IManagedAddin 介面](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
