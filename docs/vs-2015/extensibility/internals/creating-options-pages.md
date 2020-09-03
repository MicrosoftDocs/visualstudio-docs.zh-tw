---
title: 建立選項頁 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c2b993a6c6947adfa3b01f2947b992b23236b8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196941"
---
# <a name="creating-options-pages"></a>建立選項頁
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] managed 封裝架構中，從 [工具] 功能表底下新增 [選項] 頁面，衍生自的類別會 <xref:Microsoft.VisualStudio.Shell.DialogPage> 延伸 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE。 **Options** **Tools**  
  
 執行指定 **工具選項** 頁面的物件與物件的特定 vspackage 相關聯 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 。  
  
 因為環境會在 IDE 顯示特定頁面時，將執行特定 [ **工具選項** ] 頁面的物件具現化：  
  
- [ **工具] 選項** 頁應該在其本身的物件上執行，而不是在執行 VSPackage 的物件上。  
  
- 物件無法執行多個 **工具選項** 頁面。  
  
## <a name="registering-as-a-tools-options-page-provider"></a>註冊為工具選項頁面提供者  
 透過 [ **工具選項** ] 頁面支援使用者設定的 VSPackage，會透過套用套用至執行的實例，表示提供這些 **工具選項** 頁面的物件 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> <xref:Microsoft.VisualStudio.Shell.Package> 。  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>針對每個衍生的 [ <xref:Microsoft.VisualStudio.Shell.DialogPage> **工具選項**] 頁面的衍生類型，都必須有一個實例。  
  
 的每個實例都使用可執行 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> [ **工具選項** ] 頁面的型別、包含用來識別 [ **工具選項** ] 頁面之類別目錄和子類別的字串，以及將類型註冊為提供 [ **工具選項** ] 頁面的資源資訊。  
  
## <a name="persisting-tools-options-page-state"></a>保存工具選項頁面狀態  
 如果已在啟用 automation 支援的情況下註冊 **工具選項** 頁面執行，IDE 會保存頁面的狀態以及所有其他 **工具選項** 頁面。  
  
 VSPackage 可以使用來管理自己的持續性 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 。 只應使用一個或另一個持續性方法。  
  
## <a name="implementing-dialogpage-class"></a>執行 DialogPage 類別  
 提供 VSPackage 之 <xref:Microsoft.VisualStudio.Shell.DialogPage> 衍生型別的物件可利用下列繼承的功能：  
  
- 預設使用者介面視窗。  
  
- 如果套用 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 至類別，或如果將套用 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> 至類別的屬性設為，則可以使用預設的持續性機制 `true` <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 。  
  
- 自動化支援。  
  
  使用執行 [ **工具選項** ] 頁面之物件的最低需求 <xref:Microsoft.VisualStudio.Shell.DialogPage> 是新增公用屬性。  
  
  如果類別已正確註冊為 [**工具選項**] 頁面提供者，則可以在 [**工具**] 功能表的 [**選項**] 區段中，以屬性方格的形式取得其公用屬性。  
  
  所有這些預設功能都可以覆寫。 例如，若要建立更複雜的使用者介面，則只需要覆寫的預設執行 <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A> 。  
  
## <a name="example"></a>範例  
 接下來是簡單的「hello world」選項頁面執行。 將下列程式碼新增至 Visual Studio 套件範本所建立的預設專案，並選取 [ **功能表命令** ] 選項，可充分示範選項頁面功能。  
  
### <a name="description"></a>描述  
 下列類別會定義最短的 "hello world" 選項頁面。 開啟時，使用者可以 `HelloWorld` 在屬性方格中設定公用屬性。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/class1.cs#11)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/class1.vb#11)]  
  
### <a name="description"></a>描述  
 將下列屬性套用至 package 類別，可讓您在封裝載入時使用 [選項] 頁面。 這些數位是類別和頁面的任意資源識別碼，而結尾的布林值會指定頁面是否支援 automation。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#07)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#07)]  
  
### <a name="description"></a>描述  
 下列事件處理常式會根據 [選項] 頁面中設定的屬性值來顯示結果。 它會使用 <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> 方法，並將結果明確轉換成自訂選項頁面類型，以存取頁面所公開的屬性。  
  
 如果是封裝範本所產生的專案，請從函式呼叫這個函式，將 `MenuItemCallback` 它附加至新增至 [ **工具** ] 功能表的預設命令。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#08)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#08)]  
  
## <a name="see-also"></a>另請參閱  
 [擴充使用者設定和選項](../../extensibility/extending-user-settings-and-options.md)   
 [選項頁的自動化支援](../../extensibility/internals/automation-support-for-options-pages.md)
