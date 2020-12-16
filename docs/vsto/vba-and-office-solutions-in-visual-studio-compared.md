---
title: Visual Studio 中的 VBA 和 Office 方案比較
description: 深入瞭解 Microsoft Visual Basic for Applications (VBA) 與 Visual Studio 中 Microsoft Office 解決方案之間的差異。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4d07975061a7b2f5f655bf7f4339671f28fe14c9
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526415"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Visual Studio 中的 VBA 和 Office 方案比較
  Microsoft Visual Basic for Applications (VBA) 會使用與 Office 應用程式緊密整合的 Unmanaged 程式碼。 使用 Visual Studio 建立的 Microsoft Office 專案可讓您充分利用 .NET Framework 和 Visual Studio 設計工具。

 如需您可以使用 Visual Studio 建立之 Office 方案類型的詳細資訊，請參閱 [office 方案開發總覽 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。

## <a name="comparison"></a>比較
 下表提供 VBA 方案和 Visual Studio 中的 Office 方案之間的基本比較。

|VBA 方案|Visual Studio 中的 Office 方案|
|-------------------|---------------------------------------|
|使用已連接到特定文件並一起保存的程式碼。|使用與檔層級自訂分開儲存 (中的程式碼) ，或使用應用程式 (for VSTO 增益集) 所載入的元件。|
|使用 Office 物件模型和 VBA API。|可讓您存取 Office 物件模型和 [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] API。|
|針對巨集錄製和簡化開發人員經驗而設計。|針對安全性、簡化的程式碼維護，以及使用完整 Visual Studio 整合式開發環境 (IDE) 的能力而設計。|
|適用于透過與 Office 應用程式緊密整合而受益的解決方案。|相當適用於從 Visual Studio 完整資源和 [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]獲益的方案。|
|對於企業而言有限制，尤其是在安全性和部署方面。|針對在企業中使用而設計。|

 有些事仍然使用 VBA 較容易快速地達成。 具體而言，您可能想要繼續使用 VBA 的原因有：

- 自訂工作表函式。

- 巨集錄製。

## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>結合使用 Visual Studio 所建立的 VBA 方案和 Office 方案
 您可以從使用 Visual Studio 建立的 Office 方案中呼叫 VBA 程式碼，也可以從 VBA 在使用 Visual Studio 建立的 Office 方案中呼叫程式碼。 特定技術會依 Office 方案是 VSTO 增益集或文件層級自訂而有所不同。 如需詳細資訊，請參閱 [從其他 Office 方案呼叫 VSTO 增益集](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) 的程式碼，並 [結合 VBA 和檔層級自訂](../vsto/combining-vba-and-document-level-customizations.md)。

## <a name="see-also"></a>另請參閱
- [Office 方案開發總覽 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [從其他 Office 方案呼叫 VSTO 增益集的程式碼](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [合併 VBA 和檔層級自訂](../vsto/combining-vba-and-document-level-customizations.md)
- [檔層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)
- [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)
- [保護 Office 方案](../vsto/securing-office-solutions.md)
- [在 Visual Studio&#41;中開始 &#40;Office 開發 ](../vsto/getting-started-office-development-in-visual-studio.md)
