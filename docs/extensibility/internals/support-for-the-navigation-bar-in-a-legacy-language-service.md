---
title: "導覽列的舊版語言服務支援 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 935ea7d9fde2872c952f79afaa95058e9f18d0a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>導覽列的舊版語言服務的支援
導覽列頂端的編輯器檢視會顯示檔案中的類型和成員。 類型會以左側下拉式清單中，而成員就會顯示在右側下拉式清單。 當使用者選取類型時，將插入號會放在類型的第一行。 當使用者選取成員時，會將插入號放在成員的定義。 下拉式清單方塊會更新以反映目前的插入號位置。  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>顯示和更新的導覽列  
 若要支援巡覽列，您必須衍生自<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>類別，並實作<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法。 當語言服務會指定程式碼視窗中，基底<xref:Microsoft.VisualStudio.Package.LanguageService>類別具現化<xref:Microsoft.VisualStudio.Package.CodeWindowManager>，其中包含<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>物件，表示程式碼視窗。 <xref:Microsoft.VisualStudio.Package.CodeWindowManager>物件則提供新<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>物件。 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>方法取得<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>物件。 如果傳回的執行個體您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>類別，<xref:Microsoft.VisualStudio.Package.CodeWindowManager>呼叫您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法來填入內部列出，並傳遞您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>物件[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]下拉式清單列管理員。 在下拉式清單列管理員 中，接著呼叫<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>方法上的您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>物件來建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>保存兩個下拉式清單列的物件。  
  
 當插入號移時，<xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A>方法呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>方法。 基底<xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>方法呼叫<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法在您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>類別來更新導覽列的狀態。 您傳遞的一組<xref:Microsoft.VisualStudio.Package.DropDownMember>物件給這個方法。 每個物件都代表在下拉式清單中的項目。  
  
## <a name="the-contents-of-the-navigation-bar"></a>導覽列的內容  
 導覽列通常包含一份型別和成員的清單。 型別的清單中目前的原始程式檔包含所有可用的類型。 型別名稱包含完整的命名空間資訊。 C# 程式碼有兩種類型的範例如下：  
  
```csharp  
namespace TestLanguagePackage  
{  
    public class TestLanguageService  
    {  
        internal struct Token  
        {  
            int tokenID;  
        }  
        private Tokens[] tokens;  
        private string serviceName;  
    }  
}  
```  
  
 [類型] 清單會顯示`TestLanguagePackage.TestLanguageService`和`TestLanguagePackage.TestLanguageService.Tokens`。  
  
 成員清單會顯示可用類型清單中選取之類型的成員。 如果使用上述項目，在程式碼範例`TestLanguagePackage.TestLanguageService`的型別已選取 [成員] 清單會包含私用成員`tokens`和`serviceName`。 內部結構`Token`不會顯示。  
  
 您可以實作 [成員] 清單，讓成員名稱在插入號放在它之內時變成粗體。 成員也可以顯示在灰色文字表示，則這些不目前位於插入號所在位置的範圍內。  
  
## <a name="enabling-support-for-the-navigation-bar"></a>啟用支援，在導覽列  
 若要啟用導覽列的支援，您必須設定`ShowDropdownBarOption`參數<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>屬性`true`。 這個參數會設定 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> 屬性。 若要支援巡覽列，您必須實作<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>物件存放至<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>方法<xref:Microsoft.VisualStudio.Package.LanguageService>類別。  
  
 在您實作<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>方法，如果<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>屬性設定為`true`，您可以傳回<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>物件。 如果您不會傳回物件，不會顯示在導覽列。  
  
 使用者可以設定顯示導覽列的選項，因此可以開啟編輯器檢視時重設此控制項。 使用者必須關閉再重新開啟編輯器視窗，進行變更之前。  
  
## <a name="implementing-support-for-the-navigation-bar"></a>實作支援導覽列  
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法會採用兩個清單 （一個用於每個下拉式清單） 和兩個值代表每個清單中的目前選取範圍。 清單及選取項目值可加以更新，在此情況下<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法必須傳回`true`，表示清單已變更。  
  
 隨著選取範圍的變更類型 下拉式清單中，必須更新 成員 清單，以反映新的類型。 在 [成員] 清單中顯示的內容可以是：  
  
-   目前類型的成員的清單。  
  
-   中的所有成員可用來源檔案，但與不在目前類型的所有成員，以灰色文字顯示。 使用者仍然可以選取呈現灰色的成員，因此可用於快速瀏覽，但色彩表示它們不屬於目前選取的類型。  
  
 實作<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法通常會執行下列步驟：  
  
1.  取得目前宣告的原始程式檔的清單。  
  
     有數種方式來填入清單。 其中一個方法是在您的版本上建立的自訂方法<xref:Microsoft.VisualStudio.Package.LanguageService>呼叫的類別<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法會傳回一份所有宣告的自訂剖析原因。 另一種方法可能會呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法，直接從<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法以自訂剖析原因。 第三種方法可能會快取中的宣告<xref:Microsoft.VisualStudio.Package.AuthoringScope>類別中的最後一個完整剖析作業所傳回<xref:Microsoft.VisualStudio.Package.LanguageService>類別，並擷取與<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法。  
  
2.  填入或更新的類型清單。  
  
     型別清單的內容可能會更新來源變更時，或如果您已選擇要變更文字樣式，依據目前的插入號位置的類型。 請注意，這個位置傳遞至<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法。  
  
3.  決定要在目前插入號位置為基礎的型別清單中選取的類型。  
  
     您可以在步驟 1，尋找此型別的封入目前的插入號位置中搜尋所取得的宣告，，然後搜尋該型別來判斷它的索引類型的清單中的 [類型] 清單。  
  
4.  填入或更新成員根據所選類型的清單。  
  
     [成員] 清單會反映目前顯示之內容**成員**下拉式清單。 [成員] 清單的內容，可能需要更新來源已變更，或如果您要顯示所選類型的成員，而且選取的類型已變更。 如果您選擇要顯示原始程式檔中的所有成員，文字樣式，清單中每個成員必須更新目前選取的類型已變更。  
  
5.  決定要根據目前的插入號位置的 [成員] 清單中選取的成員。  
  
     搜尋所取得的宣告在步驟 1 中的成員，其中包含目前的插入號位置，然後搜尋該成員來判斷其索引成員的清單中的 [成員] 清單。  
  
6.  傳回`true`如果任何已變更的清單或任一個清單中的選取項目。