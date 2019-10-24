---
title: 舊版語言服務中的大綱 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6b2ba55a2e77a1f7261812a181ad780c2ef2b71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726168"
---
# <a name="outlining-in-a-legacy-language-service"></a>在舊版語言服務中製作大綱
大綱可以將複雜的程式折迭成總覽或大綱。 例如，在所有C#方法中，都可以折迭成單一行，只顯示方法簽章。 此外，結構和類別可以折迭，只顯示結構和類別的名稱。 在單一方法中，複雜邏輯可以折迭，只顯示第一行的語句，例如 `foreach`、`if` 和 `while`，以顯示整體流程。

 舊版語言服務會實作為 VSPackage 的一部分，但執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解，請參閱[逐步解說：大綱](../../extensibility/walkthrough-outlining.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將可改善語言服務的效能，並可讓您利用新的編輯器功能。

## <a name="enabling-support-for-outlining"></a>啟用大綱的支援
 @No__t_0 登錄專案設定為1，以啟用自動大綱。 自動大綱會在載入或變更檔案時，設定整個來源的剖析，以便識別隱藏的區域並顯示大綱圖像。 大綱也可以由使用者手動控制。

 @No__t_0 登錄專案的值可以透過 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 類別上的 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> 屬性取得。 @No__t_0 登錄專案可以使用具名引數初始化 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 屬性（如需詳細資訊，請參閱[註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)）。

## <a name="the-hidden-region"></a>隱藏的區域
 若要提供大綱，您的語言服務必須支援隱藏的區域。 這些是可以展開或折迭的文字範圍。 隱藏的區域可以用標準語言符號（例如大括弧）或自訂符號分隔。 例如， C#具有分隔隱藏區域的 `#region` / `#endregion` 配對。

 隱藏的區域是由隱藏的區域管理員所管理，這會公開為 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 介面。

 大綱：使用隱藏區域的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> 介面，並包含隱藏區域的範圍、目前的可見狀態，以及當範圍折迭時要顯示的橫幅。

 語言服務剖析器會使用 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> 方法，以隱藏區域的預設行為加入新的隱藏區域，而 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> 方法則可讓您自訂外框的外觀和行為。 將隱藏的區域提供給隱藏的區域會話之後，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 管理語言服務的隱藏區域。

 如果您需要判斷隱藏的區域會話何時終結，隱藏的區域也會變更，或您必須確定可以看見特定的隱藏區域;您必須從 <xref:Microsoft.VisualStudio.Package.Source> 類別衍生類別，並分別覆寫適當的方法、<xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>、<xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> 和 <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>。

### <a name="example"></a>範例
 以下是針對所有成對大括弧建立隱藏區域的簡化範例。 假設語言提供括弧對稱，而且要比對的大括弧包含至少大括弧（{和}）。 這個方法僅供說明之用。 完整的執行功能會在 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 中完整處理案例。 這個範例也會示範如何將 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> 喜好設定設為暫時 `true`。 另一個替代方式是在語言套件的 `ProvideLanguageServiceAttribute` 屬性中指定名為 `AutoOutlining` 的參數。

 這個範例會C#假設批註、字串和常值的規則。

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{

    public class MyLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences  GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(MyLanguageService).GUID,
                                                        Name);
                m_preferences.Init();
                // Temporarily enabled auto-outlining
                m_preferences.AutoOutlining = true;
            }
            return m_preferences;
        }

        public override AuthoringScope  ParseSource(ParseRequest req)
        {
            Source source = (Source) this.GetSource(req.FileName);
            switch (req.Reason)
            {
               case ParseReason.HighlightBraces:
               case ParseReason.MatchBraces:
               case ParseReason.MemberSelectAndHighlightBraces:
                  if (source.Braces != null)
                  {
                      foreach (TextSpan[] brace in source.Braces)
                      {
                         if (brace.Length == 2)
                         {
                             if (req.Sink.HiddenRegions == true
                                   && source.GetText(brace[0]).Equals("{")
                                   && source.GetText(brace[1]).Equals("}"))
                             {
                                //construct a TextSpan of everything between the braces
                                TextSpan hideSpan = new TextSpan();
                                hideSpan.iStartIndex = brace[0].iStartIndex;
                                hideSpan.iStartLine = brace[0].iStartLine;
                                hideSpan.iEndIndex = brace[1].iEndIndex;
                                hideSpan.iEndLine = brace[1].iEndLine;
                                req.Sink.ProcessHiddenRegions = true;
                                req.Sink.AddHiddenRegion(hideSpan);
                             }
                             req.Sink.MatchPair(brace[0], brace[1], 1);
                         }
                         else if (brace.Length >= 3)
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);
                  }
        }
                   break;
               default:
                   break;
      }
            // Must always return a valid AuthoringScope object.
            return new MyAuthoringScope();
        }
    }
}
```

## <a name="see-also"></a>請參閱
- [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)
- [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)