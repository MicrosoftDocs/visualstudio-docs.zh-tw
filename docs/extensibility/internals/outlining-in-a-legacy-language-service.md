---
title: 在傳統語言服務中概述 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be485a0e7406d49c4dcce77958c720e0b62504b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706816"
---
# <a name="outlining-in-a-legacy-language-service"></a>在舊版語言服務中製作大綱
大綱使複雜的程序摺疊成概述或大綱成為可能。 例如,在 C# 中,所有方法都可以摺疊到一行,僅顯示方法簽名。 此外,可以摺疊結構和類,僅顯示結構和類的名稱。 在單個方法內,可以通過僅顯示 語句的第一行`foreach`(`if`如`while`、 和)來摺疊複雜邏輯以顯示總體流。

 舊語言服務是作為 VSPackage 的一部分實現的,但實現語言服務功能的較新方法是使用 MEF 擴展。 要瞭解更多資訊,請參閱[演練:概述](../../extensibility/walkthrough-outlining.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將提高語言服務的性能,並允許您利用新的編輯器功能。

## <a name="enabling-support-for-outlining"></a>支援大綱
 註冊表`AutoOutlining`項設置為 1 以啟用自動大綱。 自動大綱在載入或更改檔時設置整個源的解析,以便識別隱藏區域並顯示大綱字形。 大綱也可以由用戶手動控制。

 `AutoOutlining`註冊表項的值可以<xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A><xref:Microsoft.VisualStudio.Package.LanguagePreferences>通過 類上的屬性獲取。 註冊表`AutoOutlining`項可以<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>使用 屬性的命名參數進行初始化(有關詳細資訊,請參閱[註冊舊語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md))。

## <a name="the-hidden-region"></a>隱藏區域
 要提供大綱,您的語言服務必須支援隱藏區域。 這些是可以展開或摺疊的文本範圍。 隱藏區域可以由標準語言符號(如大括弧)或自定義符號分隔。 例如,C#`#region`/`#endregion`具有分隔隱藏區域的對。

 隱藏區域由隱藏區域管理員管理,該管理器作為<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>介面公開。

 大綱使用隱藏區域介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion>,並包含隱藏區域的範圍、當前可見狀態和摺疊時要顯示的橫幅。

 語言服務解析器使用<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A>方法添加具有隱藏區域預設行為的新隱藏區域,<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A>而 該方法允許您自定義大綱的外觀和行為。 將隱藏區域提供給隱藏區域工作階段後,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]管理語言服務的隱藏區域。

 如果需要確定何時銷毀隱藏區域會話,則更改隱藏區域,或者需要確保特定隱藏區域可見;否則,需要確保隱藏區域可見。必須從<xref:Microsoft.VisualStudio.Package.Source>類派生一個類,並分別重寫相應的<xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>方法<xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>、<xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>和。

### <a name="example"></a>範例
 下面是為所有大括弧創建隱藏區域的簡化範例。 假定語言提供大括弧匹配,並且要匹配的大括弧至少包括大括弧 (* 和 *)。 這種方法僅用於說明目的。 全面實施將完全處理<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>中的案例。 此示例還演示如何<xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A>`true`暫時設置首選項。 另一種方法是在語言包`AutoOutlining``ProvideLanguageServiceAttribute`中的屬性中指定命名參數。

 此範例假定註釋、字串和文字的 C# 規則。

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

## <a name="see-also"></a>另請參閱
- [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)
- [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)
