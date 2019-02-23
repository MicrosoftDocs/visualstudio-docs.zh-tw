---
title: 在舊版語言服務中的導覽列的支援 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdac288755ca02face6f3422e2da0c78629e2905
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56604026"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>舊版語言服務中對巡覽列的支援
導覽列頂端的 [編輯器] 檢視會顯示檔案中的類型和成員。 左側下拉式清單中，會顯示類型和成員會顯示在右側下拉式清單。 當使用者選取的型別時，插入號會放在類型的第一行中。 當使用者選取的成員時，則會將插入號放在成員的定義。 下拉式清單方塊會更新以反映目前的插入號位置。

## <a name="displaying-and-updating-the-navigation-bar"></a>顯示和更新的導覽列
 若要支援的瀏覽列，您必須衍生的類別<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>類別，並實作<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法。 當您的語言服務會提供程式碼視窗中，基底<xref:Microsoft.VisualStudio.Package.LanguageService>類別會具現化<xref:Microsoft.VisualStudio.Package.CodeWindowManager>，其中包含<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>物件，表示程式碼視窗。 <xref:Microsoft.VisualStudio.Package.CodeWindowManager>物件則指定新<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>物件。 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>方法取得<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>物件。 如果您傳回的執行個體您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>類別，<xref:Microsoft.VisualStudio.Package.CodeWindowManager>呼叫您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法填入內部列出，並傳遞您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>物件[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]manager 列的下拉式清單。 下拉式清單列管理員 中，接著呼叫<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>方法，在您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>物件來建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>物件，包含兩個下拉式清單列。

 當插入號移時，請<xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A>方法呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>方法。 基底<xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>方法呼叫<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法，在您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>類別來更新導覽列的狀態。 您傳遞一組<xref:Microsoft.VisualStudio.Package.DropDownMember>至這個方法的物件。 每個物件代表下拉式清單中的項目。

## <a name="the-contents-of-the-navigation-bar"></a>瀏覽列的內容
 瀏覽列通常包含一份類型和成員的清單。 型別的清單會包含在目前的原始程式檔中可用的所有類型。 類型名稱中包含完整的命名空間資訊。 以下是使用兩種類型的 C# 程式碼範例：

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

 [成員] 清單會顯示在 [類型] 清單中選取的類型可用成員。 如果使用上述程式碼範例`TestLanguagePackage.TestLanguageService`是型別，已選取 [成員] 清單會包含私用成員`tokens`和`serviceName`。 內部結構`Token`則不會顯示。

 您可以實作讓成員的名稱變成粗體，插入號放置於它時的 [成員] 清單。 成員也可以顯示在灰色文字表示，則這些不目前所在的插入號範圍內。

## <a name="enabling-support-for-the-navigation-bar"></a>啟用導覽列的支援
 若要啟用導覽列的支援，您必須設定`ShowDropdownBarOption`的參數<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>屬性設定為`true`。 這個參數會設定 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> 屬性。 若要支援的瀏覽列，您必須實作<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>中的物件<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>方法<xref:Microsoft.VisualStudio.Package.LanguageService>類別。

 在您實作<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>方法，如果<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>屬性設定為`true`，，您可以傳回<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>物件。 如果您不會傳回物件，不會顯示巡覽列。

 使用者可以設定選項，以顯示 巡覽列，因此可以在編輯器檢視中開啟時重設此控制項。 使用者必須關閉再重新開啟 [編輯器] 視窗，才能在變更生效。

## <a name="implementing-support-for-the-navigation-bar"></a>實作在導覽列的支援
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法會採用兩個清單 （一個用於每個下拉式清單） 和兩個值，表示目前的選取範圍，每個清單中。 清單和選取項目值可以更新，在此情況下<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法必須傳回`true`表示清單已變更。

 選取變更類型下拉式清單中，[成員] 清單必須更新以反映新的類型。 在 [成員] 清單中顯示的內容可以是：

- 目前型別的成員清單。

- 中的所有成員可用的來源檔案，但與不在目前的型別中的所有成員，以灰色文字顯示。 使用者仍然可以選取灰色成員 中，因此可用於快速導覽，但色彩表示它們不是目前所選類型的組件。

  實作<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法通常會執行下列步驟：

1.  取得原始程式檔的目前宣告的清單。

     有數種方法來填入清單。 其中一個方法是在您的版本上建立自訂的方法<xref:Microsoft.VisualStudio.Package.LanguageService>呼叫的類別<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法會傳回一份所有宣告的自訂剖析原因。 另一種方法可能會呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法，直接從<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>，原因為自訂的剖析方法。 第三種方法可能會快取中的宣告<xref:Microsoft.VisualStudio.Package.AuthoringScope>中的最後一個完整剖析作業所傳回的類別<xref:Microsoft.VisualStudio.Package.LanguageService>類別，並擷取與<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法。

2.  填入或更新的類型清單。

     [類型] 清單的內容可能會更新來源已變更時，或您已選擇要變更文字樣式，根據目前的插入號位置的類型。 請注意，此位置會傳遞至<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法。

3.  決定要在目前插入號位置為基礎的 [類型] 清單中選取的型別。

     您可以在步驟 1，以尋找類型封入目前的插入號位置，搜尋所取得的宣告，然後搜尋 [類型] 清單中的該類型以判斷其索引至類型清單。

4.  填入或更新所選類型的所有成員的清單。

     [成員] 清單會反映目前顯示之內容**成員**下拉式清單。 [成員] 清單的內容可能需要更新來源已變更，或如果您要顯示所選類型的成員，而選取的類型變更。 如果您選擇要顯示所有成員的原始程式檔中，文字樣式的清單中的每個成員必須更新目前選取的型別已變更。

5.  決定要在目前插入號位置為基礎的 [成員] 清單中選取的成員。

     在步驟 1 中的成員，其中包含目前的插入號位置，搜尋所取得的宣告，然後搜尋 [成員] 清單，該成員以判斷其索引至成員清單。

6.  傳回`true`如果您已為清單或任一個清單中的選取項目做任何變更。