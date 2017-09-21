---
title: "選項和選項頁面 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具選項頁面 [Visual Studio SDK]，管理封裝 framework 支援"
  - "受管理的封裝架構、 工具選項頁支援"
  - "工具選項頁的支援"
  - "工具選項頁 [Visual Studio SDK]，版面配置"
  - "工具選項頁 [Visual Studio SDK]，屬性"
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 34
---
# 選項和選項頁面
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

按一下 **選項** 上 **工具** 功能表開啟 **選項** 對話方塊。 在此對話方塊中的選項合稱為選項頁面。 瀏覽窗格中的樹狀目錄控制項包含選項類別，而且每個類別目錄選項頁面。 當您選取頁面的選項會出現在右窗格中。 這些頁面可讓您變更選項，以決定 VSPackage 狀態的值。  
  
## 支援選項頁  
 <xref:Microsoft.VisualStudio.Shell.Package> 類別提供建立選項頁面和選項類別支援。<xref:Microsoft.VisualStudio.Shell.DialogPage> 類別會實作選項\] 頁面。  
  
 預設實作 <xref:Microsoft.VisualStudio.Shell.DialogPage> 泛用的屬性方格中的使用者提供其公用屬性。 藉由覆寫各種方法來建立自訂選項頁面，其中包含它自己的使用者介面 \(UI\) 頁面上，您可以自訂此行為。 如需詳細資訊，請參閱[建立選項\] 頁面](../Topic/Creating%20an%20Options%20Page.md)。  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> 類別會實作 <xref:Microsoft.VisualStudio.Shell.IProfileManager>, ，這樣會提供持續性選項頁以及使用者設定。 預設實作 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> 和 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> 方法保存屬性變更登錄使用者區段中，如果可以轉換的屬性，與字串。  
  
## 選項頁面登錄路徑  
 根據預設，由 \[選項\] 頁面上的屬性的登錄路徑由合併 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, ，DialogPage，and 選項頁面類別的型別名稱。 例如，選項頁面類別可以定義，如下所示。  
  
 [!CODE [VSSDKSupportForOptionsPages#1](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#1)]  
  
 如果 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> 是 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp，則屬性名稱 \/ 值組的 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp\\DialogPage\\Company.OptionsPage.OptionsPageGeneral 子機碼。  
  
 \[選項\] 頁面本身的登錄路徑由合併 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, ，word、 ToolsOptionsPages 及選項頁面類別目錄和名稱。 例如，如果自訂選項\] 頁面上有該類別，我選項頁，而 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp，則 \[選項\] 頁面上已登錄機碼，HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\ToolsOptionsPages\\My 選項 Pages\\Custom。  
  
## 工具\/選項頁面的屬性和配置  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 屬性會決定群組的自訂選項頁面的瀏覽樹狀目錄中的類別為 **選項** 對話方塊。<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 屬性關聯提供介面的 VSPackage 選項\] 頁面。 請考慮下列程式碼片段：  
  
 [!CODE [VSSDKSupportForOptionsPages#2](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#2)]  
  
 這會宣告 MyPackage 提供兩個選項和頁面，OptionsPageGeneral OptionsPageCustom。 在 **選項** 中會出現的對話方塊中，這兩個選項頁面 **我選項頁面** 類別，以作為 **一般** 和 **自訂**, 分別。  
  
## 選項屬性和版面配置  
 在頁面上的使用者介面 \(UI\) 外觀的自訂選項頁面中的選項。 版面配置、 標記、 和描述的一般選項\] 頁面中的選項決定下列屬性︰  
  
-   <xref:System.ComponentModel.CategoryAttribute> 決定選項的類別。  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> 決定選擇的顯示名稱。  
  
-   <xref:System.ComponentModel.DescriptionAttribute> 決定選項的描述。  
  
    > [!NOTE]
    >  對等的屬性、 SRCategory、 LocDisplayName 和 SRDescription，用於當地語系化字串資源，且已定義在 [受管理的專案範例](http://go.microsoft.com/fwlink/?LinkId=122774)。  
  
 請考慮下列程式碼片段：  
  
 [!CODE [VSSDKSupportForOptionsPages#3](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#3)]  
  
 OptionInteger 選項會出現在 \[選項\] 頁面，為 **整數選項** 中 **My Options** 類別。 如果選取此選項，則描述 **我整數選項**, ，會出現在 \[描述\] 方塊。  
  
## 從另一個 VSPackage 存取選項頁面  
 裝載，並且管理選項\] 頁面的 VSPackage 可以以程式設計方式存取來自另一個 VSPackage 使用 automation 模型。 例如，下列程式碼 VSPackage 會註冊為裝載選項頁面。  
  
 [!CODE [VSSDKSupportForOptionsPages#4](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#4)]  
  
 下列程式碼片段會取得從 MyOptionPage OptionInteger 的值︰  
  
 [!CODE [VSSDKSupportForOptionsPages#5](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#5)]  
  
 當 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 屬性註冊選項頁面、 AutomationProperties 鍵，如果在註冊頁面 `SupportsAutomation` 屬性的引數是 `true`。 自動化會檢查此登錄項目，來尋找相關聯的 VSPackage 和自動化，然後透過裝載的選項\] 頁面上，在此情況下，我的格線頁中存取的屬性。  
  
 Automation 屬性的登錄路徑由合併 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, ，word、 AutomationProperties 及選項頁面類別目錄和名稱。 例如，如果 \[選項\] 頁面上有 \[My Category 類別，我的格線頁名稱，而 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, ，HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp，則自動化屬性已登錄機碼，HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\AutomationProperties\\My Category\\My 格線頁。  
  
> [!NOTE]
>  正式名稱，也就是我 Category.My 格線頁中，是這個機碼名稱子機碼值。