---
title: "如何： 使用內建的色彩項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 545d5fa19182678ec1610fa7b689332e272f9962
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-built-in-colorable-items"></a>如何： 使用內建的色彩項目
使用內建的色彩項目之前，您必須先指示整合式的開發環境 (IDE) 未提供您自己自訂色彩項目，在此情況下的方式是<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>物件。 您可以設定語言服務的登錄項目。  
  
### <a name="to-use-built-in-colorable-items"></a>若要使用內建的色彩項目  
  
1.  下 HKEY_LOCAL_MACHINE\VisualStudio\\*X.Y*\Languages\Language 服務\\*語言名稱*，其中*X.Y* 版本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和*語言名稱*是名稱的程式語言，建立 DWORD 登錄項目值呼叫`RequestStockColors`。  
  
2.  設定`RequestStockColors`登錄項目值為 1。  
  
     建立登錄項目，您的色彩標示器的後<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法可以使用的成員<xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS>填滿色彩編輯器所使用的屬性陣列中的列舉。  
  
    > [!NOTE]
    >  如果您要提供自訂色彩項目未設定此登錄項目。 如需詳細資訊，請參閱[自訂色彩項目](../../extensibility/internals/custom-colorable-items.md)。  
  
## <a name="see-also"></a>請參閱  
 [自訂編輯器中著色的語法](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [使用語法色彩編碼舊版語言服務](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [實作語法著色](../../extensibility/internals/implementing-syntax-coloring.md)   
 [自訂色彩項目](../../extensibility/internals/custom-colorable-items.md)   
 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service2.md)