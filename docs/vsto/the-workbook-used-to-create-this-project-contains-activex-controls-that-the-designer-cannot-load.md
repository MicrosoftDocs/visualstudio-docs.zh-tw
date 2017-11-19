---
title: "用來建立此專案的活頁簿包含設計工具無法載入的 ActiveX 控制項 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
ms.assetid: 91e9c6ee-7543-41e3-be0c-6c000cfd32d1
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74f68bdea80705d1b774d9f24a5ba3b122b6f653
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>用來建立此專案的活頁簿包含設計工具無法載入的 ActiveX 控制項
  當您以程式設計的方式將控制項加入至 Word 文件或 Excel 工作表、儲存文件或活頁簿，然後根據文件或活頁簿建立新的文件層級方案，則會出現這個錯誤。  
  
 描述控制項的 managed 類型資訊不會與文件或活頁簿一起儲存。 當您根據文件或活頁簿建立新的方案時，Visual Studio 沒有足夠的資訊以在主機項目設計工具中載入控制項。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  開啟文件或活頁簿。  
  
2.  移除在執行階段所加入的控制項。 在文件或活頁簿中選取它們，然後按 DELETE 鍵，即可執行這項操作。  
  
3.  根據文件或活頁簿建立文件層級的方案。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  