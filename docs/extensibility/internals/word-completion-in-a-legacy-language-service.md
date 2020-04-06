---
title: 傳統語言服務中的字完成 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 948751cde5b6b710d911a30ca26a61e5411bba4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703168"
---
# <a name="word-completion-in-a-legacy-language-service"></a>舊版語言服務中的文字自動完成
單詞完成將填充部分鍵入的單詞上缺少的字元。 如果只有一個可能的完成,則輸入完成字元時,該單詞將完成。 如果部分單詞與多個可能性匹配,將顯示可能完成的清單。 完成字元可以是不用於標識符的任何字元。

 舊語言服務是作為 VSPackage 的一部分實現的,但實現語言服務功能的較新方法是使用 MEF 擴展。 要瞭解更多資訊,請參閱[延伸編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將提高語言服務的性能,並允許您利用新的編輯器功能。

## <a name="implementation-steps"></a>實施步驟

1. 當使用者從 **「IntelliSense」** 選單中選擇 **「完整字」** 時,<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>該命令將發送到語言服務。

2. 類別<xref:Microsoft.VisualStudio.Package.ViewFilter>擷取指令,用的解析<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>原因呼叫<xref:Microsoft.VisualStudio.Package.ParseReason>方法 。

3. 然後<xref:Microsoft.VisualStudio.Package.Source>,<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>類別調用 方法獲取可能的單詞完成的清單,然後<xref:Microsoft.VisualStudio.Package.CompletionSet>使用類在工具提示清單中顯示單詞。

    如果只有一個匹配的單詞,則<xref:Microsoft.VisualStudio.Package.Source>類將完成該單詞。

   或者,如果掃描程式在鍵入標識符的第<xref:Microsoft.VisualStudio.Package.TokenTriggers>一個字元時返回觸發器值<xref:Microsoft.VisualStudio.Package.Source>, 則類將檢測此值,並調<xref:Microsoft.VisualStudio.Package.Source.Completion%2A><xref:Microsoft.VisualStudio.Package.ParseReason>用 具有的解析原因的方法。 在這種情況下,解析器必須檢測成員選擇字元的存在並提供成員清單。

## <a name="enabling-support-for-the-complete-word"></a>開啟對完整字的支援
 要啟用對單詞完成的支援,將`CodeSense`命名參數傳遞給與語言<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>包關聯的使用者屬性。 這將在<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>類上<xref:Microsoft.VisualStudio.Package.LanguagePreferences>設置屬性。

 解析器必須返回聲明清單以回應解析原因值<xref:Microsoft.VisualStudio.Package.ParseReason>,以便單詞完成才能操作。

## <a name="implementing-complete-word-in-the-parsesource-method"></a>ParseSource 方法中完整單字
 對於單詞完成,<xref:Microsoft.VisualStudio.Package.Source>類別的<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A><xref:Microsoft.VisualStudio.Package.AuthoringScope>單字比類別的清單。 必須在派生自類的<xref:Microsoft.VisualStudio.Package.Declarations>類中實現該清單。 有關必須<xref:Microsoft.VisualStudio.Package.Declarations>實現的方法的詳細資訊,請參閱 該類。

 如果清單僅包含一個單詞,則<xref:Microsoft.VisualStudio.Package.Source>類會自動插入該單詞以代替部分單詞。 如果清單包含多個單詞,則<xref:Microsoft.VisualStudio.Package.Source>類將顯示一個工具提示列表,用戶可以從中選擇適當的選項。

 還要查看<xref:Microsoft.VisualStudio.Package.Declarations>[舊語言服務中成員完成中的](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)類實現示例。
