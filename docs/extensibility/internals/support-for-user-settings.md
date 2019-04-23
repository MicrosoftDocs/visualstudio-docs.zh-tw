---
title: 支援使用者設定 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f7fbb6c8e6a6310b736ade599ad7854bc4255c0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60070736"
---
# <a name="support-for-user-settings"></a>支援使用者設定
VSPackage 可能會定義一或多個設定類別，也就是當使用者選擇保存的狀態變數群組**匯入/匯出設定**命令**工具**功能表。 若要啟用此持續性，您可以使用 Api 設定中[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]。

 自訂設定點和 GUID 指的登錄項目定義 VSPackage 的 [設定] 類別。 VSPackage 可以支援多個設定分類，每個已定義的自訂設定點。

- 實作的 interop 組件為基礎的設定 (使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>介面) 應該藉由編輯登錄，或使用登錄器指令碼 （.rgs 檔案） 建立自訂設定點。 如需詳細資訊，請參閱 [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts)。

- 使用 Managed Package Framework (MPF) 的程式碼應該連結以建立自訂設定點<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>每個自訂設定點的 vspackage。

     如果單一 VSPackage 支援數個自訂設定點，每個自訂設定點藉由個別的類別，而且每個已註冊的唯一執行個體<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>類別。 因此，實作類別的設定可以支援多個設定分類。

## <a name="custom-settings-point-registry-entry-details"></a>自訂設定點的登錄項目詳細資料
 在下列位置的登錄項目中建立自訂設定點：HKLM\Software\Microsoft\VisualStudio\\*\<版本 >* \UserSettings\\`<CSPName>`，其中`<CSPName>`是 VSPackage 支援的自訂設定點名稱並*\<版本 >* 是新版[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，例如 8.0。

> [!NOTE]
>  Hkey_local_machine\software\microsoft\visualstudio \ 的根路徑\\*\<版本 >* 可以覆寫以替代 root 時[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是整合式的開發環境 (IDE)初始化。 如需詳細資訊，請參閱 <<c0> [ 命令列參數](../../extensibility/command-line-switches-visual-studio-sdk.md)。

 登錄項目結構如下所示：

 HKLM\Software\Microsoft\VisualStudio\\*\<Version>* \UserSettings\

 `<CSPName`>= s '#12345'

 封裝 = ' {XXXXXX XXXX XXXX XXXX XXXXXXXXX}'

 Category = '{YYYYYY YYYY YYYY YYYY YYYYYYYYY}'

 ResourcePackage = '{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'

 AlternateParent = CategoryName

| 名稱 | 類型 | 資料 | 描述 |
|-----------------|--------| - | - |
| (預設值) | REG_SZ | 自訂設定點的名稱 | 索引鍵的名稱， `<CSPName`>，為自訂設定點的未當地語系化的名稱。<br /><br /> 結合的 MPF 所根據的實作，取得索引鍵的名稱`categoryName`並`objectName`的引數<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>建構函式到`categoryName_objectName`。<br /><br /> 金鑰可以是空的或它可以包含在附屬 DLL 中的當地語系化字串的參考識別碼。 這個值取自`objectNameResourceID`引數<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>建構函式。 |
| 套件 | REG_SZ | GUID | VSPackage 實作自訂設定點的 GUID。<br /><br /> 實作會根據使用 MPF<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>類別中，使用的建構函式`objectType`引數包含 VSPackage 的<xref:System.Type>和反映來取得這個值。 |
| 分類 | REG_SZ | GUID | 用來識別設定類別的 GUID。<br /><br /> Interop 組件為基礎的實作，這個值可以是任意選擇的 GUID，其中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 會將傳遞給<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>而<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>方法。 所有的這兩種方法的實作應該先確認其 GUID 引數。<br /><br /> 對於根據 MPF 實作，來取得此 GUID<xref:System.Type>類別實作的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]設定機制。 |
| ResourcePackage | REG_SZ | GUID | 選擇性。<br /><br /> 通往附屬 DLL 包含當地語系化字串，如果實作 VSPackage 未提供它們。<br /><br /> MPF 會使用反映以取得正確的資源 VSPackage，因此<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>類別不會設定這個引數。 |
| AlternateParent | REG_SZ | 包含此自訂設定點的 [工具選項] 頁面下的資料夾名稱。 | 選擇性。<br /><br /> 您必須將此值，只有支援的設定實作**工具選項**使用持續性機制中的頁面[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]而不是儲存狀態的 automation 模型中的機制。<br /><br /> 在這些情況下，AlternateParent 機碼中的值是`topic`一節`topic.sub-topic`用來識別特定的字串**ToolsOptions**頁面。 例如，對於**ToolsOptions**頁`"TextEditor.Basic"`AlternateParent 的值會是`"TextEditor"`。<br /><br /> 當<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>產生自訂設定點，它是類別名稱相同。 |
