---
title: 舊版語言服務中的文字自動完成 |Microsoft Docs
description: 在 Visual Studio SDK 中，舊版語言服務可以支援 Word 自動完成。 瞭解如何在 VSPackage 中實行舊版語言服務。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b3625719987afc94deda314fa61d7a8cc2c1c843
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943364"
---
# <a name="word-completion-in-a-legacy-language-service"></a>舊版語言服務中的文字自動完成
單字完成會在部分類型的單字上填滿遺漏的字元。 如果只有一個可能的完成，則會在輸入完成字元時完成此字。 如果部分單字元合一個以上的可能性，則會顯示可能的完成清單。 完成字元可以是不會用於識別碼的任何字元。

 舊版語言服務會實作為 VSPackage 的一部分，但是執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解，請參閱 [擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。

> [!NOTE]
> 建議您儘快開始使用新的編輯器 API。 這可改善您的語言服務效能，並讓您利用新的編輯器功能。

## <a name="implementation-steps"></a>執行步驟

1. 當使用者從 [ **IntelliSense** ] 功能表中選取 [**完成文字**] 時， <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 會將命令傳送至語言服務。

2. <xref:Microsoft.VisualStudio.Package.ViewFilter>類別會捕捉命令，並 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 使用的剖析原因來呼叫方法 <xref:Microsoft.VisualStudio.Package.ParseReason> 。

3. <xref:Microsoft.VisualStudio.Package.Source>然後，類別會呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法以取得可能的字組完成的清單，然後使用類別，在工具提示清單中顯示文字 <xref:Microsoft.VisualStudio.Package.CompletionSet> 。

    如果只有一個相符的字組，則 <xref:Microsoft.VisualStudio.Package.Source> 類別會完成此字。

   或者，如果在 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 輸入識別碼的第一個字元時，掃描器傳回觸發程式值，類別會 <xref:Microsoft.VisualStudio.Package.Source> 偵測到此情況，並 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 使用的剖析原因來呼叫方法 <xref:Microsoft.VisualStudio.Package.ParseReason> 。 在此情況下，剖析器必須偵測成員選取字元是否存在，並提供成員清單。

## <a name="enabling-support-for-the-complete-word"></a>啟用完整字組的支援
 若要啟用字組自動完成的支援，請將 `CodeSense` 傳遞給 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 與語言套件相關聯之使用者屬性的具名引數設定為。 這會設定 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 類別上的屬性 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 。

 您的剖析器必須傳回宣告清單，以回應剖析原因值 <xref:Microsoft.VisualStudio.Package.ParseReason> ，讓 word 自動完成運作。

## <a name="implementing-complete-word-in-the-parsesource-method"></a>在 ParseSource 方法中執行完整的單字
 若為 word 自動完成， <xref:Microsoft.VisualStudio.Package.Source> 類別會 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> 在類別上呼叫方法 <xref:Microsoft.VisualStudio.Package.AuthoringScope> ，以取得可能的字組相符專案清單。 您必須在衍生自類別的類別中執行清單 <xref:Microsoft.VisualStudio.Package.Declarations> 。 <xref:Microsoft.VisualStudio.Package.Declarations>如需您必須執行之方法的詳細資訊，請參閱類別。

 如果清單中只包含一個單字，則 <xref:Microsoft.VisualStudio.Package.Source> 類別會自動插入該單字來取代部分字。 如果清單包含一個以上的單字，則 <xref:Microsoft.VisualStudio.Package.Source> 類別會顯示一個工具提示清單，使用者可以從中選取適當的選擇。

 另請參閱在 <xref:Microsoft.VisualStudio.Package.Declarations> [舊版語言服務中成員完成](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)的類別執行範例。
