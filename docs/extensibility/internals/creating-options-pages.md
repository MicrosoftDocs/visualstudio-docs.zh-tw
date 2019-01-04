---
title: 建立選項頁 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 879d094051efd6a64af1c43cb96be71fbc67f5ca
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820633"
---
# <a name="create-options-pages"></a>建立選項頁
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]managed 的封裝架構類別衍生自<xref:Microsoft.VisualStudio.Shell.DialogPage>擴充[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]藉由新增 IDE**選項**頁面下**工具**功能表。  
  
 物件，實作給定**工具選項**頁面是特定的 Vspackage，由相關聯<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>物件。  
  
 因為環境實作特定的物件會具現化**工具選項**頁面時，IDE 會顯示該特定網頁：  
  
-   A**工具選項**應該實作頁面，在其本身的物件，而不是在實作 VSPackage 的物件。  
  
-   物件不能實作多個**工具選項**頁面。  
  
## <a name="register-as-a-tools-options-page-provider"></a>註冊工具選項頁面提供者為  
 VSPackage 支援使用者透過設定**工具選項**頁面會指出提供這些物件**工具選項**藉由套用的執行個體的頁面<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>套用至<xref:Microsoft.VisualStudio.Shell.Package>實作。  
  
 必須有一個執行個體<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>針對每個<xref:Microsoft.VisualStudio.Shell.DialogPage>-衍生實作的型別**工具選項**頁面。  
  
 每個執行個體<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>會使用實作的型別**工具選項**頁面上，包含類別和子類別，用來識別字串**工具選項** 頁面上，與資源若要註冊為提供的類型資訊**工具選項**頁面。  
  
## <a name="persist-tools-options-page-state"></a>保存工具選項頁面狀態  
 如果**工具選項**啟用的自動化支援註冊頁面實作，IDE 會保存頁面的狀態，以及所有其他**工具選項**頁面。  
  
 VSPackage 可以使用來管理它自己的持續性<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>。 應該使用其中之一或持續性的另一個方法。  
  
## <a name="implement-dialogpage-class"></a>實作 DialogPage 類別  
 這個物件提供 VSPackage 實作<xref:Microsoft.VisualStudio.Shell.DialogPage>-衍生的型別可以利用下列繼承的功能：  
  
- 預設使用者介面視窗。  
  
- 預設持續性機制，可以使用任一 if<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>套用至類別，或者如果<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A>屬性設定為`true`的<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>套用至類別。  
  
- 自動化支援。  
  
  物件，實作的最低需求**工具選項**頁面上使用<xref:Microsoft.VisualStudio.Shell.DialogPage>是加入的公用屬性。  
  
  如果類別已正確註冊為**工具選項**頁面上提供者，則其公用屬性位於**選項**一節**工具**功能表中的表單屬性方格。  
  
  所有這些預設的功能可以被覆寫。 例如，若要建立更複雜的使用者介面需要只覆寫的預設實作<xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>。  
  
## <a name="example"></a>範例  
 以下是簡單"Hello world"的實作選項頁面。 將下列程式碼加入預設專案與 Visual Studio 封裝範本所建立**功能表命令**選項選取適當地將示範選項頁面的功能。  
  
### <a name="description"></a>描述  
 下列類別定義的基本"Hello world"選項頁面。 開啟時，使用者可以設定公用`HelloWorld`在屬性方格中的屬性。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>描述  
 將下列屬性套用至套件類別讓頁面上的選項可載入封裝時。 數字是任意的資源識別碼分類的頁面上，並在結束的布林值可讓您指定的頁面是否支援自動化。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>描述  
 下列事件處理常式會顯示 [選項] 頁面中設定的屬性值而定的結果。 它會使用<xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>結果的方法，明確轉換成的自訂選項頁面型別存取頁面所公開的屬性。  
  
 封裝範本所產生的專案，在呼叫這個函式從`MenuItemCallback`函式，將它附加至的預設命令新增至**工具**功能表。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [擴充使用者設定和選項](../../extensibility/extending-user-settings-and-options.md)   
 [自動化支援的選項頁面](../../extensibility/internals/automation-support-for-options-pages.md)