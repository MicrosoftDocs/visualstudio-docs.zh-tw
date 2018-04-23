---
title: 如何： 使用內建的色彩項目 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6cf51516677aeca71dba269bcdd132e0830b6b4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-built-in-colorable-items"></a>如何： 使用內建的色彩項目
使用內建的色彩項目之前，您必須先指示整合式的開發環境 (IDE) 未提供您自己自訂色彩項目，在此情況下的方式是<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>物件。 您可以設定語言服務的登錄項目。  
  
### <a name="to-use-built-in-colorable-items"></a>若要使用內建的色彩項目  
  
1.  下 HKEY_LOCAL_MACHINE\VisualStudio\\*X.Y*\Languages\Language 服務\\*語言名稱*，其中*X.Y* 版本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和*語言名稱*是名稱的程式語言，建立 DWORD 登錄項目值呼叫`RequestStockColors`。  
  
2.  設定`RequestStockColors`登錄項目值為 1。  
  
     建立登錄項目，您的色彩標示器的後<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法可以使用的成員<xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS>填滿色彩編輯器所使用的屬性陣列中的列舉。  
  
    > [!NOTE]
    >  如果您要提供自訂色彩項目未設定此登錄項目。 如需詳細資訊，請參閱[自訂色彩項目](../../extensibility/internals/custom-colorable-items.md)。  
  
## <a name="see-also"></a>另請參閱  
 [自訂編輯器中著色的語法](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [使用語法色彩編碼舊版語言服務](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [實作語法著色](../../extensibility/internals/implementing-syntax-coloring.md)   
 [自訂色彩項目](../../extensibility/internals/custom-colorable-items.md)   
 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service2.md)