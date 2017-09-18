---
title: "在舊版語言服務中的註解程式碼 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "註解支援的語言服務 [受管理的封裝 framework]"
  - "註解程式碼的語言服務 [受管理的封裝 framework]"
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 在舊版語言服務中的註解程式碼
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

程式語言通常會提供一種方法來加註或註解的程式碼。  註解是一段文字所提供的程式碼的其他資訊，但在編譯或解譯期間會被忽略。  
  
 受管理的套件的架構 \(MPF\) 類別會提供註解和 uncommenting 的選取文字中的支援。  
  
## 註解樣式  
 有兩種一般註解樣式：  
  
1.  內嵌註解，註解是在同一行的位置。  
  
2.  區塊註解，註解可能包含多行的位置。  
  
 內嵌註解通常會有一個開始字元 \(或字元\)，區塊註解時有開始和結束的字元。  比方說，在 C\# 行註解開頭 \/ \/，以及區塊註解開頭為 \/ \*，並結束 \* \/。  
  
 當使用者選取命令**註解選取範圍** 的 **編輯** \-\>  **進階** \] 功能表中，命令會路由傳送到<xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A>上的方法<xref:Microsoft.VisualStudio.Package.Source>類別。  當使用者選取命令**取消註解選取項目**，命令會路由至<xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A>方法。  
  
## 支援的程式碼註解  
 您可以讓您語言服務支援的程式碼意見的`EnableCommenting`的參數名稱<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 。  這會將<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A>屬性的<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別。  如需有關如何設定語言 servicce 功能的詳細資訊，請參閱[註冊語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)\)。  
  
 您也必須覆寫<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>方法來傳回<xref:Microsoft.VisualStudio.Package.CommentInfo>結構，與您的語言的註解字元。  C\#\-樣式行註解字元是預設值。  
  
### 範例  
 以下是項目的實作範例<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>方法。  
  
```c#  
using Microsoft.VisualStudio.Package;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override CommentInfo GetCommentFormat() {  
            CommentInfo info = new CommentInfo();  
            info.LineStart       = "//";  
            info.BlockStart      = "/*";  
            info.BlockEnd        = "*/";  
            info.UseLineComments = true;  
            return info;  
        }  
    }  
}  
```  
  
## 請參閱  
 [舊版的語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [註冊語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)