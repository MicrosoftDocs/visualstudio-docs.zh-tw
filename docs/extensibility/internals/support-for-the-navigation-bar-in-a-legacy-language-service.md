---
title: 舊版語言服務中的支援巡覽列
description: 瞭解如何在舊版語言服務中支援巡覽列。 編輯器視圖中的導覽列會顯示檔案中的類型和成員。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 325789c3b7210c87d5c1b0414434af27c266c31c
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876538"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>舊版語言服務中對巡覽列的支援
編輯器視圖頂端的巡覽列會顯示檔案中的類型和成員。 類型會顯示在左側下拉式清單中，而成員會顯示在右邊的下拉式清單中。 當使用者選取型別時，會將插入號放在型別的第一行。 當使用者選取成員時，會將插入號放在成員的定義上。 下拉式方塊會更新，以反映插入號的目前位置。

## <a name="displaying-and-updating-the-navigation-bar"></a>顯示和更新巡覽列
 若要支援巡覽列，您必須從類別衍生類別 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> ，並執行 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 方法。 當您的語言服務指定程式碼視窗時，基類會具現 <xref:Microsoft.VisualStudio.Package.LanguageService> 化 <xref:Microsoft.VisualStudio.Package.CodeWindowManager> ，其中包含 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 代表程式碼視窗的物件。 <xref:Microsoft.VisualStudio.Package.CodeWindowManager>接著會為物件提供新的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 物件。 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>方法會取得 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 物件。 如果您 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 傳回類別的實例，則會 <xref:Microsoft.VisualStudio.Package.CodeWindowManager> 呼叫您的 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 方法以填入內部清單，並將您的 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 物件傳遞至下拉式清單 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 管理員。 下拉式清單管理員接著會在 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> 您的物件上呼叫方法， <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 以建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> 包含兩個下拉式列的物件。

 當插入點移動時， <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> 方法會呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> 方法。 基底 <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> 方法會呼叫 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 您類別中的方法 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> ，以更新巡覽列的狀態。 您會將一組 <xref:Microsoft.VisualStudio.Package.DropDownMember> 物件傳遞給這個方法。 每個物件都代表下拉式清單中的一個專案。

## <a name="the-contents-of-the-navigation-bar"></a>巡覽列的內容
 導覽列通常會包含類型清單和成員清單。 類型清單包含目前原始程式檔中的所有可用類型。 型別名稱包含完整的命名空間資訊。 以下是具有兩種類型的 c # 程式碼範例：

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

 [類型] 清單會顯示 `TestLanguagePackage.TestLanguageService` 和 `TestLanguagePackage.TestLanguageService.Tokens` 。

 [成員] 清單會顯示 [類型] 清單中所選取之類型的可用成員。 使用上述的程式碼範例，如果 `TestLanguagePackage.TestLanguageService` 是已選取的類型，成員清單將包含私用成員 `tokens` 和 `serviceName` 。 內部結構 `Token` 不會顯示。

 您可以在將插入點放在其內部時，執行成員清單以將成員的名稱設為粗體。 成員也可以顯示成灰色的文字，表示它們不在插入點目前位置的範圍內。

## <a name="enabling-support-for-the-navigation-bar"></a>啟用巡覽列的支援
 若要啟用對巡覽列的支援，您必須將 `ShowDropdownBarOption` 屬性的參數設定 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 為 `true` 。 這個參數會設定 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> 屬性。 若要支援巡覽列，您必須 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 在類別的方法中執行物件 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> 。

 在方法的執行中 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> ，如果 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> 屬性設定為 `true` ，您可以傳回 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 物件。 如果您沒有傳回物件，則不會顯示巡覽列。

 使用者可以設定顯示巡覽列的選項，因此當編輯器視圖開啟時，可能會重設這個控制項。 使用者必須先關閉再重新開啟編輯器視窗，變更才會發生。

## <a name="implementing-support-for-the-navigation-bar"></a>執行巡覽列的支援
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法會採用兩個清單 (每一個下拉式) 各有一個，而兩個值代表每個清單中目前的選取範圍。 您可以更新清單和選取的值，在此情況下，此 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 方法必須傳回 `true` 以表示清單已變更。

 當 [類型] 下拉式清單中的選取專案變更時，必須更新 [成員] 清單，以反映新的類型。 [成員] 清單中顯示的內容可以是：

- 目前類型的成員清單。

- 來源檔案中的所有成員都可以使用，但所有成員都不在目前的類型中，會顯示為灰色文字。 使用者仍然可以選取灰色的成員，讓他們可以用來進行快速流覽，但色彩表示這些成員不屬於目前選取的類型。

  <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法的執行通常會執行下列步驟：

1. 取得原始程式檔的目前宣告清單。

     有幾種方式可填入清單。 其中一個方法是在您的類別版本上建立自訂方法 <xref:Microsoft.VisualStudio.Package.LanguageService> ，此方法會呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法，並使用會傳回所有宣告清單的自訂剖析原因。 另一種方法可能是 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 使用自訂剖析原因，直接從方法呼叫方法。 第三種方法可能是快取 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 類別中最後一次完整剖析作業所傳回之類別中的宣告 <xref:Microsoft.VisualStudio.Package.LanguageService> ，並從方法中取出 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 。

2. 填入或更新類型清單。

     當來源變更時，或您已根據目前的插入號位置選擇變更類型的文字樣式時，可能會更新類型清單的內容。 請注意，此位置會傳遞至 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 方法。

3. 根據目前的插入號位置，判斷要在類型清單中選取的類型。

     您可以搜尋步驟1中取得的宣告，以找出包含目前插入號位置的型別，然後搜尋該型別的型別清單，以判斷其在 [類型] 清單中的索引。

4. 根據選取的類型填入或更新成員清單。

     [成員] 清單會反映目前顯示在 [ **成員** ] 下拉式清單中的內容。 如果來源已變更，或您只顯示所選類型的成員，而且選取的類型已變更，則可能需要更新成員清單的內容。 如果您選擇顯示原始程式檔中的所有成員，則在目前選取的類型變更時，清單中每個成員的文字樣式必須更新。

5. 根據目前的插入號位置，判斷要在成員清單中選取的成員。

     在步驟1中，搜尋包含目前插入號位置的成員所取得的宣告，然後搜尋成員清單中的成員清單，以判斷其在成員清單中的索引。

6. `true`如果已對清單或任一清單中的選取專案進行任何變更，則傳回。
