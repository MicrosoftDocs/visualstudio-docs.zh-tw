---
title: 如何：以 Office 多語系使用者介面為目標
description: 瞭解如何使用 Visual Studio 以程式設計方式將目標設為 Microsoft Office 多語系使用者介面。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 245b257140cd0b1f54719ec7a132bf2297fc2dd3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962336"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>如何：以 Office 多語系使用者介面為目標
  多語系消費者介面 (MUI) 是 Microsoft Office 功能，可讓終端使用者變更使用者介面 (UI) 的語言。 例如，使用英文 UI 的終端使用者可以將 UI 的語言變更為西班牙文。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 如果您的應用程式將由使用許多語言 Office 的人員使用，您可以新增程式碼，以自動變更 UI 字串的語言，使其符合使用者電腦上的 Office 所使用的語言 (如果使用者已安裝正確的資源) 。

## <a name="to-check-the-current-office-ui-setting"></a>若要檢查目前的 Office UI 設定

1. 使用 <xref:System.Threading.Thread.CurrentUICulture%2A> 目前線程的屬性。 將 UI 字串的語言設定為符合目前在使用者電腦上執行的 Office 版本所使用的語言。

     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]

## <a name="see-also"></a>另請參閱
- [如何：透過主要 interop 元件以 Office 應用程式為目標](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Office 方案中的晚期繫結](../vsto/late-binding-in-office-solutions.md)
