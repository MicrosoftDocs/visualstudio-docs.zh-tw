---
title: 使用 Visual studio 的 Office 功能
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
ms.openlocfilehash: c47ed9639a33ecdea3451c63b729d959f6855e5d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62982339"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>使用 Visual studio 的 Office 功能
  當您建立的文件層級專案時，文件和相關聯的應用程式裝載在 Visual Studio 內讓您可以設計，並直接使用文件。 當您有 Visual Studio 中開啟應用程式的 Microsoft Office 時，通常它會如預期般運作。 不過，有些應用程式是功能的不同或無法存取。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>文件保護
 Microsoft Office Word 和 Microsoft Office Excel 提供文件保護功能，您可以使用您的專案中。 不過，如果文件保護已啟用 Visual Studio 中開啟文件時，它可以防止您進行一些設計變更。 如需詳細資訊，請參閱 <<c0> [ 文件的文件層級方案中的保護](../vsto/document-protection-in-document-level-solutions.md)。

## <a name="information-rights-management"></a>資訊版權管理
 Microsoft Office Word 和 Microsoft Office Excel 中使用資訊版權管理 (IRM)。 IRM 可協助您防止未經授權的人員檢視或修改敏感性資訊。 不過，IRM 也可以防止您的程式碼無法執行。 如需詳細資訊，請參閱 <<c0> [ 資訊版權管理和 managed 程式碼延伸模組概觀](../vsto/information-rights-management-and-managed-code-extensions-overview.md)。

## <a name="password-protection"></a>密碼保護
 可以設定 Microsoft Office Word 文件和 Microsoft Office Excel 活頁簿，使它們無法在不知道密碼的其他人開啟。 密碼保護的處理方式在 Word 和 Excel，而且可能影響您的開發程序。 如需詳細資訊，請參閱 < [Office 文件上的密碼保護](../vsto/password-protection-on-office-documents.md)。

## <a name="see-also"></a>另請參閱
- [在文件層級方案中的文件保護](../vsto/document-protection-in-document-level-solutions.md)
- [資訊版權管理和 managed 程式碼延伸模組概觀](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Office 文件上的密碼保護](../vsto/password-protection-on-office-documents.md)
- [如何：不執行程式碼開啟 Office 方案](../vsto/how-to-open-office-solutions-without-running-code.md)
