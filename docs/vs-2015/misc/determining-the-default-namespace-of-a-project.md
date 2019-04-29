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
ms.openlocfilehash: 0bc5cba2651f447e36491c641e9b0d05f728e5c7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822574"
---
# <a name="determining-the-default-namespace-of-a-project"></a>判斷專案的預設命名空間
針對[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]的話`CustomToolNamespace`上的輸入檔的值設定屬性`CustomToolNamespace`會變成傳遞至預設命名空間參數的值<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>方法。 否則，請`wszDefaultNamespace`參數傳遞至`Generate`會一律等於根命名空間。 如需有關命名空間的詳細資訊，請參閱 <<c0> [ 命名空間關鍵字](http://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b)。  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 使用資料夾為基礎的命名空間。 也就是命名空間包含根命名空間，再加上包含自訂工具的任何資料夾的名稱。 每個資料夾名稱會轉換成有效的識別項和句號分隔所有的名稱。 例如，如果輸入的檔是 FolderA\FolderB\FolderC\MyInput.txt，而根命名空間是 CL9，然後計算的預設命名空間可**CL9。FolderA.FolderB.FolderC**。  
  
 階層鏈結包含 Web 參考資料夾時，就會發生此規則的例外狀況。 例如，如果：  
  
- FolderC Web 參考資料夾，命名空間為**CL9。FolderC**。  
  
- FolderB Web 參考資料夾，命名空間為**CL9。FolderB.FolderC**。  
  
  也就是命名空間會使用下列格式：  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>另請參閱  
 [實作單一檔案產生器](../extensibility/internals/implementing-single-file-generators.md)   
 [註冊單一檔案產生器](../extensibility/internals/registering-single-file-generators.md)   
 [將類型公開至視覺化設計工具](../extensibility/internals/exposing-types-to-visual-designers.md)