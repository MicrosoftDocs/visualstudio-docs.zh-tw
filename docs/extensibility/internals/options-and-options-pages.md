---
title: 選項和選項頁面 |Microsoft Docs
description: 瞭解 [選項] 頁面的支援，讓您變更決定 VSPackage 狀態的選項值。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dac6c6898a8a8766d073cb5cd2f3bd330e7e2658
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954570"
---
# <a name="options-and-options-pages"></a>選項和選項頁
按一下 [**工具**] 功能表上的 [**選項**]，即可開啟 [**選項**] 對話方塊。 此對話方塊中的選項統稱為選項頁面。 流覽窗格中的樹狀目錄控制項包含選項分類，而每個類別都有選項頁面。 當您選取頁面時，其選項會顯示在右窗格中。 這些頁面可讓您變更決定 VSPackage 狀態的選項值。

## <a name="support-for-options-pages"></a>選項頁面的支援
 <xref:Microsoft.VisualStudio.Shell.Package>類別提供建立選項頁面和選項分類的支援。 <xref:Microsoft.VisualStudio.Shell.DialogPage>類別會執行 [選項] 頁面。

 的預設執行會 <xref:Microsoft.VisualStudio.Shell.DialogPage> 在屬性的一般方格中，將其公用屬性提供給使用者。 您可以藉由覆寫頁面上的各種方法來建立自訂選項頁面，該頁面會有自己的使用者介面 (UI) ，來自訂此行為。 如需詳細資訊，請參閱 [建立選項頁面](../../extensibility/creating-an-options-page.md)。

 <xref:Microsoft.VisualStudio.Shell.DialogPage>類別會執行 <xref:Microsoft.VisualStudio.Shell.IProfileManager> ，以提供選項頁面的持續性，也會提供使用者設定的持續性。 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> 如果屬性可以在字串之間來回轉換，和方法的預設執行會將屬性變更保存到登錄的使用者區段。

## <a name="options-page-registry-path"></a>選項頁面登錄路徑
 依預設，[選項] 頁面所管理之屬性的登錄路徑是由 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> [選項] 頁面類別的 [文字 DialogPage] 和 [類型名稱] 所決定。 例如，[選項] 頁面類別的定義可能如下所示。

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 如果 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp，則屬性名稱和值組是 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral 的子機碼。

 [選項] 頁面本身的登錄路徑是藉由結合 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> 、單字、ToolsOptionsPages 和 [選項] 頁面類別和名稱來決定。 例如，如果 [自訂選項] 頁面有 [類別]、[我的選項] 頁面， <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp，則 [選項] 頁面會有登錄機碼，HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom。

## <a name="toolsoptions-page-attributes-and-layout"></a>工具/選項頁面屬性和版面配置
 屬性會在 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> [ **選項** ] 對話方塊的導覽樹狀目錄中，決定將自訂選項頁面群組成類別目錄。 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>屬性會將選項頁面與提供介面的 VSPackage 產生關聯。 請考慮下列程式碼片段：

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 這會宣告 MyPackage 提供兩個選項頁面： OptionsPageGeneral 和 OptionsPageCustom。 在 [ **選項** ] 對話方塊中，[ **我的選項** 頁] 類別的 **[一般** ] 和 [ **自訂**] 中都會顯示這兩個選項頁。

## <a name="option-attributes-and-layout"></a>選項屬性和版面配置
 頁面提供的使用者介面 (UI) 可決定自訂選項頁面中選項的外觀。 [一般選項] 頁面中的 [配置]、[標記] 和 [說明] 選項，是由下列屬性所決定：

- <xref:System.ComponentModel.CategoryAttribute> 判斷選項的類別。

- <xref:System.ComponentModel.DisplayNameAttribute> 決定選項的顯示名稱。

- <xref:System.ComponentModel.DescriptionAttribute> 決定選項的描述。

  > [!NOTE]
  > 相等的屬性（SRCategory、LocDisplayName 和 SRDescription）會使用字串資源進行當地語系化，並定義于 [managed 專案範例](/azure/devops/integrate/index)中。

  請考慮下列程式碼片段：

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  [選項] 頁面上的 [OptionInteger] 選項會顯示為 [**我的選項**] 分類中的 [整數]**選項**。 如果選取此選項，[描述]、[ **我的整數] 選項** 會顯示在 [描述] 方塊中。

## <a name="accessing-options-pages-from-another-vspackage"></a>從其他 VSPackage 存取選項頁面
 您可以使用 automation 模型，以程式設計方式從另一個 VSPackage 存取裝載和管理選項頁面的 VSPackage。 例如，在下列程式碼中，VSPackage 會註冊為裝載選項頁面。

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 下列程式碼片段會從 MyOptionPage 取得 OptionInteger 的值：

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 當 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 屬性註冊 [選項] 頁面時，如果 `SupportsAutomation` 屬性的引數是，則會在 AutomationProperties 索引鍵下註冊頁面 `true` 。 自動化會檢查這個登錄專案，以尋找相關聯的 VSPackage，然後自動化會透過 [裝載的選項] 頁面（在此案例中為 [我的格線頁]）存取屬性。

 Automation 屬性的登錄路徑是藉由結合 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> 、單字、AutomationProperties 和 [選項] 頁面類別和名稱來決定。 例如，如果 [選項] 頁面有 [我的類別目錄]、[我的格線頁名稱] 和 [ <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp]，那麼 automation 屬性就會有登錄機碼 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My Grid Page。

> [!NOTE]
> 標準名稱 [我的 Category.My 格線頁] 是此索引鍵的名稱子機碼值。
