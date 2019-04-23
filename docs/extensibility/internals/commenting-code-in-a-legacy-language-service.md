---
title: 舊版語言服務中的註解程式碼 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c82669ac6d4f32f1525b7e14427ed620a51cfc5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102701"
---
# <a name="comment-code-in-a-legacy-language-service"></a>舊版語言服務中的註解程式碼
程式設計語言通常能用來標註或註解的程式碼。 註解是一段文字，提供程式碼的其他資訊，但會忽略期間編譯或解譯。

 Managed 的封裝架構 (MPF) 類別會提供註解和取消註解選取的文字支援。

## <a name="comment-styles"></a>註解樣式
有兩種一般的樣式的註解：

1. 行註解，以單行註解的所在。

2. 區塊註解，其中註解可能包含多行。

行註解通常會有起始字元 （或字元），在區塊註解時有開頭和結尾字元。 例如，在 C# 中，行註解的開頭`//`，以及區塊註解的開頭`/*`，並結束`*/`。

當使用者選取命令**註解選取範圍**從**編輯** > **進階**功能表中，此命令會路由傳送至<xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A>方法<xref:Microsoft.VisualStudio.Package.Source>類別。 當使用者選取命令**取消註解選取範圍**，此命令會路由傳送至<xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A>方法。

## <a name="support-code-comments"></a>支援程式碼註解
 您可以讓您的語言服務支援的程式碼的註解藉由`EnableCommenting`具名參數的<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>。 這會設定<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A>屬性<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別。 如需有關如何設定語言服務功能的詳細資訊，請參閱 <<c0> [ 註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)。

 您也必須覆寫<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>方法來傳回<xref:Microsoft.VisualStudio.Package.CommentInfo>結構取代為您的語言的註解字元。 C#-樣式行註解字元都是預設值。

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
- [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)
- [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)