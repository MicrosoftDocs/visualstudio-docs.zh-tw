---
title: "建立選項頁 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ae8540a2f372abacd8eda6e63cd868edbb050392
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="creating-options-pages"></a>建立選項頁面
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]managed 的封裝架構類別衍生自<xref:Microsoft.VisualStudio.Shell.DialogPage>擴充[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]加入 IDE**選項**頁面下**工具**功能表。  
  
 實作指定**工具選項**頁面都與特定的 Vspackage<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>物件。  
  
 因為環境實作特定的物件會具現化**工具選項**網頁時，IDE 會顯示該特定頁面：  
  
-   A**工具選項**頁面應該實作自己的物件，而不是在實作 VSPackage 的物件。  
  
-   物件不能實作多個**工具選項**頁面。  
  
## <a name="registering-as-a-tools-options-page-provider"></a>註冊工具選項頁面提供者為  
 VSPackage 支援使用者設定透過**工具選項**頁面指出提供這些物件**工具選項**頁面套用的執行個體<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>套用至<xref:Microsoft.VisualStudio.Shell.Package>實作。  
  
 必須有一個執行個體<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>的每個<xref:Microsoft.VisualStudio.Shell.DialogPage>-衍生型別可實作**工具選項**頁面。  
  
 每個執行個體<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>使用實作的型別**工具選項**頁面上，包含類別和子類別，用來識別字串**工具選項** 頁面上和資源若要註冊為提供的類型資訊**工具選項**頁面。  
  
## <a name="persisting-tools-options-page-state"></a>保存的工具選項頁面狀態  
 如果**工具選項**頁面實作向啟用自動化支援，IDE 會保存在網頁的狀態，以及所有其他**工具選項**頁面。  
  
 VSPackage 可以使用管理它自己的持續性<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>。 應該使用其中之一或其他持續性方法。  
  
## <a name="implementing-dialogpage-class"></a>實作 DialogPage 類別  
 物件提供的 VSPackage 實作<xref:Microsoft.VisualStudio.Shell.DialogPage>-衍生型別可以利用下列繼承的功能：  
  
-   預設使用者介面視窗。  
  
-   預設持續性機制，可以使用任一如果<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>套用至類別，或如果<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A>屬性設定為`true`如<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>套用至類別。  
  
-   自動化支援。  
  
 實作的最低需求**工具選項**網頁的<xref:Microsoft.VisualStudio.Shell.DialogPage>是新加入的公用屬性。  
  
 如果類別已正確登錄為**工具選項**頁面上提供者，則其公開屬性位於**選項**區段**工具**功能表中的表單屬性方格。  
  
 可以覆寫這些預設功能。 例如，若要建立更趨精密完美的使用者介面需要只覆寫的預設實作<xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>。  
  
## <a name="example"></a>範例  
 以下是簡單"hello world"的實作的選項頁面。 將下列程式碼加入至預設專案與 Visual Studio 封裝範本所建立**功能表命令**選取的選項將充分示範選項頁面的功能。  
  
### <a name="description"></a>描述  
 下列類別定義的最小的"hello world"選項頁面。 開啟時，使用者可以設定公開`HelloWorld`屬性方格中的屬性。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>描述  
 將下列屬性套用至在封裝類別讓頁面上的選項可載入封裝時。 數字會針對類別目錄和頁面上，任意的資源識別碼和結尾的布林值，指定該分頁是否支援自動化。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>描述  
 下列事件處理常式會顯示在 [選項] 頁面中設定的屬性值而定的結果。 它會使用<xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>方法的結果明確地轉換成自訂選項的頁面類型，若要存取此網頁所公開的屬性。  
  
 封裝範本所產生的專案，在呼叫此函式從`MenuItemCallback`函式，將它附加至的預設命令加入至**工具**功能表。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>請參閱  
 [擴充使用者設定和選項](../../extensibility/extending-user-settings-and-options.md)   
 [選項頁的自動化支援](../../extensibility/internals/automation-support-for-options-pages.md)