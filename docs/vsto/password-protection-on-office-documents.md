---
title: Office 檔上的密碼保護
description: 瞭解如何在 Microsoft Word 檔和 Excel 活頁簿上設定密碼，讓未經授權的使用者無法開啟。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b6beaf85000438846e5d440e48c9722b9660f9bd
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528067"
---
# <a name="password-protection-on-office-documents"></a>Office 檔上的密碼保護
  您可以在 Microsoft Office Word 檔上設定密碼，並 Microsoft Office Excel 活頁簿，讓不知道密碼的人可以開啟這些活頁簿。 此選項 **在開啟** 時稱為「密碼」。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 您可以使用已啟用「 **開啟」密碼** 的現有檔和活頁簿來建立檔層級專案。 在 [ **開啟] 開啟** 的 Word 和 Excel 檔中，Visual Studio 的行為不同。

 如需在 **開啟時啟用密碼** 的相關資訊，請參閱 Word 或 Excel 中的說明。

## <a name="behavior-of-excel-and-word"></a>Excel 和 Word 的行為
 每次在 **開啟 [開啟** ] 的 Visual Studio 中開啟 excel 活頁簿時，excel 都會提示您輸入密碼。 當您建立方案時，系統會再次提示您輸入密碼，因為檔會在組建期間開啟。

 當您第一次在已啟用「 **開啟」密碼** 的 Visual Studio 中開啟 word 檔時，Word 會提示您輸入密碼。 成功輸入密碼之後，開啟的 **密碼** 會從檔中移除，而開啟檔將不再需要密碼。 如果您想要讓方案中的檔在可以開啟之前要求密碼，則必須在最終組建之後，以及部署解決方案之前，先啟用 [ **開啟密碼** ]。

## <a name="see-also"></a>另請參閱
- [檔層級方案的檔案保護](../vsto/document-protection-in-document-level-solutions.md)
- [資訊版權管理和 managed 程式碼延伸模組總覽](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [如何：允許程式碼在具有限制許可權的檔背後執行](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
