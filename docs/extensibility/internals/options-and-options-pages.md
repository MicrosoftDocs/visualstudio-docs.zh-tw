---
title: "選項與選項 頁面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: "34"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1177a9a4df1f07c93540fa039117c5fa81289e17
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="options-and-options-pages"></a>選項與選項 頁面
按一下**選項**上**工具**功能表開啟**選項** 對話方塊。 在此對話方塊中的選項合稱為 [選項] 頁。 樹狀目錄控制項導覽窗格中的包含的選項類別，而且每個類別目錄選項頁面。 當您選取的頁面時，它的選項會出現在右窗格中。 這些頁面可讓您變更判斷 VSPackage 的狀態選項的值。  
  
## <a name="support-for-options-pages"></a>支援選項頁  
 <xref:Microsoft.VisualStudio.Shell.Package>類別來建立選項頁面和選項類別提供支援。 <xref:Microsoft.VisualStudio.Shell.DialogPage>類別實作的選項頁面。  
  
 預設實作<xref:Microsoft.VisualStudio.Shell.DialogPage>至泛型屬性的方格中的使用者提供其公開屬性。 藉由覆寫各種方法來建立自訂選項頁面，其中包含它自己的使用者介面 (UI) 頁面上，您可以自訂此行為。 如需詳細資訊，請參閱[建立選項頁面](../../extensibility/creating-an-options-page.md)。  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage>類別會實作<xref:Microsoft.VisualStudio.Shell.IProfileManager>，提供持續性選項頁面和使用者設定。 預設實作之<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>和<xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A>方法保存至登錄的使用者 區段的屬性變更，如果與字串可以轉換屬性。  
  
## <a name="options-page-registry-path"></a>選項頁面的登錄路徑  
 根據預設，內容管理選項頁面的登錄路徑由合併<xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>，這個字 DialogPage，與選項頁類別的型別名稱。 例如的選項頁面的類別可能定義如下。  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]  
  
 如果<xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp，則屬性名稱 / 值組會 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ 的子機碼Company.OptionsPage.OptionsPageGeneral。  
  
 登錄路徑的 [選項] 頁面本身由合併<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>，word、 ToolsOptionsPages，以及選項頁面類別目錄和名稱。 例如，如果 自訂 選項頁面有 我的選項頁面，類別目錄和<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp，則 選項 頁面已登錄機碼，HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My 選項 Pages\Custom。  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>工具/選項頁面的屬性和配置  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>屬性會決定要分組的自訂選項頁面的導覽樹狀目錄中的類別到**選項** 對話方塊。 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> VSPackage 提供介面與屬性產生關聯的選項頁面。 請考慮下列程式碼片段：  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]  
  
 這會宣告 MyPackage 提供兩個選項和頁面，OptionsPageGeneral OptionsPageCustom。 在**選項**中會出現的對話方塊中，這兩個選項頁面**我選項頁面**類別，以作為**一般**和**自訂**分別。  
  
## <a name="option-attributes-and-layout"></a>選項屬性和配置  
 頁面會提供使用者介面 (UI) 外觀的自訂選項頁面中的選項。 版面配置、 標記和描述的一般選項 頁面中的選項會決定下列屬性：  
  
-   <xref:System.ComponentModel.CategoryAttribute>決定的選項類別。  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>決定選項的顯示名稱。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>決定選項的描述。  
  
    > [!NOTE]
    >  對等的屬性、 SRCategory、 LocDisplayName，SRDescription，字串資源的當地語系化和使用中定義[受管理的專案範例](http://go.microsoft.com/fwlink/?LinkId=122774)。  
  
 請考慮下列程式碼片段：  
  
 [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]  
  
 OptionInteger 選項會出現在 [選項] 頁面，為**整數選項**中**My Options**類別目錄。 如果選取此選項，則描述**我整數選項**，會出現在 [描述] 方塊。  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>從另一個 VSPackage 存取選項頁面  
 裝載和管理選項頁面的 VSPackage 可以透過程式設計方式存取從另一個 VSPackage 使用 automation 模型。 例如，下列程式碼 VSPackage 登錄為裝載選項頁面。  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]  
  
 下列程式碼片段會取得從 MyOptionPage OptionInteger 的值：  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]  
  
 當<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>屬性註冊選項頁面的頁面並已登錄，AutomationProperties 鍵，如果下`SupportsAutomation`屬性的引數是`true`。 自動化會檢查此登錄項目，來尋找相關聯的 VSPackage 和自動化，然後透過託管的選項頁面上，在此情況下，我的格線頁中存取屬性。  
  
 Automation 屬性的登錄路徑由合併<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>，word、 AutomationProperties，以及選項頁面類別目錄和名稱。 例如，如果 選項 頁面的 我的類別目錄類別，我的格線頁名稱，而<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>，HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp，則 automation 屬性已登錄機碼，HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My 格線頁。  
  
> [!NOTE]
>  正式名稱，我的 Category.My 格線頁中，為此機碼名稱子機碼值。