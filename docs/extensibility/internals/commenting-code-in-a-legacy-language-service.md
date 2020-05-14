---
title: 在舊語言服務中註釋代碼 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5450199fde29f581dafdf9b2884c88ef26ea4ce7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709430"
---
# <a name="comment-code-in-a-legacy-language-service"></a>舊語言服務中的註解碼
程式設計語言通常提供註釋或註釋代碼的方法。 註釋是文本的一部分,提供有關代碼的其他資訊,但在編譯或解釋過程中被忽略。

 託管包框架 (MPF) 類別支援註解和取消註釋的選定文本。

## <a name="comment-styles"></a>註解樣式
有兩種一般註釋樣式:

1. 行註釋,其中註釋位於單行上。

2. 阻止註釋,其中註釋可能包含多行。

行註釋通常具有起始字元(或字元),而塊註釋具有開頭字元和結束字元。 例如,在 C# 中,行註`//`釋以 開頭,塊`/*`註釋以`*/`開頭,以結尾。

當使用者從 **「編輯** > **進階」** 選單選擇命令 **「註釋選擇**」時,該命令<xref:Microsoft.VisualStudio.Package.Source>將<xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A>路由到類上的方法。 當使用者選擇命令 **「取消註釋選擇」** 時,命令將路<xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A>由到方法。

## <a name="support-code-comments"></a>支援代碼註解
 您可以通過`EnableCommenting`的命名參數來提供語言服務支援代碼註釋<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>。 這會設定<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A>類別的屬性<xref:Microsoft.VisualStudio.Package.LanguagePreferences>。 有關設定語言服務功能的詳細資訊,請參閱[註冊舊語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)。

 還必須重寫<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>方法 以返回具有語言<xref:Microsoft.VisualStudio.Package.CommentInfo>註釋 字元的結構。 C#樣式行註釋字元為預設值。

### <a name="example"></a>範例
 下面是<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>方法的實現示例。

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
- [傳統語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)
- [註冊舊語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)
