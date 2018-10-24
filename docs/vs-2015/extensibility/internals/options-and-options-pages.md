---
title: 選項和選項頁 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e9cd4ea3b1465686ee2c0a0ebcfdc4e3aa2e9e56
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816348"
---
# <a name="options-and-options-pages"></a>選項和選項頁
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

按一下 **選項**上**工具** 功能表隨即開啟**選項** 對話方塊。 在此對話方塊中的選項會統稱為選項 頁面。 瀏覽窗格中的樹狀控制項包含選項類別，而且每個類別目錄選項頁面。 當您選取的頁面時，它的選項會出現在右窗格中。 這些頁面可讓您變更判斷 VSPackage 的狀態選項的值。  
  
## <a name="support-for-options-pages"></a>支援選項頁  
 <xref:Microsoft.VisualStudio.Shell.Package>類別建立選項頁面和選項類別提供支援。 <xref:Microsoft.VisualStudio.Shell.DialogPage>類別會實作選項頁面。  
  
 預設實作<xref:Microsoft.VisualStudio.Shell.DialogPage>泛用的屬性方格中的使用者提供其公用屬性。 藉由覆寫各種方法來建立自訂選項頁面，其中包含它自己的使用者介面 (UI) 頁面上，您可以自訂此行為。 如需詳細資訊，請參閱 <<c0> [ 建立選項頁](../../extensibility/creating-an-options-page.md)。  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage>類別會實作<xref:Microsoft.VisualStudio.Shell.IProfileManager>，以提供持續性選項頁以及使用者設定。 預設實作<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>和<xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A>方法保存至登錄的 [使用者] 區段的屬性變更，如果可以轉換的屬性，與字串。  
  
## <a name="options-page-registry-path"></a>選項頁面登錄路徑  
 根據預設，登錄路徑的 [選項] 頁面所管理的屬性由合併<xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>，word DialogPage 和選項頁面類別的型別名稱。 比方說，選項頁面類別可能會定義，如下所示。  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#1)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#1)]  
  
 如果<xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp，則屬性名稱 / 值組是子機碼的 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral。  
  
 [選項] 頁面本身的登錄路徑由合併<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>，word、 ToolsOptionsPages，以及選項頁面上的分類和名稱。 例如，如果自訂的 [選項] 頁面已在類別中，我的選項頁面，而<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>為 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp，則 [選項] 頁面已登錄機碼，而 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My 選項 Pages\Custom。  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>工具/選項頁面的屬性和版面配置  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>屬性會決定成類別目錄，在導覽樹狀目錄中的自訂選項頁面的群組**選項** 對話方塊。 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>屬性會將選項頁面關聯的 VSPackage 提供的介面。 請考慮下列程式碼片段：  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#2)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#2)]  
  
 這會宣告 MyPackage 提供兩個選項和頁面，OptionsPageGeneral OptionsPageCustom。 在 **選項** 對話方塊中，這兩個選項 頁面會出現在**My 選項頁面**類別，以作為**一般**和**自訂**分別。  
  
## <a name="option-attributes-and-layout"></a>選項屬性和版面配置  
 頁面會提供使用者介面 (UI) 決定的選項中的自訂選項頁面的外觀。 版面配置、 標記和描述的一般選項 頁面中的選項是由下列屬性所決定：  
  
- <xref:System.ComponentModel.CategoryAttribute> 決定選項分類。  
  
- <xref:System.ComponentModel.DisplayNameAttribute> 決定選項的顯示名稱。  
  
- <xref:System.ComponentModel.DescriptionAttribute> 決定選項的描述。  
  
  > [!NOTE]
  >  對等的屬性、 SRCategory、 LocDisplayName，SRDescription，字串資源當地語系化，並使用定義於[受管理的專案範例](http://go.microsoft.com/fwlink/?LinkId=122774)。  
  
  請考慮下列程式碼片段：  
  
  [!code-csharp[VSSDKSupportForOptionsPages#3](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs#3)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb#3)]  
  
  OptionInteger 選項會顯示為 [選項] 頁面上**整數選項**中**My Options**類別目錄。 如果選取此選項，則描述**我的 [整數] 選項**，會出現在 [描述] 方塊。  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>從另一個 VSPackage 中存取 [選項] 頁面  
 裝載和管理選項 頁面的 VSPackage 可以透過程式設計方式存取從另一個 VSPackage 使用 automation 模型。 例如，下列程式碼的 VSPackage 會註冊為裝載選項頁面。  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#4)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#4)]  
  
 下列程式碼片段會取得從 MyOptionPage OptionInteger 的值：  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#5)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#5)]  
  
 當<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>屬性會註冊選項頁面，註冊頁面時 AutomationProperties 鍵，如果`SupportsAutomation`屬性的引數是`true`。 自動化會檢查此登錄項目，若要尋找的相關聯的 VSPackage 和自動化，然後透過裝載的選項頁面上，在此情況下，我的格線頁中存取的屬性。  
  
 自動化屬性的登錄路徑由合併<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>，word、 AutomationProperties，以及選項頁面上的分類和名稱。 例如，如果 [選項] 頁面有 [我的類別目錄] 類別中，我的格線頁名稱，而<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>，HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp，則 [自動化] 屬性已登錄機碼，這是 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My 格線頁。  
  
> [!NOTE]
>  正式名稱，也就是我的 Category.My 格線頁中，是這個機碼名稱子機碼的值。

