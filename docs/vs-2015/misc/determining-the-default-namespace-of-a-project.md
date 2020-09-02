---
title: 判斷專案的預設命名空間 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d58c8986922c30192d6300a623a635b24c34ed5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705778"
---
# <a name="determining-the-default-namespace-of-a-project"></a>判斷專案的預設命名空間
針對 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ，如果在 `CustomToolNamespace` 輸入檔上設定屬性，則的值 `CustomToolNamespace` 會變成傳遞給方法之預設命名空間參數的值 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> 。 否則， `wszDefaultNamespace` 傳遞給的參數 `Generate` 一律等於根命名空間。 如需命名空間的詳細資訊，請參閱 [命名空間關鍵字](https://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b)。  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 使用以資料夾為基礎的命名空間。 也就是說，命名空間是由根命名空間，加上任何包含自訂工具的資料夾名稱所組成。 每個資料夾名稱都會轉換成有效的識別碼，並以句點分隔所有名稱。 例如，如果輸入檔 FolderA\FolderB\FolderC\MyInput.txt，且根命名空間是 CL9，則計算的預設命名空間會是 **CL9。FolderA. FolderB. FolderC**。  
  
 當階層鏈包含 Web 參考資料夾時，就會發生此規則的例外狀況。 例如：  
  
- FolderC 是 Web 參考資料夾，命名空間會是 **CL9。FolderC**。  
  
- FolderB 是 Web 參考資料夾，命名空間會是 **CL9。FolderB. FolderC**。  
  
  也就是說，命名空間會使用下列格式：  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行單一檔案產生器](../extensibility/internals/implementing-single-file-generators.md)   
 [註冊單一檔案產生器](../extensibility/internals/registering-single-file-generators.md)   
 [將類型公開至視覺化設計工具](../extensibility/internals/exposing-types-to-visual-designers.md)