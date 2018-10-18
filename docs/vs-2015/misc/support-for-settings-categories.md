---
title: 設定類別的支援 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- settings, supporting with Visual Studio SDK
- Visual Studio SDK, supporting settings
ms.assetid: 3bac375d-8bd5-41be-a8de-32eb33c5cfac
caps.latest.revision: 20
manager: douge
ms.openlocfilehash: 53abd3c9f35f16c2f2ae62e2c4f339a86477a8b3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244929"
---
# <a name="support-for-settings-categories"></a>設定類別的支援
設定類別包含自訂整合式開發環境 (IDE) 的選項群組。 例如，設定可以控制 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 視窗的配置和功能表的內容。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 在 [工具]  功能表上，按一下 [匯入和匯出設定]  啟動 [匯入和匯出設定精靈] 。 此精靈提供三個選項︰匯出、匯入或重設您的設定。 選取 [匯出]，例如開啟精靈的 [選擇要匯出的設定]  頁面。  
  
 此頁面之巡覽窗格中的樹狀目錄控制項會列出類別。 類別是一組顯示為「自訂設定點」(即核取方塊) 的相關設定。 您可以使用這些核取方塊來選取要保存在 .vsettings 檔案中的類別。 此精靈可讓您命名 .vsettings 檔案，並指定其路徑。  
  
> [!NOTE]
>  設定會儲存或還原為類別，而個別設定名稱則不會顯示在精靈中。  
  
 Managed Package Framework (MPF) 支援撰寫最少的額外程式碼來建立設定類別。  
  
-   將 <xref:Microsoft.VisualStudio.Shell.Package> 類別 (class) 設定為子類別，即可建立 VSPackage 來提供類別 (category) 的容器。  
  
-   從 <xref:Microsoft.VisualStudio.Shell.DialogPage> 類別 (class) 衍生類別 (category)，即可建立類別 (category) 本身。  
  
-   您可以使用 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 來連接這兩者。  
  
## <a name="support-for-settings-categories"></a>設定類別的支援  
 <xref:Microsoft.VisualStudio.Shell.Package> 類別 (class) 支援建立類別 (category)。 <xref:Microsoft.VisualStudio.Shell.DialogPage> 類別 (class) 會實作類別 (category)。 <xref:Microsoft.VisualStudio.Shell.DialogPage> 的預設實作會將其公用屬性當成類別提供給使用者。 如需詳細資訊，請參閱 [Creating a Settings Category](../extensibility/creating-a-settings-category.md)。  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> 類別會實作 <xref:Microsoft.VisualStudio.Shell.IProfileManager>，以提供選項頁面和使用者設定的持續性。 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> 和 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> 方法會將設定持續保存至 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 分別提供為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> 的 .vssettings 檔案。 <xref:Microsoft.VisualStudio.Shell.IProfileManager.ResetSettings%2A> 方法會將設定重設為其預設值。  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> 類別提供 <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromXml%2A> 方法的實作，以讀取 XML 摘要中的名稱/值組，以及使用反射來探索 <xref:Microsoft.VisualStudio.Shell.DialogPage> 衍生類別中的公用屬性。 名稱與名稱/值組相符的屬性會具有對應的值。  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage.SaveSettingsToXml%2A> 的預設實作會使用反射來探索 <xref:Microsoft.VisualStudio.Shell.DialogPage> 衍生類別中的公用屬性，並將屬性名稱和值以名稱/值組形式寫入 XML 摘要。  
  
### <a name="settings-category-registry-path"></a>設定類別登錄路徑  
 設定類別的登錄路徑是透過合併 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>、字組、UserSettings、設定類別以及自訂設定點名稱所決定。 會連結設定類別和自訂設定點的名稱，並用底線區隔，以形成出現在登錄中的標準非當地語系化名稱。 例如，如果設定類別為 "My Category"、自訂設定點名稱為 "My Settings" 且 ApplicationRegistryRoot 為 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp，則設定類別的登錄機碼為 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\UserSettings\My Category_My Settings。  
  
> [!NOTE]
>  標準名稱不會出現在使用者介面 (UI) 中。 它用來將可讀名稱與設定類別產生關聯，這與程式設計識別項 (ProgID) 十分類似。  
  
### <a name="settings-category-attribute"></a>設定類別屬性  
 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>判斷類別目錄中的自訂設定點的對應**匯入和匯出設定精靈**與提供它的 VSPackage 產生關聯的類別。 請考慮下列程式碼片段：  
  
 [!code-csharp[VSSDKSupportForSettingsCategories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforsettingscategories/cs/vssdksupportforsettingscategoriespackage.cs#1)]
 [!code-vb[VSSDKSupportForSettingsCategories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforsettingscategories/vb/vssdksupportforsettingscategoriespackage.vb#1)]  
  
 資源識別碼 106 對應至 "My Category"、107 對應至 "My Settings"，而 108 對應至 "Various Options"。 這會宣告 `MyPackage` 提供類別 My Category_My Settings。 類別 (category) 是由 `OptionsPageGeneral` 類別 (class) 所提供，而後者必須實作 <xref:Microsoft.VisualStudio.Shell.IProfileManager>。 該類別 (category) 中的設定是 `OptionsPageGeneral` 類別 (class) 的公用屬性。  
  
 在 [匯入和匯出設定精靈] 中，設定點的名稱為 My Settings。 選取設定點時，描述 ( **Various Options**) 隨即出現。 設定點名稱和描述取自當地語系化的字串資源。  
  
## <a name="see-also"></a>另請參閱  
 [建立選項頁](../extensibility/creating-an-options-page.md)   
 [VSSDK 範例](../misc/vssdk-samples.md)   
 [VSPackage 狀態](../misc/vspackage-state.md)   
 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)