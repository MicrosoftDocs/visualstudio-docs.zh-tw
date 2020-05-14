---
title: 支援舊語言服務中的導航列 |微軟文件
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
ms.openlocfilehash: f86dabb0594b1e33c45808efb387fcbe313e3de3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704855"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>舊版語言服務中對巡覽列的支援
編輯器檢視頂部的導航列顯示檔中的類型和成員。 類型顯示在左側下拉清單中,成員顯示在右側下拉清單中。 當使用者選擇類型時,care將放置在類型的第一行上。 當用戶選擇成員時,該 care 被放置在成員的定義上。 下拉框將更新以反映 caret 的當前位置。

## <a name="displaying-and-updating-the-navigation-bar"></a>顯示及更新導覽列
 要支持導航欄,必須從<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>類派生一個類並實現<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法。 為語言服務提供代碼視窗時,基<xref:Microsoft.VisualStudio.Package.LanguageService>類實<xref:Microsoft.VisualStudio.Package.CodeWindowManager>例化 ,其中包含表示<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>代碼視窗的物件。 然後<xref:Microsoft.VisualStudio.Package.CodeWindowManager>為物件指定一個<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>新 物件。 該方法<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>取得<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>物件 。 如果返回類<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars><xref:Microsoft.VisualStudio.Package.CodeWindowManager>的實例,則調用<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法 以填充內部<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>清單並將[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件傳遞給 下拉欄管理器。 下拉欄管理器反過來調用<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A><xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>物件上的方法以建立保存兩個下拉<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>欄 的物件。

 當 care 行動<xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A>時, 該<xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>方法呼叫方法。 基<xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>方法調<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A><xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>用 類中的方法以更新導航欄的狀態。 將一組<xref:Microsoft.VisualStudio.Package.DropDownMember>物件傳遞給此方法。 每個物件表示下拉清單中的條目。

## <a name="the-contents-of-the-navigation-bar"></a>導覽列的內容
 導覽列通常包含類型列表和成員清單。 類型清單包括目前源檔案中可用的所有類型。 類型名稱包括完整的命名空間資訊。 下面是具有兩種類型的 C# 代碼的範例:

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

 型態清單會`TestLanguagePackage.TestLanguageService`顯示`TestLanguagePackage.TestLanguageService.Tokens`與 。

 成員清單顯示類型清單中選擇的類型的可用成員。 使用上面的代碼範例,如果`TestLanguagePackage.TestLanguageService`選擇類型,成員清單會包含私有成員`tokens`與`serviceName`。 不顯示內部`Token`結構。

 您可以實現成員清單,使成員的名稱加粗,當該卡托放在其中時。 成員也可以以灰顯的文本顯示,指示它們不在當前位置的作用域內。

## <a name="enabling-support-for-the-navigation-bar"></a>開啟導覽列支援
 要啟用對導覽列的支援,必須將屬性`ShowDropdownBarOption`<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>的 參數`true`設定為 。 這個參數會設定 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> 屬性。 要支持導航欄,必須在<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars><xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A><xref:Microsoft.VisualStudio.Package.LanguageService>類上的方法中實現物件。

 在 方法的<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>實現 中<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>,如果`true`屬性設置為<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>,則可以返回 物件。 如果不返回物件,則不顯示導航欄。

 用戶可以設置顯示導航欄的選項,因此可以在編輯器檢視打開時重置此控制項。 在進行更改之前,用戶必須關閉並重新打開編輯器視窗。

## <a name="implementing-support-for-the-navigation-bar"></a>實作對導航列
 該方法<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>採用兩個清單(每個下拉清單一個)和兩個值,表示每個清單中的當前選擇。 可以更新清單和選擇值,在這種情況下,<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法必須`true`返回 以指示清單已更改。

 隨著類型下拉清單中的選擇更改,必須更新成員清單以反映新類型。 成員清單中顯示的內容可以是:

- 當前類型的成員清單。

- 源檔中的所有成員都可用,但所有成員不是以灰化文本顯示的當前類型。 使用者仍可以選擇灰顯成員,以便它們可用於快速導航,但顏色表示它們不是當前所選類型的一部分。

  <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>該方法的實現通常執行以下步驟:

1. 取得來源檔案的目前的聲明清單。

     填充清單的方法有很多種。 一種方法是在<xref:Microsoft.VisualStudio.Package.LanguageService>類的版本中創建一個自定義方法,該方法使用返回所有<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>聲明 清單的自定義解析原因調用該方法。 另一種方法可能是直接從具有自定義<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>解析<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>原因 的方法調用 方法。 第三種方法可能是緩存<xref:Microsoft.VisualStudio.Package.AuthoringScope><xref:Microsoft.VisualStudio.Package.LanguageService>類中最後一個完整分析操作返回的類中的聲明,並從<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法中 檢索該聲明。

2. 填充或更新類型清單。

     類型清單的內容可能會在源更改或您選擇根據當前位置更改類型的文本樣式時更新。 請注意,此位置將傳遞給<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法。

3. 根據目前位置確定要在類型清單中選擇的類型。

     您可以搜尋步驟 1 中獲得的聲明,以查找包含當前 caret 位置的類型,然後搜尋該類型的類型清單以確定其索引到類型清單中。

4. 根據選取類型填充或更新成員清單。

     成員清單反映 **「成員**」下拉清單中當前顯示的內容。 如果源已更改或僅顯示所選類型的成員且所選類型已更改,則可能需要更新成員清單的內容。 如果選擇顯示源檔中的所有成員,則需要更新清單中每個成員的文本樣式(如果當前選擇的類型已更改)。

5. 根據當前關注位置確定要在成員清單中選擇的成員。

     在步驟 1 中獲取的聲明查找包含當前關注位置的成員,然後搜尋成員清單以查找該成員以確定其索引到成員清單中。

6. 如果`true`對清單或任一列表中的選擇進行了任何更改,則返回。
