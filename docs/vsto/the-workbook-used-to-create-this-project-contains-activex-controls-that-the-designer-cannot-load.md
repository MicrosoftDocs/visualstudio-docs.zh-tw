---
title: 用來建立此專案的活頁簿包含設計工具無法載入的 ActiveX 控制項
ms.date: 02/02/2017
ms.topic: error-reference
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4485489b48c4d1b03b608c6072cfc859e8bc8f59
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537341"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>用來建立此專案的活頁簿包含設計工具無法載入的 ActiveX 控制項
  當您以程式設計的方式將控制項加入至 Word 文件或 Excel 工作表、儲存文件或活頁簿，然後根據文件或活頁簿建立新的文件層級方案，則會出現這個錯誤。

 描述控制項的 managed 類型資訊不會與文件或活頁簿一起儲存。 當您根據文件或活頁簿建立新的方案時，Visual Studio 沒有足夠的資訊以在主機項目設計工具中載入控制項。

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 開啟文件或活頁簿。

2. 移除在執行階段所加入的控制項。 若要這麼做，您可以在檔或活頁簿中選取它們，然後按下**Delete**鍵。

3. 根據文件或活頁簿建立文件層級的方案。

## <a name="see-also"></a>另請參閱
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)
