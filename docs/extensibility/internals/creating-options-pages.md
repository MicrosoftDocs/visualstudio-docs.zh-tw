---
title: 建立選項頁 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 368efaa78a56723d4a72c482bea9ee739385127e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709156"
---
# <a name="create-options-pages"></a>建立選項頁
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在託管套件框架中,透過在 **「工具」** 選[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]單 下添加 **「選項**」頁來擴展 IDE 派生的<xref:Microsoft.VisualStudio.Shell.DialogPage>類。

 實現給定**工具選項**頁的<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>物件與 物件的特定 VS 包相關聯。

 因為當 IDE 顯示特定頁面時,環境會實例化實現特定**工具選項**頁的物件:

- **工具選項**頁應在其自己的物件上實現,而不是在實現 VSPackage 的物件上實現。

- 物件無法實現多個**工具選項**頁。

## <a name="register-as-a-tools-options-page-provider"></a>註冊為工具選項頁面提供者
 通過**工具選項**頁面支援使用者配置的 VSPackage**Tools Options**<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute><xref:Microsoft.VisualStudio.Shell.Package>通過應用應用於 實現的實例來指示提供這些工具選項頁的物件。

 對於實現**工具選項**頁<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute><xref:Microsoft.VisualStudio.Shell.DialogPage>的每個 派生類型,必須有一個實例。

 的每個<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>實體都使用實現 **「工具選項」** 頁的類型、包含用於識別**工具選項**頁的類別和子類別的字串以及將類型註冊為提供**工具選項**頁的資源資訊。

## <a name="persist-tools-options-page-state"></a>持久工具選項頁面狀態
 如果在啟用了自動化支援後註冊**了「工具選項」** 頁實現,則 IDE 將保留頁面的狀態以及所有其他**工具選項**頁。

 VSPackage 可以使用 管理自己的<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>持久性 。 只應使用一種或另一種持久性方法。

## <a name="implement-dialogpage-class"></a>實作對話頁類
 提供 VSPackage<xref:Microsoft.VisualStudio.Shell.DialogPage>以使用以下的繼承功能:

- 默認使用者介面視窗。

- 如果<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>應用於類,或者<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A>該 屬性`true`<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>設置為 應用於類的屬性,則可用的預設持久性機制。

- 自動化支援。

  使用<xref:Microsoft.VisualStudio.Shell.DialogPage>實現**工具選項**頁的物件的最低要求是添加公共屬性。

  如果類正確註冊為 **「工具選項」** 頁提供程式,則其公共屬性在 **「工具」** 選單的 **「選項**」部分以屬性網格的形式可用。

  所有這些預設功能都可以重寫。 例如,要創建更複雜的用戶介面,只需要重寫<xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>的 默認實現。

## <a name="example"></a>範例
 以下是選項頁面的簡單"Hello world"實現。 將以下代碼添加到由 Visual Studio 套件套件樣本建立的預設專案中,並選擇了 **「功能表命令」** 選項,這將充分展示選項頁面功能。

### <a name="description"></a>描述
 以下類定義一個最小的"Hello world"選項頁。 打開時,用戶可以在屬性網格中設置`HelloWorld`公共屬性。

### <a name="code"></a>程式碼
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]

### <a name="description"></a>描述
 將以下屬性應用於包類使選項頁在載入包時可用。 數位是類別和頁面的任意資源 ID,末尾的布林值指定頁面是否支援自動化。

### <a name="code"></a>程式碼
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]

### <a name="description"></a>描述
 以下事件處理程序顯示的結果,具體取決於選項頁中設置的屬性的值。 它使用<xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>該方法,結果顯式轉換為自定義選項頁類型,以訪問頁面公開的屬性。

 在包範本生成的專案中,從`MenuItemCallback`函數調用此函數以將其附加到添加到 **「工具」** 功能表的預設命令。

### <a name="code"></a>程式碼
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]

## <a name="see-also"></a>另請參閱
- [擴充使用者設定與選項](../../extensibility/extending-user-settings-and-options.md)
- [選項頁的自動化支援](../../extensibility/internals/automation-support-for-options-pages.md)
