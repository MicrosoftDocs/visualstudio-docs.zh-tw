---
title: 在舊版語言服務中將程式碼批註化 |Microsoft Docs
description: 瞭解 managed package framework (MPF) 類別，在 Visual Studio 中提供舊版語言服務的程式碼批註支援。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c712f1458aa182abcf9e10bee6c6cf90e11b194d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057100"
---
# <a name="comment-code-in-a-legacy-language-service"></a>舊版語言服務中的批註碼
程式設計語言通常會提供批註或批註程式碼的方法。 批註是一段文字，可提供程式碼的其他相關資訊，但會在編譯或轉譯期間遭到忽略。

 受控封裝架構 (MPF) 類別可支援批註和取消批註選取的文字。

## <a name="comment-styles"></a>批註樣式
批註的一般樣式有兩種：

1. 行批註，其中批註是在同一行。

2. 封鎖批註，其中批註可以包含多行。

行批註通常會有起始字元 (或字元) ，同時封鎖批註同時具有開頭和結尾字元。 例如，在 c # 中，行批註的開頭為 `//` ，而且區塊批註的開頭為， `/*` 結尾為 `*/` 。

當使用者從 [**編輯**] 功能表中選取命令 **批註選取專案** 時  >   ，此命令會路由至 <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> 類別上的方法 <xref:Microsoft.VisualStudio.Package.Source> 。 當使用者選取 **取消選取** 命令的命令時，會將命令路由傳送至 <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> 方法。

## <a name="support-code-comments"></a>支援程式碼批註
 您可以透過的具名引數，讓您的語言服務支援程式碼批註 `EnableCommenting` <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 。 這會設定 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> 類別的屬性 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 。 如需設定 language service 功能的詳細資訊，請參閱 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)。

 您也必須覆寫 <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> 方法，以傳回 <xref:Microsoft.VisualStudio.Package.CommentInfo> 具有您語言批註字元的結構。 C # 樣式的行批註字元是預設值。

### <a name="example"></a>範例
 以下是方法的範例執行 <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> 。

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
