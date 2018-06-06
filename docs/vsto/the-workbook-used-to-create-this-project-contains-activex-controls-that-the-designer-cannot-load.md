---
title: 用來建立此專案的活頁簿包含設計工具無法載入的 ActiveX 控制項
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9d47ee32f23ca0eb856b2a8f618d60fae552a027
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693067"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>用來建立此專案的活頁簿包含設計工具無法載入的 ActiveX 控制項
  當您以程式設計的方式將控制項加入至 Word 文件或 Excel 工作表、儲存文件或活頁簿，然後根據文件或活頁簿建立新的文件層級方案，則會出現這個錯誤。  
  
 描述控制項的 managed 類型資訊不會與文件或活頁簿一起儲存。 當您根據文件或活頁簿建立新的方案時，Visual Studio 沒有足夠的資訊以在主機項目設計工具中載入控制項。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  開啟文件或活頁簿。  
  
2.  移除在執行階段所加入的控制項。 您可以這樣做，請選取圖形中的文件或活頁簿和按**刪除**索引鍵。  
  
3.  根據文件或活頁簿建立文件層級的方案。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  