---
title: "舊版語言服務中的大綱 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "大綱"
  - "大綱的語言服務 [受管理的封裝 framework]"
  - "大綱、 支援的語言服務 [受管理的封裝 framework]"
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 舊版語言服務中的大綱
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

大綱可以摺疊成外框或概觀的複雜的程式。 例如，C\# 中的所有方法可摺都疊至單一行，顯示方法簽章。 此外，結構和類別可摺疊以顯示結構和類別的名稱。 在單一方法中，複雜的邏輯可摺疊來顯示這類的陳述式的第一行顯示的整體流程 `foreach`, ，`if`, ，和 `while`。  
  
 舊版的語言服務會實作成，VSPackage 的一部分，但實作語言服務功能的較新的方法是使用 MEF 延伸模組。 若要深入了解，請參閱 [逐步解說: 大綱](../../extensibility/walkthrough-outlining.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會改善語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## 啟用支援的大綱  
 `AutoOutlining` 登錄項目設為 1 以啟用自動大綱。 自動大綱設定剖析整個來源的檔案載入或變動，以便能夠找出隱藏的區域，並顯示大綱的圖像 （glyph） 時。 大綱也可以控制手動使用者。  
  
 值 `AutoOutlining` 登錄項目可透過 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> 屬性 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 類別。`AutoOutlining` 登錄項目可以使用具名參數，以初始化 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 屬性 \(請參閱 [註冊語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md) 如需詳細資訊\)。  
  
## 隱藏的區域  
 若要提供大綱，語言服務必須支援隱藏的區域。 這些是可以展開或摺疊文字的範圍。 標準語言的符號，例如大括號，或自訂的符號來分隔隱藏的區域。 例如，C\# 有 `#region`\/`#endregion` 組，用來分隔的隱藏的區域。  
  
 隱藏的區域由為隱藏的區域經理，公開為 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 介面。  
  
 大綱使用隱藏的區域 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> 介面，並包含隱藏的區域、 目前的可見狀態和範圍已摺疊時顯示的橫幅的範圍。  
  
 語言服務剖析器會使用 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> 方法來加入新的隱藏的區域，以隱藏的區域的預設行為時 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> 方法可讓您自訂的外觀和行為的外框。 隱藏的區域會提供給隱藏的區域工作階段中，一旦 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 管理語言服務的隱藏的區域。  
  
 如果您需要判斷終結的隱藏的區域工作階段時，隱藏的區域變更，或者您需要確定特定的隱藏的區域是可見的。您必須衍生自 <xref:Microsoft.VisualStudio.Package.Source> 類別並覆寫適當的方法， <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, ，<xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, ，和 <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, 分別。  
  
### 範例  
 以下是建立所有的大括號配對的隱藏的區域的簡化的範例。 假設的語言提供括號對稱，而且要比對括號至少包含大括號 （{和}）。 這個方法是僅供示範用途。 完整的實作會有完整的處理中的案例 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>。 這個範例也示範如何設定 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> 喜好設定給 `true` 暫時。 另一個方法是指定 `AutoOutlining` 具名參數在 `ProvideLanguageServiceAttribute` 語言套件中的屬性。  
  
 這個範例假設 C\# 註解、 字串和常值的規則。  
  
```c#  
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
  
## 請參閱  
 [舊版的語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [註冊語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)