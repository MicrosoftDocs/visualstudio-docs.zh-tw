---
title: 在舊版語言服務中的註解程式碼 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b573b464c26c3864cece697191cf03545ada779
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128716"
---
# <a name="commenting-code-in-a-legacy-language-service"></a>在舊版語言服務中的註解程式碼
程式設計語言通常會提供註解或註解的程式碼的方法。 註解是一段文字，提供程式碼的其他資訊，但會忽略期間編譯或解譯。  
  
 Managed 的封裝架構 (MPF) 類別提供註解和取消選取的文字支援。  
  
## <a name="comment-styles"></a>註解樣式  
 有兩種一般的樣式的註解：  
  
1.  行註解，請以單行註解的所在。  
  
2.  區塊註解，也就是註解可能包含多行。  
  
 行註解通常有起始的字元 （或字元），同時區塊註解有開頭和結尾字元。 例如，在 C# 中，行註解開頭 / /，並加以啟動區塊註解 / *，以結束\*/。  
  
 當使用者選取命令**註解選取範圍**從**編輯** -> **進階**功能表上，此命令路由至<xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A>方法<xref:Microsoft.VisualStudio.Package.Source>類別。 當使用者選取命令**取消註解選取範圍**，命令路由至<xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A>方法。  
  
## <a name="supporting-code-comments"></a>支援的程式碼註解  
 您可以讓您的語言服務支援的程式碼的註解藉由`EnableCommenting`具名參數的<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>。 這會設定<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A>屬性<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別。 如需有關如何設定語言 servicce 功能的詳細資訊，請參閱[註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md))。  
  
 您也必須覆寫<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>方法以傳回<xref:Microsoft.VisualStudio.Package.CommentInfo>結構取代為您的語言的註解字元。 C#-樣式行註解字元都是預設值。  
  
### <a name="example"></a>範例  
 以下是範例實作<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>方法。  
  
```csharp  
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
  
## <a name="see-also"></a>另請參閱  
 [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)