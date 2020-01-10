---
title: 選項和選項頁面 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 963a73a3a8e079b2171c88e901913990892715cd
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981891"
---
# <a name="options-and-options-pages"></a>選項和選項頁
按一下 [**工具**] 功能表上的 [**選項**]，即可開啟 [**選項**] 對話方塊。 此對話方塊中的選項統稱為 [選項] 頁面。 流覽窗格中的樹狀目錄控制項包含選項分類，而每個類別都有選項頁。 當您選取頁面時，其選項會出現在右窗格中。 這些頁面可讓您變更決定 VSPackage 狀態的選項值。

## <a name="support-for-options-pages"></a>[選項] 頁面的支援
 <xref:Microsoft.VisualStudio.Shell.Package> 類別提供建立選項頁和選項分類的支援。 <xref:Microsoft.VisualStudio.Shell.DialogPage> 類別會實行 [選項] 頁面。

 <xref:Microsoft.VisualStudio.Shell.DialogPage> 的預設執行會在屬性的一般方格中，將其公用屬性提供給使用者。 您可以藉由覆寫頁面上的各種方法來自訂此行為，以建立具有自己的使用者介面（UI）的自訂 [選項] 頁面。 如需詳細資訊，請參閱[建立選項頁面](../../extensibility/creating-an-options-page.md)。

 <xref:Microsoft.VisualStudio.Shell.DialogPage> 類別會執行 <xref:Microsoft.VisualStudio.Shell.IProfileManager>，以提供選項頁面和使用者設定的持續性。 如果屬性可以在字串之間來回轉換，<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> 和 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> 方法的預設值就會將屬性變更保存到登錄的使用者區段中。

## <a name="options-page-registry-path"></a>選項頁登錄路徑
 根據預設，[選項] 頁面所管理之屬性的登錄路徑是藉由結合 [<xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>]、[DialogPage] 和 [選項] 頁面類別的類型名稱來決定。 例如，選項頁面類別可能定義如下。

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 如果 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> 是 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp，則屬性名稱和值組是 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral. 的子機碼。

 [選項] 頁面本身的登錄路徑是藉由結合 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>、單字、ToolsOptionsPages 和 [選項] 頁面類別目錄和名稱來決定。 例如，如果 [自訂選項] 頁面具有 [類別]、[我的選項] 頁面，而 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> 為 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp]，則 [選項] 頁面會有 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\ 的登錄機碼8.0 exp \ ToolsOptionsPages \ My Option Pages\Custom。

## <a name="toolsoptions-page-attributes-and-layout"></a>工具/選項頁面屬性和版面配置
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 屬性會在 [**選項**] 對話方塊的導覽樹狀目錄中，將 [自訂選項] 頁面的群組決定為 [分類]。 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 屬性會將選項頁面與提供介面的 VSPackage 產生關聯。 請考慮下列程式碼片段：

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 這會宣告 MyPackage 提供兩個選項頁面 OptionsPageGeneral 和 OptionsPageCustom。 在 [**選項**] 對話方塊中，兩個 [選項] 頁面會分別在 [**我的選項頁**] 類別目錄中顯示為**一般**和**自訂**。

## <a name="option-attributes-and-layout"></a>選項屬性和版面配置
 頁面提供的使用者介面（UI）會決定自訂選項頁面中選項的外觀。 [一般選項] 頁面中的 [配置]、[標記] 和 [描述] 是由下列屬性所決定：

- <xref:System.ComponentModel.CategoryAttribute> 決定選項的類別目錄。

- <xref:System.ComponentModel.DisplayNameAttribute> 決定選項的顯示名稱。

- <xref:System.ComponentModel.DescriptionAttribute> 決定選項的描述。

  > [!NOTE]
  > 對等屬性（SRCategory、LocDisplayName 和 SRDescription）會使用字串資源進行當地語系化，並在[managed 專案範例](/azure/devops/integrate/index)中定義。

  請考慮下列程式碼片段：

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  [選項] 頁面上的 [OptionInteger] 選項會顯示為 [**我的選項**] 分類中的 [整數]**選項**。 如果選取此選項，[描述] 方塊中會出現 [描述]、[**我的整數] 選項**。

## <a name="accessing-options-pages-from-another-vspackage"></a>存取其他 VSPackage 的選項頁面
 裝載和管理 [選項] 頁面的 VSPackage，可以使用 automation 模型，以程式設計方式從另一個 VSPackage 進行存取。 例如，在下列程式碼中，VSPackage 會註冊為裝載選項頁面。

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 下列程式碼片段會從 MyOptionPage 取得 OptionInteger 的值：

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 當 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 屬性註冊選項頁面時，如果 `true`屬性的 `SupportsAutomation` 引數，則會在 AutomationProperties 索引鍵下註冊此頁面。 自動化會檢查這個登錄專案以尋找相關聯的 VSPackage，然後自動化會透過 [裝載的選項] 頁面（在此案例中是我的格線頁）存取屬性。

 Automation 屬性的登錄路徑是藉由結合 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>、單字、AutomationProperties 和 [選項] 頁面分類和名稱來決定。 例如，如果 [選項] 頁面具有 [我的類別] 分類、[我的方格] 頁面名稱和 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp，則 automation 屬性會有登錄機碼 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My 格線頁。

> [!NOTE]
> [標準名稱] 的 [我的 Category.My 格線] 頁面是此索引鍵的 Name 子機碼值。