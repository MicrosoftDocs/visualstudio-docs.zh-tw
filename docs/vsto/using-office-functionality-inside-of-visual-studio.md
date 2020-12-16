---
title: 使用 Visual Studio 內的 Office 功能
description: 瞭解檔層級專案中的檔和相關聯的應用程式如何裝載于 Visual Studio 內，讓您可以直接使用檔。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c93994b233990e2362c62445909adb66a0eeeb9b
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528408"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>使用 Visual Studio 內的 Office 功能
  當您建立檔層級專案時，檔和相關聯的應用程式會裝載于 Visual Studio 內，因此您可以直接設計和使用檔。 當您在 Visual Studio 中開啟 Microsoft Office 應用程式時，它通常會如預期般運作。 不過，有些應用程式的功能是不同的或無法存取。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>檔案保護
 Microsoft Office Word 和 Microsoft Office Excel 提供您可以在專案中使用的檔案保護功能。 但是，如果在 Visual Studio 中開啟檔時啟用檔案保護，可能會讓您無法進行某些設計變更。 如需詳細資訊，請參閱檔 [層級方案中的檔案保護](../vsto/document-protection-in-document-level-solutions.md)。

## <a name="information-rights-management"></a>資訊版權管理
  (IRM) 的資訊 Rights Management 可在 Microsoft Office Word 和 Microsoft Office Excel 中取得。 IRM 可協助防止未經授權的人員查看或改變機密資訊。 不過，IRM 也會防止您的程式碼執行。 如需詳細資訊，請參閱 [資訊版權管理和 managed 程式碼延伸模組總覽](../vsto/information-rights-management-and-managed-code-extensions-overview.md)。

## <a name="password-protection"></a>密碼保護
 您可以設定 Microsoft Office Word 檔和 Microsoft Office Excel 活頁簿，讓不知道密碼的人可以開啟這些活頁簿。 密碼保護在 Word 和 Excel 中的處理方式不同，而且可能會影響您的開發流程。 如需詳細資訊，請參閱 [Office 檔的密碼保護](../vsto/password-protection-on-office-documents.md)。

## <a name="see-also"></a>另請參閱
- [檔層級方案的檔案保護](../vsto/document-protection-in-document-level-solutions.md)
- [資訊版權管理和 managed 程式碼延伸模組總覽](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Office 檔上的密碼保護](../vsto/password-protection-on-office-documents.md)
- [如何：開啟 Office 方案而不執行程式碼](../vsto/how-to-open-office-solutions-without-running-code.md)
