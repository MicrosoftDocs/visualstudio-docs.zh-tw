---
title: 支援使用者設定 |Microsoft Docs
description: 瞭解如何使用 Visual Studio SDK 中的設定 Api 來啟用設定類別的持續性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 06cd22ec933e72344ab743372fe30c1a3ddf5fbf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901586"
---
# <a name="support-for-user-settings"></a>支援使用者設定
VSPackage 可定義一或多個設定類別，這是當使用者選擇 [**工具**] 功能表上的 [匯 **入/匯出設定**] 命令時保存的狀態變數群組。 若要啟用此持續性，您可以在中使用設定 Api [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 。

 稱為自訂設定點的登錄專案，以及 GUID 定義了 VSPackage 的設定類別。 VSPackage 可以支援多個設定類別，每個都是由自訂設定點所定義。

- 以 interop 元件為基礎的設定的執行 (使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 介面) 應該藉由編輯登錄或使用註冊機構腳本 ( .rgs 檔) 來建立自訂設定點。 如需詳細資訊，請參閱 [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts)。

- 使用受管理套件架構 (MPF) 的程式碼應該藉由 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 將 VSPackage 附加至每個自訂設定點的方式，來建立自訂設定點。

     如果單一 VSPackage 支援數個自訂設定點，每個自訂設定點都是由個別的類別來執行，而每個都是由類別的唯一實例所註冊 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 。 因此，設定實類別可支援一個以上的設定類別。

## <a name="custom-settings-point-registry-entry-details"></a>自訂設定點登錄專案詳細資料
 自訂設定點會建立在下列位置的登錄專案中： HKLM\Software\Microsoft\VisualStudio \\ *\<Version>* \UserSettings \\ `<CSPName>` ，其中 `<CSPName>` 是 VSPackage 支援的自訂設定點名稱，而 *\<Version>* 則是的版本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，例如8.0。

> [!NOTE]
> \\ *\<Version>* 當 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 初始化整合式開發環境 (IDE) 時，可使用替代根目錄覆寫 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio的根路徑。 如需詳細資訊，請參閱 [命令列參數](../../extensibility/command-line-switches-visual-studio-sdk.md)。

 登錄專案的結構如下所示：

 HKLM\Software\Microsoft\VisualStudio \\ *\<Version>* \UserSettings\

 `<CSPName`>= s ' #12345 '

 Package = ' {XXXXXX XXXX xxxx xxxx XXXXXXXXX} '

 Category = ' {YYYYYY YYYY YYYY YYYY YYYYYYYYY} '

 ResourcePackage = ' {ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ} '

 AlternateParent = 類別名稱

| 名稱 | 類型 | 資料 | 描述 |
|-----------------|--------| - | - |
| (預設值) | REG_SZ | 自訂設定點的名稱 | 金鑰的名稱 `<CSPName`> 是自訂設定點的未當地語系化名稱。<br /><br /> 若是以 MPF 為基礎的實作為基礎，則會藉由將函式的 `categoryName` 和 `objectName` 引數合併為來取得索引鍵的名稱 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> `categoryName_objectName` 。<br /><br /> 索引鍵可以是空的，也可以在附屬 DLL 中包含當地語系化字串的參考識別碼。 這個值是從函式的 `objectNameResourceID` 引數取得的 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 。 |
| 套件 | REG_SZ | GUID | 執行自訂設定點之 VSPackage 的 GUID。<br /><br /> 以使用類別的 MPF 為基礎的 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 實作為基礎，使用 `objectType` 包含 VSPackage 和反映的函式引數， <xref:System.Type> 以取得此值。 |
| 類別 | REG_SZ | GUID | 識別設定類別的 GUID。<br /><br /> 針對以 interop 元件為基礎的實值，此值可以是任意選擇的 GUID，IDE 會將它 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 傳遞至 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 方法。 這兩個方法的所有執行都應該驗證其 GUID 引數。<br /><br /> 針對以 MPF 為基礎的執行，此 GUID 是由實 <xref:System.Type> 設定機制的類別所取得 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 |
| ResourcePackage | REG_SZ | GUID | 選擇性。<br /><br /> 如果實 VSPackage 未提供，則為包含當地語系化字串之附屬 DLL 的路徑。<br /><br /> MPF 使用反映來取得正確的資源 VSPackage，因此 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 類別不會設定此引數。 |
| AlternateParent | REG_SZ | 包含此自訂設定點的 [工具選項] 頁面下的資料夾名稱。 | 選擇性。<br /><br /> 只有在設定實支援在中使用持續性機制的 [ **工具選項** ] 頁面， [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 而不是 automation 模型中的機制來儲存狀態時，才必須設定這個值。<br /><br /> 在這些情況下，AlternateParent 索引鍵中的值是 `topic` `topic.sub-topic` 用來識別特定 **ToolsOptions** 頁面的字串區段。 例如，針對 **ToolsOptions** 頁面， `"TextEditor.Basic"` AlternateParent 的值會是 `"TextEditor"` 。<br /><br /> 當 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 產生自訂設定點時，它會與類別目錄名稱相同。 |
