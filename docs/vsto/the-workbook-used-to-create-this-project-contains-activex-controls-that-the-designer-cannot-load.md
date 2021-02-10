---
title: 活頁簿包含無法載入的 ActiveX 控制項
description: 瞭解如何解決活頁簿包含無法載入的 ActiveX 控制項時所發生的錯誤。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: error-reference
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4c8039fc2a5df197446873f0b2efef82d9a5f662
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940783"
---
# <a name="the-workbook-contains-activex-controls-that-cannot-be-loaded"></a>活頁簿包含無法載入的 ActiveX 控制項

  當您以程式設計方式將控制項加入 Word 檔或 Excel 工作表時，會出現「用來建立此專案的活頁簿包含設計工具無法載入的 ActiveX 控制項」錯誤：儲存檔或活頁簿，然後根據檔或活頁簿建立新的檔層級方案。

 描述控制項的 managed 類型資訊不會與文件或活頁簿一起儲存。 當您根據文件或活頁簿建立新的方案時，Visual Studio 沒有足夠的資訊以在主機項目設計工具中載入控制項。

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 開啟文件或活頁簿。

2. 移除在執行階段所加入的控制項。 若要這麼做，您可以在檔或活頁簿中選取它們，然後按下 **Delete** 鍵。

3. 根據文件或活頁簿建立文件層級的方案。

## <a name="see-also"></a>另請參閱
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [在執行時間將控制項新增至 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)
