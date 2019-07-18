---
title: 舊版語言服務中字完成 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26495f909d815b32ff8a75c2529ba30eabf3b5c8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309717"
---
# <a name="word-completion-in-a-legacy-language-service"></a>舊版語言服務中的文字自動完成
文字自動完成會填入遺漏的字元，在部分輸入的字組。 如果只有一個可能的完成，這個字被完成時完成輸入的字元是。 如果部分文字比對一個以上的可能性，會顯示可能的完成清單。 完成字元可以是任何字元，不會用於識別項。

 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新的方式是使用 MEF 擴充功能。 若要深入了解，請參閱[擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。

> [!NOTE]
> 我們建議您開始使用新的編輯器 API 盡。 這會改善您的語言服務的效能，並可讓您充分利用新編輯器功能。

## <a name="implementation-steps"></a>實作步驟

1. 當使用者選取**自動完成文字**從**IntelliSense**功能表上，<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>命令傳送到語言服務。

2. <xref:Microsoft.VisualStudio.Package.ViewFilter>類別會攔截命令，並呼叫<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>方法的剖析原因<xref:Microsoft.VisualStudio.Package.ParseReason>。

3. <xref:Microsoft.VisualStudio.Package.Source>類別接著會呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法，以取得可能的字組自動完成，然後顯示工具提示中的字詞清單使用的清單<xref:Microsoft.VisualStudio.Package.CompletionSet>類別。

    如果只有一個符合的文字，<xref:Microsoft.VisualStudio.Package.Source>類別完成這個字。

   或者，如果掃描器傳回觸發程序值<xref:Microsoft.VisualStudio.Package.TokenTriggers>識別項的第一個字元輸入時，<xref:Microsoft.VisualStudio.Package.Source>偵測到此類別，並呼叫<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>方法的剖析原因<xref:Microsoft.VisualStudio.Package.ParseReason>。 在此情況下，剖析器必須偵測存在的成員選取範圍的字元，並提供成員的清單。

## <a name="enabling-support-for-the-complete-word"></a>啟用完整單字的支援
 若要啟用 word 完成集合的支援`CodeSense`名為參數傳遞至<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>語言套件相關聯的使用者屬性。 這會設定<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>屬性上的<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別。

 您的剖析器必須傳回宣告的清單，以回應剖析原因值<xref:Microsoft.VisualStudio.Package.ParseReason>的操作文字自動完成。

## <a name="implementing-complete-word-in-the-parsesource-method"></a>在 ParseSource 方法中實作自動完成文字
 文字自動完成，如<xref:Microsoft.VisualStudio.Package.Source>類別會呼叫<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>方法<xref:Microsoft.VisualStudio.Package.AuthoringScope>類別來取得一份 word 可能相符項目。 您必須從衍生類別中實作清單<xref:Microsoft.VisualStudio.Package.Declarations>類別。 請參閱<xref:Microsoft.VisualStudio.Package.Declarations>如需詳細資訊，您必須實作之方法的類別。

 如果清單包含只有一個字使用，則<xref:Microsoft.VisualStudio.Package.Source>類別會自動插入該文字來取代部分的文字。 如果清單包含多個單字，<xref:Microsoft.VisualStudio.Package.Source>類別顯示工具提示清單，使用者可以從中選取適當的選擇。

 也看範例<xref:Microsoft.VisualStudio.Package.Declarations>中的類別實作[舊版語言服務中的成員自動完成](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)。