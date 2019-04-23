---
title: 用來建立此專案的活頁簿包含設計工具無法載入的 ActiveX 控制項
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 0087841e7f37d49da40817e1487b8529af1f87df
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089350"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>用來建立此專案的活頁簿包含設計工具無法載入的 ActiveX 控制項
  當您以程式設計的方式將控制項加入至 Word 文件或 Excel 工作表、儲存文件或活頁簿，然後根據文件或活頁簿建立新的文件層級方案，則會出現這個錯誤。

 描述控制項的 managed 類型資訊不會與文件或活頁簿一起儲存。 當您根據文件或活頁簿建立新的方案時，Visual Studio 沒有足夠的資訊以在主機項目設計工具中載入控制項。

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 開啟文件或活頁簿。

2. 移除在執行階段所加入的控制項。 您可以執行這項操作，請選取圖形中的文件或活頁簿和按下**刪除**索引鍵。

3. 根據文件或活頁簿建立文件層級的方案。

## <a name="see-also"></a>另請參閱
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)
