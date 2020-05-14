---
title: 支援使用者設定 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02bb2450196de76917e9cffc2f5f5acc6c8ee7b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704782"
---
# <a name="support-for-user-settings"></a>支援使用者設定
VSPackage 可以定義一個或多個設置類別,這些類別是當使用者在 **「工具**」功能表上選擇 **「導入/匯出設定」** 命令時仍然存在的狀態變數組。 要啟用此持久性,請使用[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]中的設置 API。

 稱為自訂設置點和 GUID 的註冊表項定義 VSPackage 的設置類別。 VSPackage 可以支援多個設置類別,每個類別由自定義設置點定義。

- 基於互通程式集(使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>介面)的設定的實現應透過編輯註冊表或使用註冊器腳本(.rgs 檔案)創建自訂設定點。 如需詳細資訊，請參閱 [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts)。

- 使用託管包框架 (MPF) 的代碼應透過每個自訂設定點<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>附加到 VS 套件來建立自訂設定點。

     如果單個 VSPackage 支援多個自定義設置點,則每個自定義設置點由單獨的類實現,並且每個設置點<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>都由 類的唯一實例註冊。 因此,實現類的設置可以支援多個設置類別。

## <a name="custom-settings-point-registry-entry-details"></a>自訂設定點註冊表項目詳細資訊
 自訂設定點在以下位置的註冊表項中建立:HKLM_Software_Microsoft_VisualStudio\\*\<版本>*[\\`<CSPName>`用戶設置`<CSPName>`], 其中是 VSPackage 支援的自定義設置點的名稱[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)],*\<版本>* 是的版本,例如 8.0。

> [!NOTE]
> 在初始化[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式開發環境 (IDE) 時\\,可以使用備用根覆蓋 HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft_VisualStudio*\<版本>* 的根路徑。 有關詳細資訊,請參閱[命令列開關](../../extensibility/command-line-switches-visual-studio-sdk.md)。

 註冊表項的結構如下圖所示:

 HKLM_軟體_微軟_VisualStudio\\*\<版本>[* 用戶設置]

 `<CSPName`>= #12345

 包 = 'XXXXXX XXXX XXXX XXXX XXXX XXXXXX]"

 類別 = "*YyyyyyYYYYYyyyyyyyyy}"

 資源包 = "_ZZZZ ZZ ZZ ZZ ZZZZZZZZZZZZZZZZZZZZZZ_zZZ__"

 備用父項目 = 類別名稱

| 名稱 | 類型 | 資料 | 描述 |
|-----------------|--------| - | - |
| (預設值) | REG_SZ | 自訂設定點的名稱 | 鍵的名稱`<CSPName`>是自定义设置点的未本地化名称。<br /><br /> 對於基於 MPF`categoryName`的實現,`objectName`<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>通過將建構函數的和參數`categoryName_objectName`合併到中獲取密鑰的名稱。<br /><br /> 密鑰可以是空的,也可以包含對附屬 DLL 中本地化字串的引用 ID。 此值從`objectNameResourceID`參數獲取<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>到 建構函數。 |
| Package | REG_SZ | GUID | 實現自訂設定點的 VS 包的 GUID。<br /><br /> 基於 MPF<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>使用 類別的使用建構函`objectType`數的參數包含 VSPackage 的<xref:System.Type>和反射以取得此值。 |
| 類別 | REG_SZ | GUID | 識別設置類別的 GUID。<br /><br /> 對於基於內部程式集的實現,此值可以是任意選擇的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]GUID,IDE 將 GUID<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A><xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>傳遞給和方法。 這兩種方法的所有實現都應驗證其 GUID 參數。<br /><br /> 對於基於 MPF 的實現,此<xref:System.Type>GUID 由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]實現設置機制的 類獲得。 |
| 資源包 | REG_SZ | GUID | 選擇性。<br /><br /> 如果實現 VSPackage 不提供本地化字串,則衛星 DLL 的路徑包含本地化字串。<br /><br /> MPF 使用反射來獲取正確的資源 VSPackage,因此<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>類不會設置此參數。 |
| 備用父級 | REG_SZ | 包含此自定義設定點的工具選項頁面下的資料夾的名稱。 | 選擇性。<br /><br /> 僅當設定實現支援**在**自動化模型中使用持久性[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]機制 而不是自動化模型中的機制來保存狀態的工具選項頁時,才必須設置此值。<br /><br /> 在這些情況下,"備用父"鍵中的值是用於標識特定`topic`**ToolsOptions**`topic.sub-topic`頁字串的部分。 例如,對於 **「工具選項」** 頁`"TextEditor.Basic"`,備用父項目`"TextEditor"`的值為 。<br /><br /> 生成<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>自定義設置點時,它與類別名稱相同。 |
