---
title: 舊版語言服務中的大綱 |Microsoft Docs
description: 瞭解如何支援在舊版語言服務中執行隱藏區域的大綱。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a56d755341aa611f0e2762f6bae8940778fe0864
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062950"
---
# <a name="outlining-in-a-legacy-language-service"></a>在舊版語言服務中製作大綱
大綱可將複雜的程式折迭到總覽或大綱中。 例如，在 c # 中，所有方法都可以折迭成單一行，只顯示方法簽章。 此外，您可以將結構和類別折迭，只顯示結構和類別的名稱。 在單一方法中，您可以藉由只顯示第一行的語句（例如、和），折迭複雜邏輯以顯示整體流程 `foreach` `if` `while` 。

 舊版語言服務會實作為 VSPackage 的一部分，但是執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解，請參閱 [逐步解說：大綱](../../extensibility/walkthrough-outlining.md)。

> [!NOTE]
> 建議您儘快開始使用新的編輯器 API。 這可改善您的語言服務效能，並讓您利用新的編輯器功能。

## <a name="enabling-support-for-outlining"></a>啟用大綱支援
 `AutoOutlining`登錄專案會設定為1，以啟用自動大綱。 自動大綱會在載入或變更檔案時，設定整個來源的剖析，以便識別隱藏的區域並顯示大綱字元。 大綱也可以由使用者手動控制。

 您 `AutoOutlining` 可以透過類別上的屬性來取得登錄專案的值 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 。 您 `AutoOutlining` 可以使用屬性的具名引數來初始化登錄專案 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> (如需詳細資訊) ，請參閱 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md) 。

## <a name="the-hidden-region"></a>隱藏的區域
 若要提供大綱，您的語言服務必須支援隱藏區域。 這些是可展開或折迭的文字範圍。 隱藏的區域可以用標準語言符號來分隔，例如大括弧或自訂符號。 例如，c # 具有 `#region` / `#endregion` 分隔隱藏區域的配對。

 隱藏的區域是由隱藏的區域管理員所管理，它會公開為 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 介面。

 大綱會使用隱藏區域 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> 介面並包含隱藏區域的範圍、目前的可見狀態，以及在範圍折迭時要顯示的橫幅。

 語言服務剖析器會使用 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> 方法，以隱藏區域的預設行為來新增隱藏的區域，而此 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> 方法可讓您自訂大綱的外觀和行為。 一旦將隱藏的區域提供給隱藏的區域會話，就會 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 管理語言服務的隱藏區域。

 如果您需要判斷隱藏區域會話的終結時間，隱藏的區域會變更，或者您需要確定可以看見特定的隱藏區域;您必須從類別衍生類別， <xref:Microsoft.VisualStudio.Package.Source> 並分別覆寫適當的方法：、 <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A> <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> 和 <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A> 。

### <a name="example"></a>範例
 以下是針對所有成對大括弧建立隱藏區域的簡化範例。 假設語言提供括弧對稱，而且要比對的括弧至少包含大括弧 ( {和} ) 。 這種方法僅供說明之用。 完整的實作為中的案例完整處理 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 。 此範例也會示範如何將喜好設定設 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> 為 `true` 暫時。 替代方法是在 `AutoOutlining` 您的語言套件中指定屬性中的具名引數 `ProvideLanguageServiceAttribute` 。

 這個範例會假設 c # 規則適用于批註、字串和常值。

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
