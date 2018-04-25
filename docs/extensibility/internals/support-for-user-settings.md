---
title: 支援使用者設定 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cf2ba79cc8bff57de1fd410f8a2780825d693181
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="support-for-user-settings"></a>支援使用者設定
VSPackage 可能會定義一或多個設定分類，也就是群組的保存在使用者選擇時的狀態變數**匯入/匯出設定**命令**工具**功能表。 若要啟用此持續性，您可以使用設定應用程式開發介面中[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]。  
  
 自訂設定點和 GUID 指的登錄項目定義 VSPackage 的 [設定] 類別。 VSPackage 可以支援多個設定分類，每個已定義的自訂設定點。  
  
-   實作的 interop 組件為基礎的設定 (使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>介面) 應該建立自訂設定點編輯登錄，或使用的登錄器指令碼 （.rgs 檔案）。 如需詳細資訊，請參閱[建立登錄器指令碼](/cpp/atl/creating-registrar-scripts)。  
  
-   使用 Managed Package Framework (MPF) 的程式碼應該建立自訂設定點附加<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>至每個自訂設定點的 VSPackage。  
  
     如果單一 VSPackage 支援數個自訂設定點，每個自訂設定點藉由個別的類別，而且每個已註冊的唯一執行個體<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>類別。 因此，實作類別設定可以支援多個設定分類。  
  
## <a name="custom-settings-point-registry-entry-details"></a>自訂設定點的登錄項目詳細資料  
 在下列位置的登錄項目建立自訂設定點： HKLM\Software\Microsoft\VisualStudio\\*\<版本 >* \UserSettings\\`<CSPName>`，其中`<CSPName>`是 VSPackage 支援的自訂設定點的名稱和*\<版本 >* 版本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，例如 8.0。  
  
> [!NOTE]
>  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio 的根路徑\\*\<版本 >* 會覆寫以替代根時[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)初始化。 如需詳細資訊，請參閱[命令列參數](../../extensibility/command-line-switches-visual-studio-sdk.md)。  
  
 登錄項目的結構如下所示：  
  
 HKLM\Software\Microsoft\VisualStudio\\*\<版本 >* \UserSettings\  
  
 `<CSPName`> = '#12345' s  
  
 封裝 = ' {XXXXXX XXXX XXXX XXXX XXXXXXXXX}'  
  
 類別目錄 = ' {YYYYYY YYYY YYYY YYYY YYYYYYYYY}'  
  
 ResourcePackage = ' {ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'  
  
 AlternateParent = 類別名稱  
  
|名稱|類型|資料|描述|  
|----------|----------|----------|-----------------|  
|(預設值)|REG_SZ|自訂設定點的名稱|索引鍵的名稱， `<CSPName`>，為自訂設定點的未當地語系化的名稱。<br /><br /> 結合 MPF 為基礎的實作，取得索引鍵的名稱`categoryName`和`objectName`引數的<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>建構函式到`categoryName_objectName`。<br /><br /> 索引鍵可以是空的或它可以包含在附屬 DLL 中的當地語系化字串的參考識別碼。 這個值取自`objectNameResourceID`引數<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>建構函式。|  
|Package|REG_SZ|GUID|VSPackage，實作自訂設定點的 GUID。<br /><br /> 實作會根據使用 MPF<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>類別，請使用建構函式的`objectType`包含 VSPackage 的引數<xref:System.Type>和反映來取得這個值。|  
|分類|REG_SZ|GUID|識別設定類別的 GUID。<br /><br /> Interop 組件為基礎的實作，這個值可以是任意選擇的 GUID，其中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 傳遞給<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>方法。 這兩種方法的所有實作都應該都確認其 GUID 引數。<br /><br /> 對於根據 MPF 實作，這個 GUID 藉由取得<xref:System.Type>類別實作的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]設定機制。|  
|ResourcePackage|REG_SZ|GUID|選擇性。<br /><br /> 如果實作 VSPackage 不會提供其附屬 DLL 包含路徑的當地語系化字串。<br /><br /> MPF 會使用反映來取得正確的資源 VSPackage，所以<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>類別並不會設定這個引數。|  
|AlternateParent|REG_SZ|包含此自訂設定點的工具選項頁面下的資料夾名稱。|選擇性。<br /><br /> 您必須將此值，只有當設定實作支援**工具選項**使用持續性機制中的頁面[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]而不是儲存狀態的 automation 模型中的機制。<br /><br /> 在這些情況下，AlternateParent 機碼中的值是`topic`區段`topic.sub-topic`字串用來識別特定**ToolsOptions**頁面。 例如，對於**ToolsOptions**頁面`"TextEditor.Basic"`AlternateParent 值會`"TextEditor"`。<br /><br /> 當<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>產生自訂設定點，它是類別名稱相同。|