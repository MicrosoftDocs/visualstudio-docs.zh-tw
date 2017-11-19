---
title: "在舊版語言服務 word 完成 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c24765450d0bf8ffdab479bb28c822602892b595
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="word-completion-in-a-legacy-language-service"></a>在舊版語言服務中的文字完成
文字完成填滿遺漏字元在齊部分輸入的字組中。 如果只有一個可能的完成，完成字元輸入時完成這個字。 如果部分文字符合一個以上的可能性，會顯示可能的完成的清單。 完成字元可以是任何字元，不會用於識別項。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新方法是使用 MEF 擴充功能。 若要深入了解，請參閱[擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會提升語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="implementation-steps"></a>實作步驟  
  
1.  當使用者選取**自動完成文字**從**IntelliSense**功能表上，<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>命令傳送至語言服務。  
  
2.  <xref:Microsoft.VisualStudio.Package.ViewFilter>類別就會攔截指令和呼叫<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>方法以剖析原因的<xref:Microsoft.VisualStudio.Package.ParseReason>。  
  
3.  <xref:Microsoft.VisualStudio.Package.Source>類別接著會呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法，以取得可能 word 完成後則將顯示工具提示中的字詞清單使用的清單<xref:Microsoft.VisualStudio.Package.CompletionSet>類別。  
  
     如果只有一個符合的文字，<xref:Microsoft.VisualStudio.Package.Source>類別完成這個字。  
  
 或者，如果掃描器傳回觸發程序值<xref:Microsoft.VisualStudio.Package.TokenTriggers>識別項的第一個字元輸入時，<xref:Microsoft.VisualStudio.Package.Source>會偵測到這個類別，並呼叫<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>方法以剖析原因的<xref:Microsoft.VisualStudio.Package.ParseReason>。 在此情況下剖析器必須偵測存在的成員選取範圍字元，並提供成員的清單。  
  
## <a name="enabling-support-for-the-complete-word"></a>啟用完整單字的支援  
 若要啟用 word 完成集支援`CodeSense`名為參數傳遞至<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>語言套件相關聯的使用者屬性。 這會設定<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>屬性<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別。  
  
 您的剖析器必須傳回宣告的清單，以回應剖析原因值<xref:Microsoft.VisualStudio.Package.ParseReason>，word 完成操作。  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>ParseSource 方法中實作自動完成文字  
 文字完成的<xref:Microsoft.VisualStudio.Package.Source>類別會呼叫<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>方法<xref:Microsoft.VisualStudio.Package.AuthoringScope>類別來取得文字可能相符項目的清單。 您必須從衍生類別中實作清單<xref:Microsoft.VisualStudio.Package.Declarations>類別。 請參閱<xref:Microsoft.VisualStudio.Package.Declarations>如需詳細資訊，您必須實作之方法的類別。  
  
 如果清單包含只有一個字使用，則<xref:Microsoft.VisualStudio.Package.Source>類別會自動插入該單字的部分文字取代。 如果清單包含多個單字，<xref:Microsoft.VisualStudio.Package.Source>類別會顯示使用者可以從中選取適當的選擇工具提示清單。  
  
 另請查看的範例<xref:Microsoft.VisualStudio.Package.Declarations>類別中的實作[舊版語言服務中的成員完成](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)。