---
title: IManagedAddin 介面
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ddede8542cda7499a9781c19a6baf1c58acfd125
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839540"
---
# <a name="imanagedaddin-interface"></a>IManagedAddin 介面
  實作 IManagedAddin 介面以建立元件，可將 managed VSTO 增益集。2007 Microsoft Office system 中已新增這個介面。  
  
## <a name="syntax"></a>語法  
  
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
 Microsoft Office 應用程式，開始使用 2007 Microsoft Office system 中，使用 IManagedAddin 介面協助載入 Office VSTO 增益集。您可以實作 IManagedAddin 介面以建立您自己的 VSTO 增益集載入器，而且執行階段針對 managed VSTO 增益集，而不是使用 VSTO 增益集載入器 (*VSTOLoader.dll*) 和[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 如需詳細資訊，請參閱 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)。  
  
## <a name="how-managed-add-ins-are-loaded"></a>如何載入受管理的增益集  
 當應用程式啟動時，會執行下列步驟：  
  
1. 應用程式會在下列登錄機碼底下尋找項目，以探索 VSTO 增益集：  
  
    **HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<應用程式名稱 >* \Addins\\**  
  
    這個登錄機碼下的每個項目都是 VSTO 增益集的唯一識別碼。 通常這會是 VSTO 增益集組件的名稱。  
  
2. 應用程式會在每個 VSTO 增益集的項目底下尋找 `Manifest` 項目。  
  
    受管理的 VSTO 增益集可以儲存的資訊清單的完整路徑`Manifest`下的項目**HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<應用程式名稱 >_ \Addins\\_\<增益集識別碼 >_**。 資訊清單是一種檔案 (通常是 XML 檔案)，可提供協助載入 VSTO 增益集的資訊。  
  
3. 如果應用程式找到 `Manifest` 項目，則會嘗試載入 Managed VSTO 增益集載入器元件。 應用程式會嘗試建立實作 IManagedAddin 介面的 COM 物件。  
  
    [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]包含 VSTO 增益集載入器元件 (*VSTOLoader.dll*)，或者您可以建立您自己的實作 IManagedAddin 介面。  
  
4. 應用程式會呼叫 [IManagedAddin::Load](../vsto/imanagedaddin-load.md) 方法，並傳入 `Manifest` 項目的值。  
  
5. [IManagedAddin::Load](../vsto/imanagedaddin-load.md) 方法會執行載入 VSTO 增益集所需的工作，例如設定要載入之 VSTO 增益集的應用程式定義域和安全性原則。  
  
   如需有關登錄 Microsoft Office 應用程式用來探索及載入的金鑰管理 VSTO 增益集，請參閱 < [VSTO 增益集的登錄項目](../vsto/registry-entries-for-vsto-add-ins.md)。  
  
## <a name="guidance-to-implement-imanagedaddin"></a>若要實作 IManagedAddin 的指引  
 如果您實作 IManagedAddin 時，您必須註冊包含實作，使用下列 CLSID 的 DLL:  
  
 99D651D7-5F7C-470E-8A3B-774D5D9536AC  
  
 Microsoft Office 應用程式會使用這個 CLSID 建立實作 IManagedAddin 的 COM 物件。  
  
> [!CAUTION]  
>  也會使用這個 CLSID *VSTOLoader.dll*在[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 因此，如果您使用 IManagedAddin 來建立您自己的 VSTO 增益集載入器和執行階段元件時，則無法部署您的元件會執行 VSTO 增益集依賴電腦[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [Unmanaged API 參考&#40;在 Visual Studio 中的 Office 程式開發&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  