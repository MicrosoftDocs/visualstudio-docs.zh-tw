---
title: 如何： 使用內建可設定色彩的項目 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9cd6cc62e54fa35a8b146c93e2931b2cf35145b5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209766"
---
# <a name="how-to-use-built-in-colorable-items"></a>如何： 使用內建可設定色彩的項目
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用內建可設定色彩的項目之前，您必須先通知整合式的開發環境 (IDE)，您不會提供您自己自訂色彩項目，在此情況下會<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>物件。 您可以設定語言服務的登錄項目。  
  
### <a name="to-use-built-in-colorable-items"></a>若要使用內建可設定色彩的項目  
  
1.  下 HKEY_LOCAL_MACHINE\VisualStudio\\*X.Y*\Languages\Language Services\\*語言名稱*，其中*X.Y* 版本[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]並*語言名稱*是名稱的語言，建立 DWORD 登錄項目值呼叫`RequestStockColors`。  
  
2.  設定`RequestStockColors`登錄項目值設為 1。  
  
     您建立的登錄項目，您的色彩標示器的後<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法可以使用的成員<xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS>來填滿色彩編輯器所使用的屬性陣列中的列舉。  
  
    > [!NOTE]
    >  如果您要提供自訂色彩的項目，請不要設定此登錄項目。 如需詳細資訊，請參閱 <<c0> [ 自訂色彩項目](../../extensibility/internals/custom-colorable-items.md)。  
  
## <a name="see-also"></a>另請參閱  
 [自訂編輯器中的語法著色](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [舊版語言服務中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [實作語法著色](../../extensibility/internals/implementing-syntax-coloring.md)   
 [自訂色彩的項目](../../extensibility/internals/custom-colorable-items.md)   
 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service2.md)

