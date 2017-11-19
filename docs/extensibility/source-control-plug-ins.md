---
title: "原始檔控制外掛程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea5169b3d74a77bbb079dab5b310a3b7ebbbeff0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-plug-ins"></a>原始檔控制外掛程式
原始檔控制外掛程式 SDK 參考章節包含完整的介面規格，可讓原始檔控制系統整合與[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 它會指定的語法和語意的原始檔控制外掛程式必須實作介面以各種函式和資料類型[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)。  
  
## <a name="in-this-section"></a>本章節內容  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)  
 列出原始檔控制外掛程式必須遵守原始檔控制外掛程式 API 實作的函式。  
  
 [IDE 所實作的回呼函式](../extensibility/callback-functions-implemented-by-the-ide.md)  
 描述函式的原始檔控制外掛程式用來執行特定命令時，將資訊傳遞至 IDE。  
  
 [列舉程式](../extensibility/enumerators.md)  
 列出原始檔控制外掛程式必須知道原始檔控制外掛程式 API 中的列舉值的資料類型。  
  
 [功能旗標](../extensibility/capability-flags.md)  
 描述`SCC_CAP_xxx`旗標，會指示提供者的功能。  
  
 [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)  
 列出可用於特定命令的內容的旗標。  
  
 [錯誤碼](../extensibility/error-codes.md)  
 列出常見的錯誤值做為函式傳回`SCCTRN`。  
  
 [用來做為索引鍵以尋找原始檔控制外掛程式的字串](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 描述索引鍵來存取登錄，以尋找原始檔控制外掛程式。  
  
 [MSSCCPRJ.SCC 檔案](../extensibility/mssccprj-scc-file.md)  
 描述用戶端檔案會包含在 IDE 中的不透明的資訊，但正由原始檔控制外掛程式在版本控制中找出方案或專案。  
  
 [實作原始檔控制外掛程式的最佳作法](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 提供重要技術的備忘提醒記住當您實作原始檔控制外掛程式 API 的集合。  
  
 [字串長度限制](../extensibility/restrictions-on-string-lengths.md)  
 描述的不同函式中使用的字串長度在原始檔控制外掛程式 API 中的限制。  
  
 [名詞解釋](../extensibility/source-control-plug-in-glossary.md)  
 提供有用的詞彙和其定義讀取原始檔控制外掛程式 SDK 文件。  
  
 [如何︰關閉原始檔控制外掛程式的相容性警告](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 描述如何停用警告。  
  
## <a name="related-sections"></a>相關章節  
 [原始檔控制外掛程式範例](http://msdn.microsoft.com/en-us/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 提供的原始檔控制外掛程式功能的範例。  
  
 [原始檔控制外掛程式測試指南](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 描述原始檔控制外掛程式相關的測試程序。  
  
 [建立原始檔控制外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)  
 討論如何建立原始檔控制外掛程式，提供原始檔控制功能，當您使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]原始檔控制使用者介面 (UI)。  
  
 [Visual Studio SDK 參考](../extensibility/visual-studio-sdk-reference.md)  
 顯示清單的參考主題。