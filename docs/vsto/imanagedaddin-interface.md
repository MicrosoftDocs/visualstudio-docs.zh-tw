---
title: IManagedAddin 介面
description: 執行 IManagedAddin 介面，以建立載入 managed VSTO 增益集的元件。
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 614cf7e8d0e682d894328fb764c6d64b855d2834
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469784"
---
# <a name="imanagedaddin-interface"></a>IManagedAddin 介面
  執行 IManagedAddin 介面，以建立載入 managed VSTO 增益集的元件。此介面已在 2007 Microsoft Office system 中加入。

## <a name="syntax"></a>Syntax

```csharp
[
    object,
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),
    pointer_default(unique),
    oleautomation
]
interface IManagedAddin : IUnknown
{
    HRESULT Load(
        [in] BSTR bstrManifestURL,
        [in] IDispatch *pdispApplication);
    HRESULT Unload();
};
```

## <a name="methods"></a>方法
 下表列出 IManagedAddin 介面所定義的方法。

|名稱|描述|
|----------|-----------------|
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|當 Microsoft Office 應用程式載入 Managed VSTO 增益集時呼叫。|
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|只在 Microsoft Office 應用程式卸載 Managed VSTO 增益集之前呼叫。|

## <a name="remarks"></a>備註
 從 2007 Microsoft Office system 開始，microsoft Office 應用程式會使用 IManagedAddin 介面來協助載入 Office VSTO 增益集。您可以執行 IManagedAddin 介面，為 managed VSTO 增益集建立您自己的 VSTO 增益集載入器和執行時間，而不是使用 VSTO 增益集載入器 (*VSTOLoader.dll*) 和 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 。 如需詳細資訊，請參閱 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)。

## <a name="how-managed-add-ins-are-loaded"></a>Managed 增益集的載入方式
 當應用程式啟動時，會執行下列步驟：

1. 應用程式會在下列登錄機碼底下尋找項目，以探索 VSTO 增益集：

    **HKEY_CURRENT_USER\Software\Microsoft\Office\\ *\<application name>* \Addins\\**

    這個登錄機碼下的每個項目都是 VSTO 增益集的唯一識別碼。 通常這會是 VSTO 增益集組件的名稱。

2. 應用程式會在每個 VSTO 增益集的項目底下尋找 `Manifest` 項目。

    Managed VSTO 增益集可以在 `Manifest` **HKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<application name>_ \Addins \\ _\<add-in ID>_** 下的專案中儲存資訊清單的完整路徑。 資訊清單是一種檔案 (通常是 XML 檔案)，可提供協助載入 VSTO 增益集的資訊。

3. 如果應用程式找到 `Manifest` 項目，則會嘗試載入 Managed VSTO 增益集載入器元件。 應用程式會藉由嘗試建立可執行 IManagedAddin 介面的 COM 物件來執行這項工作。

    [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]包含 (*VSTOLoader.dll*) 的 VSTO 增益集載入器元件，或者您可以藉由執行 IManagedAddin 介面來建立自己的增益集。

4. 應用程式會呼叫 [IManagedAddin::Load](../vsto/imanagedaddin-load.md) 方法，並傳入 `Manifest` 項目的值。

5. [IManagedAddin::Load](../vsto/imanagedaddin-load.md) 方法會執行載入 VSTO 增益集所需的工作，例如設定要載入之 VSTO 增益集的應用程式定義域和安全性原則。

   如需 Microsoft Office 應用程式用來探索及載入 managed VSTO 增益集之登錄機碼的詳細資訊，請參閱 [VSTO 增益集的登錄專案](../vsto/registry-entries-for-vsto-add-ins.md)。

## <a name="guidance-to-implement-imanagedaddin"></a>執行 IManagedAddin 的指導方針
 如果您執行 IManagedAddin，則必須使用下列 CLSID 來註冊包含執行的 DLL：

 99D651D7-5F7C-470E-8A3B-774D5D9536AC

 Microsoft Office 應用程式會使用此 CLSID 來建立可執行 IManagedAddin 的 COM 物件。

> [!CAUTION]
> 中的 *VSTOLoader.dll* 也會使用此 CLSID [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 。 因此，如果您使用 IManagedAddin 來建立您自己的 VSTO 增益集載入器和執行時間元件，則無法將元件部署到執行依賴之 VSTO 增益集的電腦 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 。

## <a name="see-also"></a>另請參閱
- [Visual Studio&#41;中 &#40;Office 開發的非受控 API 參考 ](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)
